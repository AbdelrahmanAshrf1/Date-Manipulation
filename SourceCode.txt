#pragma warning(disable : 4996)
#include <iostream>
#include <string>
#include <iomanip>
#include <cctype>

using namespace std;

enum enOperationName
{
	eIsLeapYear = 1,
	eNumberOfDaysInMonth,
	eNumberOfHoursInAmonth,
	eNumberOfMinutesInAmonth,
	eNumberOfSecondsInAmonth,
	eDayOfWeekOrder,
	ePrintMonthCalender,
	ePrintCalenderYear,
	eTotalDaysFromTheBeginningOfYrar,
	eGetDateFromDayOrderInYear,
	eDateAddDays,
	eGetSystemDate,
	eIsDate1BeforeDate2,
	eIsDate1EqualDate2,
	eIsDate1AfterDate2,
	eIsLastDayInMonth,
	eIsLasMonthInYear,
	eIsDateInPeriod,
	eIsValidDate,
	eIsOverlapPeriods,
	eGetDifferenceInDays,
	eIncreaseDateByOneDay,
	eIncreaseDateByXDays,
	eIncreaseDateByOneWeek,
	eIncreaseDateByXWeeks,
	eIncreaseDateByOneMonth,
	eIncreaseDateByXMonth,
	eIncreaseDateByOneYear,
	eIncreaseDateByXYear,
	eIncreaseDateByOneDecade,
	eIncreaseDateByOneCentury,
	eIncreaseDateByOneMillennium,
	eDecrementDateByOneDay,
	eDecreaseDateByXDays,
	eDecreaseDateByOneWeek,
	eDecreaseDateByXWeeks,
	eDecreaseDateByOneMonth,
	eDecreaseDateByXMonths,
	eDecreaseDateByOneYear,
	eDecreaseDateByXYears,
	eDecreaseDateByOneDecade,
	eDecreaseDateByOneCentury,
	eDecreaseDateByOneMillennium,
	eDaysUntilEndOfMonth,
	eDaysUntilEndOfYear,
	eIsEndOfWeek,
	eIsWeekEnd,
	eIsBusineesDay,
	eDaysUntilEndOfWeek,
	eCalculatePeriodLengthInDays,
	eCountOverlapDays
};

struct stOperationInfo
{
	enOperationName OperationName;
	string result;
};

struct stDate
{
	short Year;
	short Month;
	short Day;
};

struct stPeriod
{
	stDate StartDate;
	stDate EndDate;
};

short ReadYear()
{
	short Year = 0;

	cout << "Please enter a Year to check .. ?";
	cin >> Year;

	return Year;
}

short ReadMonth()
{
	short Month = 0;

	cout << "Please enter a Month to check .. ?";
	cin >> Month;

	return Month;
}

short ReadDay()
{
	short Day = 0;

	cout << "Please enter a Day .. ?";
	cin >> Day;

	return Day;
}

stDate ReadFullDate()
{
	stDate Date;

	Date.Day = ReadDay();

	Date.Month = ReadMonth();

	Date.Year = ReadYear();

	return Date;
}

stPeriod ReadPeriod()
{
	stPeriod Period;

	cout << "Enter Start date :\n\n";
	Period.StartDate = ReadFullDate();
	cout << "\nEnter End date :\n";
	Period.EndDate = ReadFullDate();

	return Period;
}

string ReadStringDate(string Mesage)
{
	string DateString = "";

	cout << Mesage;
	getline(cin >> ws, DateString);

	return DateString;
}

