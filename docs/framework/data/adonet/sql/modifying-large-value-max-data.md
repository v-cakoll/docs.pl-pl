---
title: Modyfikowanie danych o dużej wartości (maks.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174280"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET
Typy danych dużych obiektów (LOB) to te, które przekraczają maksymalny rozmiar wiersza 8 kilobajtów (KB). SQL Server `max` zapewnia specyfikator `nvarchar`dla `varbinary` `varchar`, i typów danych, aby umożliwić przechowywanie wartości tak dużych, jak 2 ^ 32 bajtów. Kolumny tabeli i zmienne Transact-SQL mogą określać `varchar(max)`, `nvarchar(max)`lub `varbinary(max)` typy danych. W ADO.NET, typy `max` danych mogą być pobierane przez `DataReader`, i może być również określony jako wartości parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi. W `varchar` przypadku dużych typów danych dane mogą być pobierane i aktualizowane stopniowo.  
  
 Typy `max` danych mogą służyć do porównań, jako zmienne Transact-SQL i do łączenia. Mogą być również używane w distinct, ORDER BY, GROUP BY klauzule SELECT instrukcji, jak również w agregatach, sprzężenia i podksyrii.  
  
 Poniższa tabela zawiera łącza do dokumentacji w programie SQL Server Books Online.  
  
 **SQL Server documentation (Dokumentacja programu SQL Server)**  
  
1. [Korzystanie z typów danych o dużej wartości](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Ograniczenia typu o dużej wartości  
 Następujące ograniczenia mają zastosowanie `max` do typów danych, które nie istnieją dla mniejszych typów danych:  
  
- A `sql_variant` nie może `varchar` zawierać dużego typu danych.  
  
- Dużych `varchar` kolumn nie można określić jako kolumny klucza w indeksie. Są one dozwolone w dołączonej kolumnie w indeksie nieklastrowanym.  
  
- Dużych `varchar` kolumn nie można używać jako partycjonowania kolumn klucza.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Praca z typami dużych wartości w transact-SQL  
 Funkcja Transact-SQL `OPENROWSET` jest jednorazową metodą łączenia i uzyskiwania dostępu do zdalnych danych. Zawiera wszystkie informacje o połączeniu niezbędne do uzyskania dostępu do zdalnych danych ze źródła danych OLE DB. `OPENROWSET`można odwoływać się w klauzuli FROM kwerendy tak, jakby była to nazwa tabeli. Można również odwoływać się jako tabela docelowa wstawić, UPDATE, lub DELETE instrukcji, z zastrzeżeniem możliwości dostawcy OLE DB.  
  
 Funkcja `OPENROWSET` obejmuje `BULK` dostawcę zestawu wierszy, który umożliwia odczytywanie danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej. Umożliwia to użycie `OPENROWSET` w prostej instrukcji INSERT SELECT.  
  
 Argumenty `OPENROWSET BULK` opcji zapewniają znaczną kontrolę nad tym, od czego zacząć i zakończyć odczyt danych, jak radzić sobie z błędami i jak dane są interpretowane. Na przykład można określić, że plik danych będzie odczytywany jako jednowierszowy, jednokolumnowy zestaw wierszy typu `varbinary`, `varchar`lub `nvarchar`. Aby uzyskać pełną składnię i opcje, zobacz SQL Server Books Online.  
  
 Poniższy przykład wstawia zdjęcie do productphoto tabeli w adventureworks przykładowej bazy danych. Podczas korzystania `BULK OPENROWSET` z dostawcy, należy podać nazwany listy kolumn, nawet jeśli nie są wstawiania wartości do każdej kolumny. Klucz podstawowy w tym przypadku jest zdefiniowany jako kolumna tożsamości i może zostać pominięty na liście kolumn. Należy również zauważyć, że należy również podać nazwę `OPENROWSET` korelacji na końcu instrukcji, która w tym przypadku jest ThumbnailPhoto. Jest to skorelowane `ProductPhoto` z kolumną w tabeli, do której jest ładowany plik.  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Aktualizowanie danych za pomocą aktualizacji . Napisz  
 Instrukcja Transact-SQL UPDATE zawiera nową składnię WRITE `varchar(max)` `nvarchar(max)`do `varbinary(max)` modyfikowania zawartości , lub kolumn. Dzięki temu można wykonać częściowe aktualizacje danych. Aktualizacja . Składnia WRITE jest tutaj pokazana w formie skróconej:  
  
 UPDATE  
  
 { * \<>obiektu* }  
  
 SET  
  
 { *column_name* = { . WRITE *expression* ( @Offset wyrażenie @Length , , ) }  
  
 Write Metoda określa, że sekcja wartości *column_name* zostaną zmodyfikowane. Wyrażenie jest wartością, która zostanie *column_name*skopiowana do `@Offset` column_name , jest to punkt początkowy, w `@Length` którym wyrażenie zostanie napisane, a argument jest długością sekcji w kolumnie.  
  
|Jeśli użytkownik|Następnie|  
|--------|----------|  
|Wyrażenie jest ustawione na NULL|`@Length`jest ignorowana, a wartość w *column_name* jest obcinana w określonym `@Offset`pliku .|  
|`@Offset`ma wartość NULL|Operacja aktualizacji dołącza wyrażenie na końcu istniejącej wartości *column_name* i `@Length` jest ignorowana.|  
|`@Offset`jest większa niż długość wartości column_name|Program SQL Server zwraca błąd.|  
|`@Length`ma wartość NULL|Operacja aktualizacji usuwa wszystkie `@Offset` dane z do `column_name` końca wartości.|  
  
> [!NOTE]
> Ani `@Offset` nie `@Length` może być ani liczba ujemna.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Transact-SQL aktualizuje wartość częściową w documentsummary, kolumnie `nvarchar(max)` w tabeli Dokument w bazie danych AdventureWorks. Wyraz "składniki" zastępuje się słowem "features" przez określenie słowa zastępczego, początkowej lokalizacji (przesunięcia) wyrazu, który ma zostać zastąpiony w istniejących danych, oraz liczby znaków, które mają zostać zastąpione (długość). Przykład zawiera instrukcje SELECT przed i po update instrukcji, aby porównać wyniki.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Praca z typami o dużych wartościach w ADO.NET  
 Można pracować z dużymi typami wartości w ADO.NET, <xref:System.Data.SqlClient.SqlParameter> określając duże <xref:System.Data.SqlClient.SqlDataReader> typy wartości jako obiekty <xref:System.Data.SqlClient.SqlDataAdapter> w celu `DataSet` / `DataTable`zwrócenia zestawu wyników lub za pomocą a do wypełnienia . Nie ma różnicy między sposobem pracy z typem dużej wartości a powiązanym z nim typem danych o mniejszej wartości.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Pobieranie danych za pomocą getsqlBytes  
 Metoda `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `varbinary(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli <xref:System.Data.SqlTypes.SqlBytes>i obiekt o nazwie, który pobiera dane jako .  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Pobieranie danych za pomocą programu GetSqlChars  
 Metoda `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varchar(max)` kolumny lub `nvarchar(max)` kolumny. Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `nvarchar(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli i obiekt o nazwie, który pobiera dane.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Pobieranie danych za pomocą funkcji GetSqlBinary  
 Metoda `GetSqlBinary` a <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada `cmd` obiekt o `varbinary(max)` nazwie, który <xref:System.Data.SqlClient.SqlDataReader> wybiera `reader` dane z tabeli <xref:System.Data.SqlTypes.SqlBinary> i obiekt o nazwie, który pobiera dane jako strumień.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Pobieranie danych za pomocą getbytów  
 Metoda `GetBytes` <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z określonej kolumny przesuniętej do tablicy bajtów, zaczynając od określonego przesunięcia tablicy. Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera bajty do tablicy bajtów. Należy zauważyć, `GetSqlBytes` `GetBytes` że w przeciwieństwie do , wymaga rozmiaru buforu tablicy.  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Pobieranie danych za pomocą funkcji GetValue  
 Metoda `GetValue` odczytuje <xref:System.Data.SqlClient.SqlDataReader> wartość z określonej kolumny przesuniętej do tablicy. Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera dane binarne z pierwszego przesunięcia kolumny, a następnie ciąg danych z drugiej kolumny przesunięcie.  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Konwertowanie z dużych typów wartości na typy CLR  
 Zawartość `varchar(max)` kolumny można `nvarchar(max)` przekonwertować przy użyciu dowolnej metody `ToString`konwersji ciągów, takiej jak . Poniższy fragment kodu <xref:System.Data.SqlClient.SqlDataReader> zakłada `reader` obiekt o nazwie, który pobiera dane.  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Przykład  
 Poniższy kod pobiera nazwę `LargePhoto` i obiekt `ProductPhoto` z `AdventureWorks` tabeli w bazie danych i zapisuje go w pliku. Zestaw musi być skompilowany z <xref:System.Drawing> odwołaniem do obszaru nazw.  Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.SqlTypes.SqlBytes> obiekt, który udostępnia `Stream` właściwość. Kod używa tego do utworzenia nowego `Bitmap` obiektu, a następnie `ImageFormat`zapisuje go w pliku Gif .  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Korzystanie z parametrów typu dużej wartości  
 Duże typy wartości <xref:System.Data.SqlClient.SqlParameter> mogą być używane w obiektach <xref:System.Data.SqlClient.SqlParameter> w taki sam sposób, w jaki używane są mniejsze typy wartości w obiektach. Można pobrać duże typy <xref:System.Data.SqlClient.SqlParameter> wartości jako wartości, jak pokazano w poniższym przykładzie. Kod zakłada, że następująca procedura składowana GetDocumentSummary istnieje w przykładowej bazie danych AdventureWorks. Procedura składowana przyjmuje parametr @DocumentID wejściowy o nazwie i zwraca zawartość @DocumentSummary kolumny DocumentSummary w parametrze wyjściowym.  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Przykład  
 Kod ADO.NET tworzy <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów do wykonania GetDocumentSummary procedury składowanej i pobrać podsumowanie dokumentu, który jest przechowywany jako typ dużej wartości. Kod przekazuje wartość parametru wejściowego @DocumentID i wyświetla wyniki @DocumentSummary przekazane z powrotem w parametrze wyjściowym w oknie konsoli.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Operacje danych serwera SQL w ADO.NET](sql-server-data-operations.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
