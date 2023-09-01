** Organizing lineup by batting average **
#include <iostream>
#include <string>
using namespace std;

//Enumerations
enum innings {FIRSTINNING, SECONDINNING, THIRDINNING, FOURTHINNING, FIFTHINNING};
enum positions {FIRSTBASE, SECONDBASE, SHORTSTOP, THIRDBASE, CATCHER, PITCHER, 
				LEFTFIELD, LEFTCENTERFIELD, RIGHTCENTERFIELD, CENTERFIELD, RIGHTFIELD};

//Constant integers
const int NUMOFPLAYERS = 12;
const int NUMOFINNINGS = 5;
const int NUMOFPOSITIONS = 12;
const int ROWS = 12;
const int COLUMNS = 5;

//Void functions
void getPlayerNames(string NAMESOFPLAYERS[NUMOFPLAYERS]);
void getBattingAverage(int battingAverage[NUMOFPLAYERS]);
void displayArray(string playerPositionArray[ROWS][COLUMNS]);
void battingAverageHighToLow(int battingaverage[NUMOFPLAYERS], string NAMESOFPLAYERS[NUMOFPLAYERS]);
void columnHeaders();

//Arrays
string NAMESOFPLAYERS[NUMOFPLAYERS];
string positions;
int battingAverage[NUMOFPLAYERS];

int main() 
{
	string playerPositionArray[ROWS][COLUMNS] =
	{
	{"RF","2B", "RCF", "OUT2", "P"},
	{"RCF", "3B", "LCF", "1B", "OUT1"},
	{"2B", "RF", "OUT1", "C", "LF"},
	{"1B", "RCF", "P", "OUT1", "SS"},
	{"P", "OUT2", "1B", "LCF", "RF"},
	{"LCF", "1B", "OUT2", "2B", "RCF"},
	{"LF", "SS", "RF", "3B", "C"},
	{"C", "LCF", "SS", "RF", "2B"},
	{"SS", "LF", "3B", "P", "OUT2"},
	{"OUT1", "C", "LF", "RCF", "3B"},
	{"3B", "OUT1", "2B", "LF", "1B"},
	{"OUT2", "P", "C", "SS", "LCF"}
	};

	//Player name input
	cout << "Enter 12 player names: " << endl;
	getPlayerNames(NAMESOFPLAYERS);
	cout << endl;

	//Player input batting average
	cout << "Enter the averages for each player: " << endl;
	getBattingAverage(battingAverage);
	cout << endl;

	//Arrange batting order and positions
	cout << "Game lineup and field positions: " << endl;
	
	//Arrange batting average from high to low
	battingAverageHighToLow(battingAverage, NAMESOFPLAYERS);

	//Column headers
	columnHeaders();
	cout << endl;

	//Displays player positions in the array
	displayArray(playerPositionArray);

	return 0;
}

//Void function for player names
void getPlayerNames(string NAMESOFPLAYERS[NUMOFPLAYERS])
{
	for (int counter = 0; counter < NUMOFPLAYERS; counter += 1)
	{
		cout << "What is player " << counter + 1 << "'s name: ";
		cin >> NAMESOFPLAYERS[counter];
	}
}

//Void function for batting average
void getBattingAverage(int battingAverage[NUMOFPLAYERS])
{
	for (int counter = 0; counter < NUMOFPLAYERS; counter += 1)
	{
		cout << "What is " << NAMESOFPLAYERS[counter] << "'s average: ";
		cin >> battingAverage[counter];
	}
}

//Void function for displaying array of rows and columns
void displayArray(string playerPositionArray[ROWS][COLUMNS])
{
	for (int i = 0; i < ROWS; i++)
	{
		cout << NAMESOFPLAYERS[i];
		for (int k = 0; k < 10 - NAMESOFPLAYERS[i].length(); k++) {
			cout << " ";
		}
		for (int j = 0; j < COLUMNS; j++) {
			cout << playerPositionArray[i][j] << " ";
		}
		cout << endl;
	}
}

//Void function for arranging batting average from high to low
void battingAverageHighToLow(int battingAverage[NUMOFPLAYERS], string NAMESOFPLAYERS[NUMOFPLAYERS])
{
	int indexOfLargest;
	string temp;

	for (int i = 0; i < NUMOFPLAYERS; i++)
	{
		for (int j = i + 1; j <= NUMOFPLAYERS; j++)
		{
			if (battingAverage[i] < battingAverage[j]) {
				indexOfLargest = battingAverage[i];
				temp = NAMESOFPLAYERS[i];
				battingAverage[i] = battingAverage[j];
				NAMESOFPLAYERS[i] = NAMESOFPLAYERS[j];
				battingAverage[j] = indexOfLargest;
				NAMESOFPLAYERS[j] = temp;
			}
		}
	}
}

void columnHeaders()
{
	const int COLUMNS = 6;
	string column[COLUMNS] = { "Name", "Inning 1", "Inning 2", "Inning 3", "Inning 4", "Inning 5" };
	string columnArrayIndex;

	for (int i = 0; i < COLUMNS; i += 1)
	{
		columnArrayIndex = column[i];
		cout << column[i];
		for (int i = 0; i < COLUMNS; i += 1)
		{
			cout << " ";
		}
	}
}
