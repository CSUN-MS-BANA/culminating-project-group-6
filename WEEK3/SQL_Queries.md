SQL Queries to Create Tables

COUNTRY TABLE
CREATE TABLE Country (
    country_code TEXT PRIMARY KEY,
    country_name TEXT NOT NULL
);

ECONOMIC INDICATORS TABLE
CREATE TABLE Economic (
    Series_code TEXT,
    Year INTEGER,
    Series_Name TEXT,
    Value INTEGER,
    Country_code TEXT,
    PRIMARY KEY (Series_code, Year),
    FOREIGN KEY (Country_code) REFERENCES Country(Country_code)
);


PUBLIC DEBT INDICATORS TABLE
CREATE TABLE Public_Debt_Indicators (
    series_code INTEGER,
    country_code TEXT,
    year INTEGER,
    series_name TEXT,
    value INTEGER
    PRIMARY KEY (series_code, year),
    FOREIGN KEY (country_code) REFERENCES Country(country_code)
);

--SOCIAL INDICATORS TABLE--
CREATE TABLE Social_Indicators (
    Series_Code TEXT NOT NULL,               -- Unique identifier for each indicator (Primary Key)
    Year INTEGER NOT NULL,                   -- Year (e.g., 2021, 2022, 2023) (Primary Key)
    Country_Code TEXT NOT NULL,              -- Foreign key referencing the Countries table
    Series_Name TEXT NOT NULL,               -- Description of the indicator
    Value REAL,                              -- Corresponding numerical value for that year
    PRIMARY KEY (Series_Code, Year),         -- Composite Primary Key (Unique per indicator & year)
    FOREIGN KEY (Country_Code) REFERENCES Country(Country_Code) -- Referential Integrity
);

--Environmental Indicators Table--
CREATE TABLE Environmental_Indicators (
    country_code VARCHAR(10) NOT NULL,        -- Foreign key referencing the Countries table
    series_name VARCHAR(255) NOT NULL,        -- Description of the indicator
    series_code VARCHAR(50) NOT NULL,         -- Unique identifier for each indicator (Primary Key)
    year INT NOT NULL,                        -- Year (Primary Key)
    value DECIMAL,
    PRIMARY KEY (series_code, year)
    FOREIGN KEY (Country_Code) REFERENCES Country(Country_Code)
);

Statistical Indicators Table
CREATE TABLE Statistical_Indicators (
    Series_ID TEXT,
    Year INTEGER,
    Series_Name TEXT,
    Value TEXT,
    Country_code TEXT,
    PRIMARY KEY (Series_code, Year),
    FOREIGN KEY (Country_code) REFERENCES Country(Country_code)
);

