SQL Queries to create tables
COUNTRY TABLE
CREATE TABLE Country (
    country_code TEXT PRIMARY KEY,
    country_name TEXT NOT NULL
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
    FOREIGN KEY (country_code) REFERENCES Countries(country_code)
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
    FOREIGN KEY (Country_Code) REFERENCES Countries(Country_Code) -- Referential Integrity
);
