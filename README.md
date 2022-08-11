int query = entityManager.createNativeQuery("INSERT INTO rating (ident,game, username, rating, rated_on) SELECT ?,?, ?, ?, ? WHERE NOT EXISTS (SELECT username FROM rating WHERE username = ?); UPDATE rating SET rating = ? WHERE EXISTS (SELECT username FROM rating WHERE username = ?) AND username = ?")
                .setParameter(1, 100)
                .setParameter(2, game)
                .setParameter(3, username)
                .setParameter(4, 5)
                .setParameter(5, new Date())
                .setParameter(6, username)
                .setParameter(7, 5)
                .setParameter(8, username)
                .setParameter(9, username).executeUpdate();