#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>

void extractLogs(const std::string &inputFilePath, const std::string &date) {
    std::ifstream inputFile(inputFilePath);
    if (!inputFile.is_open()) {
        std::cerr << "Error: Could not open input file." << std::endl;
        exit(EXIT_FAILURE);
    }

#ifdef _WIN32
    system("if not exist output mkdir output");
#else
    system("mkdir -p output");
#endif

    std::string outputFilePath = "output/output_" + date + ".txt";
    std::ofstream outputFile(outputFilePath);
    if (!outputFile.is_open()) {
        std::cerr << "Error: Could not create output file." << std::endl;
        exit(EXIT_FAILURE);
    }

    std::string line;
    size_t dateLength = date.length();
    while (std::getline(inputFile, line)) {
        if (line.compare(0, dateLength, date) == 0) {
            outputFile << line << '\n';
        }
    }

    inputFile.close();
    outputFile.close();
    std::cout << "Logs for " << date << " extracted to " << outputFilePath << std::endl;
}

int main(int argc, char *argv[]) {
    if (argc != 3) {
        std::cerr << "Usage: " << argv[0] << " <log_file_path> <YYYY-MM-DD>" << std::endl;
        return EXIT_FAILURE;
    }

    std::string logFilePath = argv[1];
    std::string date = argv[2];

    if (date.size() != 10 || date[4] != '-' || date[7] != '-') {
        std::cerr << "Error: Date format must be YYYY-MM-DD." << std::endl;
        return EXIT_FAILURE;
    }

    extractLogs(logFilePath, date);
    return EXIT_SUCCESS;
}