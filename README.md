# DatabasesWithSQLProject

Uses the chinook.db database to do the following two tasks. solutions for both Parts at the bottom of this page

Part 1
The 'company' you work for has decided to hire a new bi-lingual support position. Your job is to locate all users who have purchased a Spanish language track and assign them to this new support representative. The new support representative's id is 6. Sales has begun to identify all the albums that are classified as Spanish language, so far they have found AlbumId's of 8, 21, 22, 23, 24, 25, 26, 27, 28, 29, 32, 33, 34, 41, 42, 45, 47, 52, 53.

Part 2
Next, it's been requested that we create a new table that can be used to generate shipping labels for thank you packages. Create a new table named TopCustomers that has fields for first name, last name, address, city, state, postal code, and phone number. Fill this table with the relevant data for any customer that has spent at least $10.


Part 1 solution

UPDATE SupportRepId
SET SupportRepId = 6
FROM customers JOIN invoices USING(CustomerId)
JOIN invoice_items USING(InvoiceId)
JOIN tracks USING(TrackId)
WHERE AlbumId IN(8, 21, 22, 23, 24, 25, 26, 27, 28, 29, 32, 33, 34, 41, 42, 45, 47, 52, 53)



Part 2 Solution 
CREATE Table TopCustomers (
Customer Id INTEGER,
FirstName VARCHAR(50) NOT NULL,
LastName VARCHAR(50) NOT NULL, 
Address VARCHAR(100),
City VARCHAR(50),
State VARCHAR (25), 
PostalCode INTEGER, 
PhoneNumber VARCHAR (20))

SELECT CustomerId, FirstName, LastName, Address, City, State, PostalCode, PhoneNumber
INTO TopCustomers
FROM customers JOIN invoices USING(customerID)
WHERE total > 10
