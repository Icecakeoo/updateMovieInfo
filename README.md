# updateMovieInfo
updateMovieInfo uf
public void updateMovieInfo() {
    Scanner scanner = new Scanner(System.in);
    
    System.out.println("Enter movie ID to update information: ");
    int movieId = scanner.nextInt();
    
    // Fetch movie details from database using movieId
    Movie movie = MovieDatabase.getMovieById(movieId);
    
    if (movie != null) {
        System.out.println("Current movie details:");
        System.out.println("Title: " + movie.getTitle());
        System.out.println("Description: " + movie.getDescription());
        
        System.out.println("Enter new movie title: ");
        String newTitle = scanner.nextLine();
        
        System.out.println("Enter new movie description: ");
        String newDescription = scanner.nextLine();
        
        // Update movie details in database
        movie.setTitle(newTitle);
        movie.setDescription(newDescription);
        MovieDatabase.updateMovie(movie);
        
        System.out.println("Movie information updated successfully!");
    } else {
        System.out.println("Movie not found with ID: " + movieId);
    }
}
