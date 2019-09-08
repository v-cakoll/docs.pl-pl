---
title: Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 34f0a61329667a42aa42693e93169a5b6fb0aa5e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792043"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET
Typy danych dużego obiektu (LOB) to te, które przekraczają maksymalny rozmiar wiersza wynoszący 8 kilobajtów (KB). SQL Server udostępnia `max` specyfikator dla `varchar`, `nvarchar` i`varbinary` typów danych, aby umożliwić przechowywanie wartości o rozmiarze maksymalnie 2 ^ 32 bajtów. Kolumny tabeli i zmienne języka Transact-SQL mogą `varchar(max)`określać, `varbinary(max)` `nvarchar(max)`lub typy danych. W ADO.NET `max` typy danych mogą być pobierane `DataReader`przez i można również określić jako wartości parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi. W przypadku `varchar` dużych typów danych można pobrać i zaktualizować dane przyrostowo.  
  
 Typy `max` danych mogą służyć do porównań, jako zmienne Transact-SQL, oraz do łączenia. Mogą być również używane w klauzulach DISTINCT, ORDER BY, GROUP BY instrukcji SELECT, a także w agregacjach, sprzężeniach i podzapytaniach.  
  
 Poniższa tabela zawiera linki do dokumentacji w SQL Server książki online.  
  
 **Książka SQL Server online**  
  
