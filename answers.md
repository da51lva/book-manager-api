1. Get All Books - This GET is at endpoint /api/v1/book and routed to BookManagerController.getAllBooks(). The
   controller used the BookManagerService to deal with the logic of getting all the books. The service interacts with
   the Repository that acts as an abstraction in front of the DB and returns all the entities from the DB being used.
   The only entity is book, and the ORM converts the database results into the model. The service then returns the
   objects from the repo to the controller, which builds and response object which is returned to the client.
2. Get Book by ID - This GET is at endpoint /api/v1/book/{bookId} and routed to the BookManagerController.getBookByID().
   Almost identical to the previous feature. The only difference is the Service calls a different method on the repo to
   return the book for a given ID.
3. Add Book - This POST is at endpoint /api/v1/book and routed to the BookManagerController.addBook(). This time The
   RequestBody contains a JSON representing the book to be added. The @RequestBody annotation automatically
   de-serializes the body into the Model. The controller passes the book the service to deal with the logic of adding
   the book. The service uses the repo to add the book to the DB. The controller creates a response object containing
   JSON format of the newly created book, and a header which contains the endpoint to GET the newly created book.
4. Update Book - The PUT is at endpoint /api/v1/book/{bookId} and routed to BookManagerController.updateBookById(). The
   ID of the book to be updated is given in the endpoint, and the updated values are given in the RequestBody as a JSON.
   Again the logic responsibilities are passed to the Service, which uses the Repo to retrieve the book for the given
   ID, then updates the objects values with the given ones, then uses the Repo to save this to the DB. A response is
   returned to the uses containing the ID of the updated book