void ShowMainMenuOptions()
{
	system("cls");
	cout << "========================================================================================\n";
	cout << "\t\t\tChoose one choice to perform\n";
	cout << "========================================================================================\n";
	cout << setw(45) << left << " [01] Is Leap Year." << "|" << "\t[31] Increase Date By One Century.\n";
	cout << setw(45) << left << " [02] Number Of Days In Month ." << "|" << "\t[32] Increase Date By One Millennium.\n";
	cout << setw(45) << left << " [03] Number Of Hours In a month ." << "|" << "\t[33] Decrease Date By One Day.\n";
	cout << setw(45) << left << " [04] Number Of Minutes In a month." << "|" << "\t[34] Decrease Date By X Days.\n";
	cout << setw(45) << left << " [05] Number Of Seconds In a month." << "|" << "\t[35] Decrease Date By One Week.\n";
	cout << setw(45) << left << " [06] Day Of Week Order." << "|" << "\t[36] Decrease Date By X Weeks.\n";
	cout << setw(45) << left << " [07] Print Month Calender ." << "|" << "\t[37] Decrease Date By One Month.\n";
	cout << setw(45) << left << " [08] Print Calender Year." << "|" << "\t[38] Decrease Date By X Months.\n";
	cout << setw(45) << left << " [09] Total Days From The Beginning Of Yrar." << "|" << "\t[39] Decrease Date By One Year.\n";
	cout << setw(45) << left << " [10] Get Date From Day Order In Year." << "|" << "\t[40] Decrease Date By X Years.\n";
	cout << setw(45) << left << " [11] Date Add Days." << "|" << "\t[41] Decrease Date By One Decade.\n";
	cout << setw(45) << left << " [12] Get System Date." << "|" << "\t[42] Decrease Date By One Century.\n";
	cout << setw(45) << left << " [13] Is Date1 Before Date2." << "|" << "\t[43] Decrease Date By One Millennium.\n";
	cout << setw(45) << left << " [14] Is Date1 Equal Date2." << "|" << "\t[44] Days Until End Of Month.\n";
	cout << setw(45) << left << " [15] Is Date1 After Date2." << "|" << "\t[45] Days Until End Of Year.\n";
	cout << setw(45) << left << " [16] Is Last Day In Month." << "|" << "\t[46] Is End Of Week.\n";
	cout << setw(45) << left << " [17] Is Last Month In Year." << "|" << "\t[47] Is Week End.\n";
	cout << setw(45) << left << " [18] Is Date In Period." << "|" << "\t[48] Is Businees Day.\n";
	cout << setw(45) << left << " [19] Is Valid Date." << "|" << "\t[49] Days Until End Of Week.\n";
	cout << setw(45) << left << " [20] Is Overlap Periods." << "|" << "\t[50] Calculate Period Length In Days.\n";
	cout << setw(45) << left << " [21] Get Difference In Days." << "|" << "\t[51] Count Overlap Days.\n";
	cout << setw(45) << left << " [22] Increase Date By One Day." << "|\n";
	cout << setw(45) << left << " [23] Increase Date By X Days." << "|\n";
	cout << setw(45) << left << " [24] Increase Date By One Week." << "|\n";
	cout << setw(45) << left << " [25] Increase Date By X Weeks." << "|\n";
	cout << setw(45) << left << " [26] Increase Date By One Month." << "|\n";
	cout << setw(45) << left << " [27] Increase Date By X Months." << "|\n";
	cout << setw(45) << left << " [28] Increase Date By One Year." << "|\n";
	cout << setw(45) << left << " [29] Increase Date By X Years." << "|\n";
	cout << setw(45) << left << " [30] Increase Date By One Decade." << "|\n";
	cout << "========================================================================================\n";
}

enOperationName GetUserChoice()
{
	short Choice = 0;
	cin >> Choice;

	while (cin.fail() || Choice < 1 || Choice > 51)
	{
		cin.clear();
		cin.ignore(numeric_limits<streamsize>::max(), '\n');

		cout << "\nInvalid input ,Please enter a vaild one [1 : 51] ! ";
		cin >> Choice;
	}
	return (enOperationName)Choice;
}

// Define Core Functions.
// (1) Define Is Leap Year Functions.
bool IsLeapYear(short Year)
{
	return (Year % 4 == 0 && Year % 100 != 0) || (Year % 400 == 0);
}

string IsLeapYearScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tIs Leap Year Screen.\n";
	cout << "====================================\n";

	short Year = ReadYear();
	bool Answer = IsLeapYear(Year);

	return (Answer == 1) ? "True" : "False";
}

// (2) Define Number Of Days In Month Functions.
short NumberOfDaysInMonth(short Year, short Month)
{
	if (Month < 1 || Month > 12)
		return 0;

	short DaysInMonths[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };
	return Month == 2 ? IsLeapYear(Year) ? 29 : 28 : DaysInMonths[Month - 1];
}

string NumberOfDaysInMonthScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "  Number Of Days In Month Screen.\n";
	cout << "====================================\n";

	short Month = ReadMonth();
	short Year = ReadYear();
	short Answer = NumberOfDaysInMonth(Year, Month);

	return to_string(Answer);
}

// (3) Define Number Of Hours In a month Functions.
short NumberOfHoursInAmonth(short Year, short Month)
{
	return NumberOfDaysInMonth(Year, Month) * 24;
}

string NumberOfHoursInAmonthScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tNumber Of Hours In a month.\n";
	cout << "====================================\n";

	short Month = ReadMonth();
	short Year = ReadYear();
	short Answer = NumberOfHoursInAmonth(Year, Month);

	return to_string(Answer) + " - Hours";
}

// (4) Define Number Of Hours In a month Functions.
int NumberOfMinutesInAmonth(short Year, short Month)
{
	return NumberOfHoursInAmonth(Year, Month) * 60;
}

string NumberOfMinutesInAmonthScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tNumber Of Minutes In a month.\n";
	cout << "====================================\n";

	short Month = ReadMonth();
	short Year = ReadYear();
	short Answer = NumberOfMinutesInAmonth(Year, Month);

	return to_string(Answer) + " - Minutes";
}

// (5) Define Number Of Seconds In a month Functions.
int NumberOfSecondsInAmonth(short Year, short Month)
{
	return NumberOfMinutesInAmonth(Year, Month) * 60;
}

string NumberOfSecondsInAmonthScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tNumber Of Seconds In a month.\n";
	cout << "====================================\n";

	short Month = ReadMonth();
	short Year = ReadYear();
	short Answer = NumberOfSecondsInAmonth(Year, Month);

	return to_string(Answer) + " - Seconds";
}

// (6) Define Number Of Seconds In a month Functions.
short DayOfWeekOrder(stDate Date)
{
	short a, y, m, d;

	// Gregorian:
	// 0:sun, 1:Mon, 2:Tue...etc

	a = (14 - Date.Month) / 12;
	y = Date.Year - a;
	m = Date.Month + 12 * a - 2;

	return (Date.Day + y + (y / 4) - (y / 100) + (y / 400) + (31 * m / 12)) % 7;
}

string DayOfWeekOrderScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tDay Of Week Order.\n";
	cout << "====================================\n";

	stDate Date = ReadFullDate();
	short Answer = DayOfWeekOrder(Date);

	return to_string(Answer);
}

// (7) Define Print Month Calender Functions.
string DayShortName(short DayOfWeekOrder)
{
	string arrNameOfDaysWeek[7] = { "Sun","Mon","Tue","Wed","Thu","Fri","Sat" };
	return arrNameOfDaysWeek[DayOfWeekOrder];

}

string MonthShortName(short MonthNumber)
{
	string Months[12] = { "Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec" };
	return Months[MonthNumber - 1];
}

void PrintMonthCalender(stDate Date)
{
	short NumberOfDays = NumberOfDaysInMonth(Date.Year, Date.Month);

	// Index of the Day from 0 to 6 
	short Current = DayOfWeekOrder(Date);

	// Print Current Month name
	printf("\n--------------%s-------------- \n\n", MonthShortName(Date.Month).c_str());

	// Print the Colums 
	printf("  Sun  Mon  Tue  Wed  Thu  Fri  Sat\n");
	// Print appropriate Spaces
	short i;
	for (i = 0; i < Current; i++)
		printf("     ");

	for (short j = 1; j <= NumberOfDays; j++)
	{
		printf("%5d", j);

		if (++i == 7)
		{
			i = 0;
			printf("\n");
		}
	}
	cout << "\n---------------------------------\n";
}

void PrintMonthCalenderScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tPrint Month Calender.\n";
	cout << "====================================\n";

	short year = ReadYear();
	short month = ReadMonth();

	stDate Date;
	Date.Month = month, Date.Year = year, Date.Day = 1;
	PrintMonthCalender(Date);

}

// (8) Define Print Month Calender Functions.
void PrintCalenderYear(stDate Date)
{
	printf("\n------------------------------------\n");
	printf("       Calender - %d", Date.Year);
	printf("\n------------------------------------\n");


	for (short Month = 1; Month <= 12; Month++)
	{
		Date.Month = Month;
		PrintMonthCalender(Date);
	}
}

// (9) Define Print Year Calender Functions.
void PrintYearCalenderScreen()
{
	system("cls");
	cout << "====================================\n";
	cout << "\tPrint Year Calender.\n";
	cout << "====================================\n";

	short year = ReadYear();

	stDate Date;
	Date.Year = year;

	PrintCalenderYear(Date);
}

// (10) Define Total Days From The Beginning Of Year Functions.
short TotalDaysFromTheBeginningOfYear(stDate Date)
{
	short TotalDays = 0, i;

	for (i = 1; i <= Date.Month - 1; i++)
	{
		TotalDays += NumberOfDaysInMonth(Date.Year, i);
	}
	return TotalDays + Date.Day;
}

string TotalDaysFromTheBeginningOfYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "Total Days From The Beginning Of Year.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	short Answer = TotalDaysFromTheBeginningOfYear(Date);

	return to_string(Answer);
}

// (11) Define Get Date From Day Order In Year Functions.
stDate GetDateFromDayOrderInYear(short DateOrderInYear, short Year)
{
	stDate Date;
	short RemainingDays = DateOrderInYear;
	short MonthDays = 0;

	Date.Year = Year;
	Date.Month = 1;

	while (true)
	{
		MonthDays = NumberOfDaysInMonth(Year, Date.Month);

		if (RemainingDays > MonthDays)
		{
			RemainingDays -= MonthDays;
			Date.Month++;
		}
		else
		{
			Date.Day = RemainingDays;
			break;
		}
	}
	return Date;
}

string DateToString(stDate Date)
{
	return to_string(Date.Day) + "/" + to_string(Date.Month) + "/" + to_string(Date.Year);
}

string GetDateFromDayOrderInYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "   Get Date From Day Order In Year.\n";
	cout << "=====================================\n";

	short Day = ReadDay();
	short Year = ReadYear();

	stDate Date = GetDateFromDayOrderInYear(Day, Year);

	return DateToString(Date);
}

// (12) Define Date add days Functions.
stDate DateAddDays(short Days, stDate Date)
{
	short RemainingDays = Days + TotalDaysFromTheBeginningOfYear(Date);
	short DaysMonth = 0;

	Date.Month = 1;

	while (true)
	{
		DaysMonth = NumberOfDaysInMonth(Date.Year, Date.Month);

		if (RemainingDays > DaysMonth)
		{
			RemainingDays -= DaysMonth;
			Date.Month++;

			if (Date.Month > 12)
			{
				Date.Year++;
				Date.Month = 1;
			}
		}

		else
		{
			Date.Day = RemainingDays;
			break;
		}
	}
	return Date;
}

int ReadUserInput(string Massage)
{
	int Days = 0;

	cout << "Enter number of " << Massage;
	cin >> Days;

	return Days;
}

string DateAddDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDate add days.\n";
	cout << "=====================================\n";

	short Days = ReadUserInput("Days");
	stDate date = ReadFullDate();

	stDate Date = DateAddDays(Days, date);

	return DateToString(Date);
}