1. [Korzystanie z typów danych o dużej wartości](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Ograniczenia typu dużej wartości  
 Następujące ograniczenia mają zastosowanie do `max` typów danych, które nie istnieją dla mniejszych typów danych:  
  
- A `sql_variant` nie może zawierać dużego `varchar` typu danych.  
  
- Nie `varchar` można określić dużych kolumn jako kolumny klucza w indeksie. Są one dozwolone w uwzględnionej kolumnie w nieklastrowanym indeksie.  
  
- Nie `varchar` można używać dużych kolumn jako kolumn klucza partycjonowania.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Praca z typami dużej wartości w języku Transact-SQL  
 Funkcja Transact-SQL `OPENROWSET` to jednorazowa Metoda łączenia się i uzyskiwania dostępu do danych zdalnych. Zawiera wszystkie informacje o połączeniu niezbędne do uzyskania dostępu do danych zdalnych ze źródła danych OLE DB. `OPENROWSET`można odwoływać się do klauzuli FROM zapytania, tak jakby była nazwą tabeli. Może być również przywoływany jako tabela docelowa instrukcji INSERT, UPDATE lub DELETE, z uwzględnieniem możliwości dostawcy OLE DB.  
  
 `OPENROWSET` Funkcja zawieradostawcęzestawuwierszy,któryumożliwiaodczytywaniedanychbezpośredniozplikubezładowania`BULK` danych do tabeli docelowej. Umożliwia to korzystanie `OPENROWSET` z prostej instrukcji INSERT SELECT.  
  
 Argumenty `OPENROWSET BULK` opcji zapewniają znaczącą kontrolę nad tym, gdzie rozpocząć i zakończyć odczytywanie danych, jak rozwiązywać problemy oraz jak interpretować dane. Na przykład można określić, że plik danych ma być odczytywany jako pojedynczy wiersz zestawu wierszy jednokolumnowych typu `varbinary`, `varchar`, lub `nvarchar`. Pełną składnię i opcje można znaleźć w temacie SQL Server Books Online.  
  
 Poniższy przykład wstawia zdjęcie do tabeli ProductPhoto w przykładowej bazie danych AdventureWorks. W przypadku korzystania `BULK OPENROWSET` z dostawcy należy podać nazwę listy kolumn, nawet jeśli nie wstawiasz wartości do każdej kolumny. Klucz podstawowy w tym przypadku jest definiowany jako kolumna tożsamości i może zostać pominięty z listy kolumn. Należy pamiętać, że należy również podać nazwę korelacji na końcu `OPENROWSET` instrukcji, która w tym przypadku jest thumbnailPhoto. Jest to skorelowane z kolumną w `ProductPhoto` tabeli, do której plik jest ładowany.  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Aktualizowanie danych przy użyciu polecenia UPDATE. PRAWEM  
 Instrukcja UPDATE języka Transact-SQL ma nową składnię zapisu do modyfikowania zawartości `varchar(max)`, `nvarchar(max)`lub `varbinary(max)` kolumn. Dzięki temu można wykonywać częściowe aktualizacje danych. Aktualizacja. Składnia zapisu jest wyświetlana w skróconej formie:  
  
 UPDATE  
  
 *{\<Object >* }  
  
 SET  
  
 { *column_name* = {. ZAPIS ( *wyrażenie* , @Offset , @Length )}  
  
 Metoda WRITE określa, że sekcja wartości *column_name* zostanie zmodyfikowana. Wyrażenie jest wartością, która zostanie skopiowana do *column_name*, `@Offset` jest punktem początkowym, w którym wyrażenie zostanie `@Length` napisane, a argument jest długością sekcji w kolumnie.  
  
|IF|Następnie|  
|--------|----------|  
|Wyrażenie jest ustawione na wartość NULL.|`@Length`jest ignorowany, a wartość w *column_name* jest obcinana do `@Offset`określonego.|  
|`@Offset`ma wartość NULL|Operacja Update dołącza wyrażenie na końcu istniejącej wartości *column_name* i `@Length` jest ignorowane.|  
|`@Offset`jest większa niż długość wartości column_name|SQL Server zwraca błąd.|  
|`@Length`ma wartość NULL|Operacja Update usuwa wszystkie dane z `@Offset` do końca `column_name` wartości.|  
  
> [!NOTE]
> `@Offset` Aninie`@Length` może być liczbą ujemną.  
  
## <a name="example"></a>Przykład  
 Ten przykład Transact-SQL aktualizuje wartość częściową w DocumentSummary, `nvarchar(max)` w kolumnie tabeli dokumentów w bazie danych AdventureWorks. Słowo "Components" jest zastępowane słowem "Features", określając wyraz zamienny, początkową lokalizację (przesunięcie) wyrazu, który ma zostać zastąpiony w istniejących danych, oraz liczbę znaków, które mają zostać zastąpione (długość). Przykład zawiera instrukcje SELECT przed i po instrukcji UPDATE, aby porównać wyniki.  
  
```  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Praca z typami dużej wartości w ADO.NET  
 Możesz współpracować z dużymi typami wartości w ADO.NET, określając duże typy wartości jako <xref:System.Data.SqlClient.SqlParameter> obiekty <xref:System.Data.SqlClient.SqlDataReader> w w celu zwrócenia zestawu wyników lub przy / <xref:System.Data.SqlClient.SqlDataAdapter> `DataSet` `DataTable`użyciu do wypełnienia. Nie ma różnicy między sposobem pracy z dużym typem wartości i powiązanymi danymi o mniejszych wartości.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Pobieranie danych za pomocą GetSqlBytes  
 Metoda może służyć do`varbinary(max)`pobieraniazawartościkolumny. `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlCommand> Poniższy fragment kodu zakłada, że obiekt o nazwie `cmd` wybiera `varbinary(max)` dane z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiekt o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Pobieranie danych za pomocą GetSqlChars  
 Metoda może służyć `nvarchar(max)` do`varchar(max)` pobierania zawartości kolumny lub. <xref:System.Data.SqlClient.SqlDataReader> `GetSqlChars` Poniższy fragment kodu <xref:System.Data.SqlClient.SqlCommand> zakłada, że obiekt o nazwie `cmd` wybiera `nvarchar(max)` dane z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiekt o nazwie `reader` pobierającej dane.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Pobieranie danych za pomocą GetSqlBinary  
 Metoda a <xref:System.Data.SqlClient.SqlDataReader> może służyć do `varbinary(max)` pobierania zawartości kolumny. `GetSqlBinary` <xref:System.Data.SqlClient.SqlCommand> Poniższy fragment kodu zakłada, że obiekt o nazwie `cmd` wybiera `varbinary(max)` dane z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiekt o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBinary> strumień.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Pobieranie danych przy użyciu GetBytes  
 `GetBytes` Metoda a<xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z określonej kolumny przesunięte do tablicy bajtów, rozpoczynając od określonego przesunięcia tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> , że obiekt o nazwie `reader` pobiera bajty do tablicy bajtów. Należy pamiętać, że w `GetSqlBytes`przeciwieństwie do, `GetBytes` wymaga rozmiaru buforu tablicy.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Pobieranie danych za pomocą GetValue  
 `GetValue` Metoda a<xref:System.Data.SqlClient.SqlDataReader> odczytuje wartość z przesunięcia określonego kolumny do tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> , że obiekt o nazwie `reader` pobiera dane binarne z pierwszego przesunięcia kolumny, a następnie dane ciągu z przesunięcia drugiej kolumny.  
  
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
 Możesz przekonwertować zawartość `varchar(max)` kolumny lub `nvarchar(max)` , używając dowolnej z metod konwersji ciągów, takich jak `ToString`. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> , że obiekt o nazwie `reader` pobiera dane.  
  
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
 Poniższy kod pobiera nazwę i `LargePhoto` obiekt `ProductPhoto` z tabeli w `AdventureWorks` bazie danych i zapisuje je w pliku. Zestaw musi być skompilowany z odwołaniem do <xref:System.Drawing> przestrzeni nazw.  Metoda zwraca obiekt, który uwidacznia`Stream` właściwość. <xref:System.Data.SqlTypes.SqlBytes> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Kod używa tego do utworzenia nowego `Bitmap` obiektu, a następnie zapisuje go w formacie GIF. `ImageFormat`  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Używanie parametrów typu dużej wartości  
 W <xref:System.Data.SqlClient.SqlParameter> obiektach można używać dużych typów wartości w taki sam sposób jak w przypadku mniejszych typów <xref:System.Data.SqlClient.SqlParameter> wartości w obiektach. Możesz pobrać duże typy wartości jako <xref:System.Data.SqlClient.SqlParameter> wartości, jak pokazano w poniższym przykładzie. W kodzie założono, że w przykładowej bazie danych AdventureWorks istnieje następująca procedura składowana GetDocumentSummary. Procedura składowana przyjmuje parametr wejściowy o nazwie @DocumentID i zwraca zawartość kolumny DocumentSummary @DocumentSummary w parametrze Output.  
  
```  
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
 Kod ADO.NET tworzy <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiektów do wykonania procedury składowanej GetDocumentSummary i pobiera podsumowanie dokumentu, który jest przechowywany jako typ dużej wartości. Kod przekazuje wartość @DocumentID parametru wejściowego i wyświetla wyniki przekazane z powrotem @DocumentSummary w parametrze danych wyjściowych w oknie konsoli.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Operacje danych serwera SQL w ADO.NET](sql-server-data-operations.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
