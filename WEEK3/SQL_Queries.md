SQL Queries to create tables
COUNTRY TABLE
CREATE TABLE Country (
    country_code TEXT PRIMARY KEY,
    country_name TEXT NOT NULL
);

ECONOMIC INDICATORS TABLE
CREATE TABLE Economic (
    Series_ID TEXT,
    Year INTEGER,
    GDP TEXT,
    Inflation_Rate TEXT,
    Trade_Balance TEXT,
    Foreign_Direct_Investment TEXT,
    Government_Spending TEXT,
    Country_Country_ID TEXT,
    PRIMARY KEY (Series_ID, Year, Country_Country_ID),
    FOREIGN KEY (Country_Country_ID) REFERENCES Country(Country_ID)
);


PUBLIC DEBT INDICATORS TABLE
CREATE TABLE Public_Debt_Indicators (
    series_code INTEGER,
    country_code TEXT,
    year INTEGER,
    total_government_debt REAL,
    debt_to_gdp_ratio REAL,
    interest_payments_on_debt REAL,
    external_debt_stocks REAL,
    PRIMARY KEY (series_code, year),
    FOREIGN KEY (country_code) REFERENCES Country(country_code)
);

--SOCIAL INDICATORS TABLE--
CREATE TABLE Social_Indicators (
    Series_Code TEXT NOT NULL,               -- Unique identifier for each indicator (Primary Key)
    Year INTEGER NOT NULL,                   -- Year (e.g., 2021, 2022, 2023) (Primary Key)
    Country_Code TEXT NOT NULL,              -- Foreign key referencing the Countries table
    Country_Name TEXT NOT NULL,              -- Name of the country
    Series_Name TEXT NOT NULL,               -- Description of the indicator
    Value REAL,                              -- Corresponding numerical value for that year
    PRIMARY KEY (Series_Code, Year),         -- Composite Primary Key (Unique per indicator & year)
    FOREIGN KEY (Country_Code) REFERENCES Country(Country_Code) -- Referential Integrity
);

--Environmental indicator Table--
CREATE TABLE Environmental_Indicators (
    country_name VARCHAR(100) NOT NULL,       -- Name of the country
    country_code VARCHAR(10) NOT NULL,        -- Foreign key referencing the Countries table
    series_name VARCHAR(255) NOT NULL,        -- Description of the indicator
    series_code VARCHAR(50) NOT NULL,         -- Unique identifier for each indicator (Primary Key)
    year INT NOT NULL,                        -- Year (Primary Key)
    value DECIMAL(15,6),
    PRIMARY KEY (series_code, year)
    FOREIGN KEY (Country_Code) REFERENCES Country(Country_Code)
);
