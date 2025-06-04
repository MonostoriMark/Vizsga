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




## Objektum létrehozás
```
internal class adat
{
    public string szerelo;
    public List<string> gepek = new List<string>();
    public bool[] munka = new bool[7];
    public int minosites;
    public adat(string sor)
    {
        string[] szet = sor.Split(',');
        this.szerelo = szet[0];
        int utso = szet.Length-1;
        this.minosites = int.Parse(szet[utso]);
        for (int i = 1; i < szet.Length-8; i++)
        {
            gepek.Add(szet[i]);

        }
        int f = 6;
        for (int i = szet.Length-2; i > szet.Length-9; i--)
        {
            if (szet[i] == "X")
            {
                munka[f] = true;                    
            }
            f--;
        }
    }
}
```

## File beolvasás
```

List<adat> szerelok = new List<adat>();

StreamReader reader = new StreamReader("pest.csv", Encoding.UTF8);

while (!reader.EndOfStream)
{
    szerelok.Add(new adat(reader.ReadLine()));
}
Console.WriteLine("1. feladat: A fájl beolvasása sikeres!");

```


## Form Objektum dinamikus létrehozás
```
CheckBox[] mezok = new CheckBox[10];

int x = 15;
int y = 110;

for (int i = 0; i < 10; i++) 
    {
        CheckBox cb = new CheckBox();
        cb.AutoSize = true;
        cb.Location = new Point(x, y);
        mezok[i, j] = cb;
        this.Controls.Add(cb);
        x += 26;
        
    }


```