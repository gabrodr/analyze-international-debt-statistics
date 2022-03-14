# analyze-international-debt-statistics
Quick project provided by DataCamp to practice importing, cleaning, and manipulating datasets with SQL. All datasets and questions provided by DataCamp.

-- 1. SELECT all of the columns from the international_debt table and LIMIT the output to the first ten rows to keep the output clean.

SELECT * 
FROM international_debt
LIMIT 10;

-- 2. Finding the number of distinct countries

SELECT COUNT(DISTINCT country_name) AS total_distinct_countries
FROM international_debt;

-- 3. Finding out the distinct debt indicators

SELECT DISTINCT indicator_code as distinct_debt_indicators
FROM international_debt
ORDER BY distinct_debt_indicators

-- 4. Totaling the amount of debt owed by the countries

SELECT ROUND(SUM(debt)/1000000, 2) as total_debt
FROM international_debt; 

-- 5. Country with the highest debt

SELECT country_name, SUM(debt) as total_debt
FROM international_debt
GROUP BY country_name
ORDER BY total_debt DESC 
LIMIT 1;

-- 6. Average amount of debt across indicators

SELECT indicator_code AS debt_indicator, indicator_name, AVG(debt) as average_debt
FROM international_debt
GROUP BY debt_indicator, indicator_name
ORDER BY average_debt DESC
LIMIT 10;

-- 7. The highest amount of principal repayments

SELECT country_name, indicator_name
FROM international_debt
WHERE debt = (SELECT MAX(debt) FROM international_debt);

-- 8 . The most common debt indicator

SELECT indicator_code, COUNT(indicator_code) as indicator_count
FROM international_debt
GROUP BY indicator_code
ORDER BY indicator_count DESC, indicator_code DESC
LIMIT 20;

-- 9. Other viable debt issues and conclusion

SELECT country_name, MAX(debt) as maximum_debt
FROM international_debt
GROUP BY country_name
ORDER BY maximum_debt DESC
LIMIT 10;
