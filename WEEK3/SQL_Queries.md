SQL Queries to create tables
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