// (13) Define Get system date Functions.
stDate GetSystemDate()
{
	time_t  CurrentTime = time(0); // Get the current time in secoinds
	tm* Time = localtime(&CurrentTime);

	stDate Date;
	Date.Day = Time->tm_mday;
	Date.Month = (Time->tm_mon + 1);
	Date.Year = (Time->tm_year + 1900);

	return Date;
}

string GetSystemDateScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tGet system date.\n";
	cout << "=====================================\n";
	return DateToString(GetSystemDate());
}
 
// (14) Define Is Date1 Before Date2 Functions.
bool IsDate1BeforeDate2(stDate Date1, stDate Date2)
{
	return  (Date1.Year < Date2.Year) ? true : ((Date1.Year == Date2.Year) ? (Date1.Month < Date2.Month ? true : (Date1.Month == Date2.Month ? Date1.Day < Date2.Day : false)) : false);
}

string IsDate1BeforeDate2Screen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Date1 Before Date2.\n";
	cout << "=====================================\n";
	
	cout << "Enter date 1:\n";
	stDate Date1 = ReadFullDate();
	cout << "Enter date 2:\n";
	stDate Date2 = ReadFullDate();

	bool Answer = IsDate1BeforeDate2(Date1, Date2);

	return (Answer == 1) ? "True" : "False";
}

// (15) Define Is Date1 Equal Date2 Functions.
bool IsDate1EqualDate2(stDate Date1, stDate Date2)
{
	return (Date1.Year == Date2.Year) ? ((Date1.Month == Date2.Month) ? ((Date1.Day == Date2.Day) ? true : false) : false) : false;
}

string IsDate1EqualDate2Screen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Date1 Equal Date2.\n";
	cout << "=====================================\n";

	cout << "Enter date 1:\n";
	stDate Date1 = ReadFullDate();
	cout << "Enter date 2:\n";
	stDate Date2 = ReadFullDate();

	bool Answer = IsDate1EqualDate2(Date1, Date2);

	return (Answer == 1) ? "True" : "False";
}

// (16) Define Is Date1 After Date2 Functions.
bool IsDate1AfterDate2(stDate Date1, stDate Date2)
{
	return  !IsDate1BeforeDate2(Date1, Date2) && !IsDate1EqualDate2(Date1, Date2);
}

string IsDate1AfterDate2Screen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Date1 After Date2.\n";
	cout << "=====================================\n";

	cout << "Enter date 1:\n";
	stDate Date1 = ReadFullDate();
	cout << "Enter date 2:\n";
	stDate Date2 = ReadFullDate();

	bool Answer = IsDate1AfterDate2(Date1, Date2);

	return (Answer == 1) ? "True" : "False";
}

// (17) Define Is Last Day In Month Functions.
bool IsLastDayInMonth(stDate Date)
{
	return (Date.Day == NumberOfDaysInMonth(Date.Year, Date.Month));
}

string IsLastDayInMonthScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Last Day In Month.\n";
	cout << "=====================================\n";
	
	stDate Date = ReadFullDate();
	bool Answer = IsLastDayInMonth(Date);

	return (Answer == 1) ? "True" : "False";
}

// (18) Define Is Last Month In Year Functions.
bool IsLasMonthInYear(short Month)
{
	return (Month == 12);
}

string IsLasMonthInYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Last Month In Year.\n";
	cout << "=====================================\n";

	short Month = ReadMonth();
	bool Answer = IsLasMonthInYear(Month);

	return (Answer == 1) ? "True" : "False";
}

// (19) Define Is Date In Period Functions.
enum enDateCompare { Before = -1, Equal = 0, After = 1 };

enDateCompare CompareDates(stDate Date1, stDate Date2)
{
	if (IsDate1BeforeDate2(Date1, Date2))
		return enDateCompare::Before;

	if (IsDate1EqualDate2(Date1, Date2))
		return enDateCompare::Equal;

	/*if (IsDate1AfterDate2(Date1, Date2))
		return enDateCompare::After;*/

		// This is faster
	return enDateCompare::After;
}

bool IsDateInPeriod(stDate Date, stPeriod Period)
{
	return !(CompareDates(Date, Period.StartDate) == enDateCompare::Before || CompareDates(Date, Period.EndDate) == enDateCompare::After);
}

string IsDateInPeriodScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Date In Period.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	stPeriod Period = ReadPeriod();

	bool Answer = IsDateInPeriod(Date, Period);

	return (Answer == 1) ? "True" : "False";
}

// (20) Define Is Valid Date Functions.
bool IsValidDate(stDate Date)
{
	return (Date.Year > 0) ? (Date.Month >= 1 || Date.Month <= 12 ? (Date.Day <= NumberOfDaysInMonth(Date.Year, Date.Month) ? true : false) : false) : false;
}

string IsValidDateScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Valid Date.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	bool Answer = IsValidDate(Date);

	return (Answer == 1) ? "True" : "False";
}

// (21) Define Is Overlap Periods Functions.
bool IsOverlapPeriods(stPeriod Period1, stPeriod Period2)
{
	if (
		CompareDates(Period2.EndDate, Period1.StartDate) == enDateCompare::Before
		||
		CompareDates(Period2.StartDate, Period1.EndDate) == enDateCompare::After
		)
		return false;
	else
		return true;
}

string IsOverlapPeriodsScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Overlap Periods.\n";
	cout << "=====================================\n";

	cout << "Enter Period 1 :\n";
	stPeriod Period1 = ReadPeriod();
	cout << "Enter Period 2 :\n";
	stPeriod Period2 = ReadPeriod();

	bool Answer = IsOverlapPeriods(Period1, Period2);

	return (Answer == 1) ? "True" : "False";
}

// (22) Define Get Difference In Days Functions.
void SwapDate1AndDate2(stDate& Date1, stDate& Date2)
{
	stDate Temp;

	Temp.Day = Date1.Day;
	Temp.Month = Date1.Month;
	Temp.Year = Date1.Year;

	Date1.Day = Date2.Day;
	Date1.Month = Date2.Month;
	Date1.Year = Date2.Year;

	Date2.Day = Temp.Day;
	Date2.Month = Temp.Month;
	Date2.Year = Temp.Year;
}

stDate IncrementDateByOneDay(stDate  Date)
{
	if (IsLastDayInMonth(Date))
	{
		if (IsLasMonthInYear(Date.Month))
		{
			Date.Day = 1;
			Date.Month = 1;
			Date.Year++;
		}
		else
		{
			Date.Day = 1;
			Date.Month++;
		}
	}
	else
	{
		Date.Day++;
	}
	return Date;
}

short GetDifferenceInDays(stDate Date1, stDate Date2, bool IncludeEndDay = false)
{
	short Days = 0;
	short SwapFlageValue = 1;

	if (!IsDate1BeforeDate2(Date1, Date2))
	{
		SwapDate1AndDate2(Date1, Date2);
		SwapFlageValue = -1;
	}

	while (IsDate1BeforeDate2(Date1, Date2))
	{
		Days++;
		Date1 = IncrementDateByOneDay(Date1);
	}

	return IncludeEndDay ? ++Days * SwapFlageValue : Days * SwapFlageValue;
}

string GetDifferenceInDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tGet Difference In Days.\n";
	cout << "=====================================\n";

	cout << "Enter Data 1 :\n";
	stDate Date1 = ReadFullDate();
	cout << "Enter Data 2 :\n";
	stDate Date2 = ReadFullDate();
	
	return to_string(GetDifferenceInDays(Date1, Date2));
}

// (23) Define Increment Date By One Day Functions.
string IncrementDateByOneDayScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "     Increment Date By One Day.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	return DateToString(IncrementDateByOneDay(Date));
}

// (24) Define Increase Date By X Days Functions.
stDate IncreaseDateByXDays(stDate Date, short IncreasedDays)
{
	for (short i = 0; i < IncreasedDays; i++)
	{
		Date = IncrementDateByOneDay(Date);
	}
	return Date;
}

string IncreaseDateByXDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By X Days.\n";
	cout << "=====================================\n";

	short Days = ReadUserInput("Days");
	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByXDays(Date, Days));
}

// (25) Define Increase Date By One Week Functions.
stDate IncreaseDateByOneWeek(stDate Date)
{
	for (short i = 0; i < 7; i++)
	{
		Date = IncrementDateByOneDay(Date);
	}
	return Date;
}

string IncreaseDateByOneWeekScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By One Week.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneWeek(Date));
}

// (26) Define Increase Date By X Week Functions.
stDate IncreaseDateByXWeeks(stDate Date, short IncreasedWeeks)
{
	for (short i = 0; i < IncreasedWeeks; i++)
	{
		Date = IncreaseDateByOneWeek(Date);
	}
	return Date;
}

string IncreaseDateByXWeeksScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By X Week.\n";
	cout << "=====================================\n";

	short Weeks = ReadUserInput("Weeks");
	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByXWeeks(Date, Weeks));
}

// (27) Define Increase Date By One Month Functions.
stDate IncreaseDateByOneMonth(stDate Date)
{
	if (IsLasMonthInYear(Date.Month))
	{
		Date.Month = 1;
		Date.Year++;
	}
	else
	{
		Date.Month++;
	}

	//last check day in date should not exceed max days in the current month
	// example if date is 31/1/2022 increasing one month should not be 31/2/2022, it should
	// be 28/2/2022

	short NumberOfDaysInCurrentMonth = NumberOfDaysInMonth(Date.Year, Date.Month);
	if (Date.Day > NumberOfDaysInCurrentMonth)
	{
		Date.Day = NumberOfDaysInCurrentMonth;
	}

	return Date;
}

string IncreaseDateByOneMonthScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By One Month.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneMonth(Date));
}

// (28) Define Increase Date By X Month Functions.
stDate IncreaseDateByXMonth(stDate Date, short IncreasedMonths)
{
	for (short i = 0; i < IncreasedMonths; i++)
	{
		Date = IncreaseDateByOneMonth(Date);
	}
	return Date;
}

string IncreaseDateByXMonthScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By X Month.\n";
	cout << "=====================================\n";

	short Months = ReadUserInput("Months");
	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByXMonth(Date, Months));
}

// (29) Define Increase Date By One Year Functions.
stDate IncreaseDateByOneYear(stDate Date)
{
	Date.Year++;
	return Date;
}

string IncreaseDateByOneYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By One Year .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneYear(Date));
}

// (30) Define Increase Date By X Year Functions.
stDate IncreaseDateByXYearFaster(stDate Date, short IncreasedYears)
{
	Date.Year += IncreasedYears;
	return Date;
}

string IncreaseDateByXYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIncrease Date By X Year .\n";
	cout << "=====================================\n";

	short Years = ReadUserInput("Years");
	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByXYearFaster(Date, Years));
}

// (31) Define Increase Date By One Decade Functions.
stDate IncreaseDateByOneDecade(stDate Date)
{
	Date.Year += 10;
	return Date;
}

string IncreaseDateByOneDecadeScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Increase Date By One Decade .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneDecade(Date));
}

// (32) Define Increase Date By One Century Functions.
stDate IncreaseDateByOneCentury(stDate Date)
{
	Date.Year += 100;
	return Date;
}

string IncreaseDateByOneCenturyScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Increase Date By One Century .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneCentury(Date));
}

// (33) Define Increase Date By One Millennium Functions.
stDate IncreaseDateByOneMillennium(stDate Date)
{
	Date.Year += 1000;
	return Date;
}

string IncreaseDateByOneMillenniumScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Increase Date By One Millennium .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(IncreaseDateByOneMillennium(Date));
}

// (34) Define Decrement Date By One Day Functions.
stDate DecrementDateByOneDay(stDate Date)
{
	if (Date.Day == 1)
	{
		if (Date.Month == 1)
		{
			Date.Day = 31;
			Date.Month = 12;
			Date.Year--;
		}
		else
		{
			Date.Day = NumberOfDaysInMonth(Date.Year, Date.Month - 1);
			Date.Month--;
		}
	}
	else
	{
		Date.Day--;
	}
	return Date;
}

string DecrementDateByOneDayScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "     Decrement Date By One Day.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	return DateToString(DecrementDateByOneDay(Date));
}

// (35) Define Decrease Date By X Days Functions.
stDate DecreaseDateByXDays(stDate Date, short Days)
{
	for (short i = 1; i <= Days; i++)
	{
		Date = DecrementDateByOneDay(Date);
	}
	return Date;
}

string  DecreaseDateByXDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By X Days.\n";
	cout << "=====================================\n";

	short Days = ReadUserInput("Days");
	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByXDays(Date, Days));
}

// (36) Define Decrease Date By One Week Functions.
stDate DecreaseDateByOneWeek(stDate Date)
{
	for (short i = 1; i <= 7; i++)
	{
		Date = DecrementDateByOneDay(Date);
	}
	return Date;
}

string DecreaseDateByOneWeekScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By One Week.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneWeek(Date));
}

// (37) Define Decrease Date By X Week Functions.
stDate DecreaseDateByXWeeks(stDate Date, short Weeks)
{
	for (short i = 1; i <= Weeks; i++)
	{
		Date = DecreaseDateByOneWeek(Date);
	}
	return Date;
}

string DecreaseDateByXWeeksScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By X Week.\n";
	cout << "=====================================\n";

	short Weeks = ReadUserInput("Weeks");
	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByXWeeks(Date, Weeks));
}

// (38) Define Decrease Date By One Month Functions.
stDate DecreaseDateByOneMonth(stDate Date)
{
	if (Date.Month == 1)
	{
		Date.Month = 12;
		Date.Year--;
	}
	else
	{
		Date.Month--;
	}

	short NumberOfDaysInCurrentMonth = NumberOfDaysInMonth(Date.Year, Date.Month);
	if (Date.Day > NumberOfDaysInCurrentMonth)
	{
		Date.Day = NumberOfDaysInCurrentMonth;
	}
	return Date;
}

string DecreaseDateByOneMonthScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By One Month.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneMonth(Date));
}

// (39) Define Decrease Date By X Month Functions.
stDate DecreaseDateByXMonths(stDate Date, short Months)
{
	for (short i = 0; i < Months; i++)
	{
		Date = DecreaseDateByOneMonth(Date);
	}
	return Date;
}

string DecreaseDateByXMonthsScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By X Month.\n";
	cout << "=====================================\n";

	short Months = ReadUserInput("Months");
	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByXMonths(Date, Months));
}

// (40) Define Decrease Date By One Year Functions.
stDate DecreaseDateByOneYear(stDate Date)
{
	Date.Year--;
	return Date;
}

string DecreaseDateByOneYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By One Year .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneYear(Date));
}

// (41) Define Decrease Date By X Year Functions.
stDate DecreaseDateByXYearsFaster(stDate Date, short Years)
{
	Date.Year -= Years;
	return Date;
}

string DecreaseDateByXYearsScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDecrement Date By X Year .\n";
	cout << "=====================================\n";

	short Years = ReadUserInput("Years");
	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByXYearsFaster(Date, Years));
}

// (42) Define Decrease Date By One Decade Functions.
stDate DecreaseDateByOneDecade(stDate Date)
{
	Date.Year -= 10;
	return Date;
}

string DecreaseDateByOneDecadeScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Decrement Date By One Decade .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneDecade(Date));
}

// (43) Define Decrease Date By One Century Functions.
stDate DecreaseDateByOneCentury(stDate Date)
{
	Date.Year -= 100;
	return Date;
}

string DecreaseDateByOneCenturyScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Decrement Date By One Century .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneCentury(Date));
}

// (44) Define Decrease Date By One Millennium Functions.
stDate DecreaseDateByOneMillennium(stDate Date)
{
	Date.Year -= 1000;
	return Date;
}

string DecreaseDateByOneMillenniumScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Decrement Date By One Millennium .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return DateToString(DecreaseDateByOneMillennium(Date));
}

// (45) Define Days Until End Of Month Functions.
short DaysUntilEndOfMonth(stDate Date)
{
	stDate EndOfMonthDate;

	EndOfMonthDate.Day = NumberOfDaysInMonth(Date.Year, Date.Month);
	EndOfMonthDate.Month = Date.Month;
	EndOfMonthDate.Year = Date.Year;

	return GetDifferenceInDays(Date, EndOfMonthDate, true);
}

string DaysUntilEndOfMonthScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDays Until End Of Month .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return to_string(DaysUntilEndOfMonth(Date));
}

// (46) Define Days Until End Of Year Functions.
short DaysUntilEndOfYear(stDate Date)
{
	stDate EndOfYearDate;

	EndOfYearDate.Day = 31;
	EndOfYearDate.Month = 12;
	EndOfYearDate.Year = Date.Year;

	return GetDifferenceInDays(Date, EndOfYearDate, true);
}

string DaysUntilEndOfYearScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDays Until End Of Year .\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();

	return to_string(DaysUntilEndOfYear(Date));
}

// (47) Define Is End Of Week Functions.
bool IsEndOfWeek(stDate Date)
{
	return DayOfWeekOrder(Date) == 6;
}

string IsEndOfWeekScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs End Of Week.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	bool Answer = IsEndOfWeek(Date);

	return (Answer == 1) ? "True" : "False";
}

// (48) Define Is Week End Functions.
bool IsWeekEnd(stDate Date)
{
	short DayIndex = DayOfWeekOrder(Date);
	return (DayIndex == 5 || DayIndex == 6);
}

string IsWeekEndScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Week End.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	bool Answer = IsWeekEnd(Date);

	return (Answer == 1) ? "True" : "False";
}

// (49) Define Is Businees Day Functions.
bool IsBusineesDay(stDate Date)
{
	//Weekends are Sun,Mon,Tue,Wed and Thur
	/*
	short DayIndex = DayOfWeekOrder(Date.Day, Date.Month, Date.Year);
	return  (DayIndex >= 5 && DayIndex <= 4);
	*/

	//shorter method is to invert the IsWeekEnd: this will save updating code.
	return !IsWeekEnd(Date);
}

string IsBusineesDayScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tIs Businees Day.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	bool Answer = IsBusineesDay(Date);

	return (Answer == 1) ? "True" : "False";
}

// (50) Define Days Until End Of Week Functions.
short DaysUntilEndOfWeek(stDate Date)
{
	return (6 - DayOfWeekOrder(Date));
}

string DaysUntilEndOfWeekScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tDays Until End Of Week.\n";
	cout << "=====================================\n";

	stDate Date = ReadFullDate();
	return to_string(DaysUntilEndOfWeek(Date));

}

// (51) Define Calculate Period Length In Days Functions.
short CalculatePeriodLengthInDays(stPeriod Period, bool IncludeEndDay = false)
{
	return GetDifferenceInDays(Period.StartDate, Period.EndDate, IncludeEndDay);
}

string CalculatePeriodLengthInDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "  Calculate Period Length In Days.\n";
	cout << "=====================================\n";

	stPeriod Period = ReadPeriod();
	return to_string(CalculatePeriodLengthInDays(Period));

}

// (52) Define Count Over lapDays Functions.
short CountOverlapDays_1(stPeriod Period1, stPeriod Period2)
{
	if (!IsOverlapPeriods(Period1, Period2))
		return 0;

	stDate StartOverlap, EndOverlap;

	StartOverlap = CompareDates(Period1.StartDate, Period2.StartDate) == enDateCompare::Before ? Period2.StartDate : Period1.StartDate;
	EndOverlap = CompareDates(Period1.EndDate, Period2.EndDate) == enDateCompare::Before ? Period1.EndDate : Period2.EndDate;

	return GetDifferenceInDays(StartOverlap, EndOverlap);
}

string CountOverlapDaysScreen()
{
	system("cls");
	cout << "=====================================\n";
	cout << "\tCount Over lapDays.\n";
	cout << "=====================================\n";

	cout << "Enter Period 1 :\n";
	stPeriod Period1 = ReadPeriod();
	cout << "Enter Period 2 :\n";
	stPeriod Period2 = ReadPeriod();

	return to_string(CountOverlapDays_1(Period1, Period1));

}

