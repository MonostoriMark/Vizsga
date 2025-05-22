## Adatbázis megnyitás és olvasás
```    
InitializeComponent();
var build = new MySqlConnectionStringBuilder { Server = "127.0.0.1", UserID = "root", Password = "", Database = "dbname"};
kapcsolat = new MySqlConnection(build.ConnectionString);
kapcsolat.Open();

List<Seller> a = new List<Seller>();

var command = kapcsolat.CreateCommand();
command.CommandText = "SELECT * FROM sellers ORDER BY name;";
var reader = command.ExecuteReader();

while (reader.Read())
{
    Seller tmp = new Seller();
    tmp.Id = reader.GetInt32("id");
    tmp.Name = reader.GetString("name");
    tmp.Phone = reader.GetString("phone");

    a.Add(tmp);
}

reader.Close();

```