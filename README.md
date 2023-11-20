# Fork of Real Estate Api
 Using .NET 8 and MySql (instead of MS Sql Server)

# ToDo's before running the solution
 1. create a Db and an user in your MySql Server
 2. modify Database, UserID and Password in the OnConfiguring method of RealEstateApi/RealEstateApi/Data/ApiDbContext.cs. 
    - example:
         ```
        protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
        {
            var connectionStringBuilder = new MySqlConnectionStringBuilder();
            connectionStringBuilder.Server = "localhost";
            connectionStringBuilder.Database = "realEstateApi01";
            connectionStringBuilder.Port = 3306;
            connectionStringBuilder.UserID = "realEstateApiUser";
            connectionStringBuilder.Password = "myPassword";

            var connectionString = connectionStringBuilder.ToString();
            var serverVersion = ServerVersion.AutoDetect(connectionString);
            optionsBuilder.UseMySql(connectionString, serverVersion);
        }
        ```
3. create migrations via 'Package Manager Console': `Add-Migration InitialCreate`