// Perform User Option.
void PerformMainMenuOptions(stOperationInfo OperationInfo,string &result)
{
	switch (OperationInfo.OperationName)
	{
	case eIsLeapYear:
		 result = IsLeapYearScreen();
		 break;

	case eNumberOfDaysInMonth:
		 result = NumberOfDaysInMonthScreen();
		 break;

	case eNumberOfHoursInAmonth:
		 result = NumberOfHoursInAmonthScreen();
		 break;

	case eNumberOfMinutesInAmonth:
		 result = NumberOfMinutesInAmonthScreen();
		 break;

	case eNumberOfSecondsInAmonth:
		 result = NumberOfSecondsInAmonthScreen();
		 break;

	case eDayOfWeekOrder:
		 result = DayOfWeekOrderScreen();
		 break;

	case ePrintMonthCalender:
		result = "Empty";
		PrintMonthCalenderScreen();
		break;

	case ePrintCalenderYear:
		result = "Empty";
		PrintYearCalenderScreen();
		break;

	case eTotalDaysFromTheBeginningOfYrar:
		result = TotalDaysFromTheBeginningOfYearScreen();
		break;

	case eGetDateFromDayOrderInYear:
		result = GetDateFromDayOrderInYearScreen();
		break;

	case eDateAddDays:
		result = DateAddDaysScreen();
		break;

	case eGetSystemDate:
		result = GetSystemDateScreen();
		break;

	case eIsDate1BeforeDate2:
		result = IsDate1BeforeDate2Screen();
		break;

	case eIsDate1EqualDate2:
		result = IsDate1EqualDate2Screen();
		break;

	case eIsDate1AfterDate2:
		result = IsDate1AfterDate2Screen();
		break;

	case eIsLastDayInMonth:
		result = IsLastDayInMonthScreen();
		break;

	case eIsLasMonthInYear:
		result = IsLasMonthInYearScreen();
		break;

	case eIsDateInPeriod:
		result = IsDateInPeriodScreen();
		break;

	case eIsValidDate:
		result = IsValidDateScreen();
		break;

	case eIsOverlapPeriods:
		result = IsOverlapPeriodsScreen();
		break;

	case eGetDifferenceInDays:
		result = GetDifferenceInDaysScreen();
		break;

	case eIncreaseDateByOneDay:
		result = IncrementDateByOneDayScreen();
		break;

	case eIncreaseDateByXDays:
		result = IncreaseDateByXDaysScreen();
		break;

	case eIncreaseDateByOneWeek:
		result = IncreaseDateByOneWeekScreen();
		break;

	case eIncreaseDateByXWeeks:
		result = IncreaseDateByXWeeksScreen();
		break;

	case eIncreaseDateByOneMonth:
		result = IncreaseDateByOneMonthScreen();
		break;

	case eIncreaseDateByXMonth:
		result = IncreaseDateByXMonthScreen();
		break;

	case eIncreaseDateByOneYear:
		result = IncreaseDateByOneYearScreen();
		break;

	case eIncreaseDateByXYear:
		result = IncreaseDateByXYearScreen();
		break;

	case eIncreaseDateByOneDecade:
		result = IncreaseDateByOneDecadeScreen();
		break;

	case eIncreaseDateByOneCentury:
		result = IncreaseDateByOneCenturyScreen();
		break;

	case eIncreaseDateByOneMillennium:
		result = IncreaseDateByOneMillenniumScreen();
		break;

	case eDecrementDateByOneDay:
		result = DecrementDateByOneDayScreen();
		break;

	case eDecreaseDateByXDays:
		result = DecreaseDateByXDaysScreen();
		break;

	case eDecreaseDateByOneWeek:
		result = DecreaseDateByOneWeekScreen();
		break;

	case eDecreaseDateByXWeeks:
		result = DecreaseDateByXWeeksScreen();
		break;

	case eDecreaseDateByOneMonth:
		result = DecreaseDateByOneMonthScreen();
		break;

	case eDecreaseDateByXMonths:
		result = DecreaseDateByXMonthsScreen();
		break;

	case eDecreaseDateByOneYear:
		result = DecreaseDateByOneYearScreen();
		break;

	case eDecreaseDateByXYears:
		result = DecreaseDateByXYearsScreen();
		break;

	case eDecreaseDateByOneDecade:
		result = DecreaseDateByOneDecadeScreen();
		break;

	case eDecreaseDateByOneCentury:
		result = DecreaseDateByOneCenturyScreen();
		break;

	case eDecreaseDateByOneMillennium:
		result = DecreaseDateByOneMillenniumScreen();
		break;

	case eDaysUntilEndOfMonth:
		result = DaysUntilEndOfMonthScreen();
		break;

	case eDaysUntilEndOfYear:
		result = DaysUntilEndOfYearScreen();
		break;

	case eIsEndOfWeek:
		result = IsEndOfWeekScreen();
		break;

	case eIsWeekEnd:
		result = IsWeekEndScreen();
		break;

	case eIsBusineesDay:
		result = IsBusineesDayScreen();
		break;

	case eDaysUntilEndOfWeek:
		result = DaysUntilEndOfWeekScreen();
		break;

	case eCalculatePeriodLengthInDays:
		result = CalculatePeriodLengthInDaysScreen();
		break;

	case eCountOverlapDays:
		result = CountOverlapDaysScreen();
		break;
	}
}

void PrintResult(string result)
{
	if (result != "Empty")
	{
		cout << "\n==============================\n";
		cout << "\tResult is :";
		cout << "\n------------------------------\n";
		cout << "\t" << result;
		cout << "\n==============================\n";
	}
}

void start()
{
	char answer = 'y';
	do
	{
		ShowMainMenuOptions();
		stOperationInfo OperationInfo;

		OperationInfo.OperationName = GetUserChoice();
		PerformMainMenuOptions(OperationInfo, OperationInfo.result);

		PrintResult(OperationInfo.result);

		// Ask user if he want to do another operation.
		cout << "\nDo you wnat to do another operation Y/N ? ";
		cin >> answer;

	} while (toupper(answer) == 'Y');
}

int main()
{
	start();
	system("pause>0");

	return 0;
}
