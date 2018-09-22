---
title: Modyfikowanie dużej wartości (maksymalna) danych w ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: ea079a0b55dde8df7b3442f3d604b2b6467ba785
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584334"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modyfikowanie dużej wartości (maksymalna) danych w ADO.NET
Typy danych dużego obiektu (LOB) to te, które przekraczają maksymalny rozmiar wiersza 8 kilobajtów (KB). SQL Server udostępnia `max` specyfikatorem `varchar`, `nvarchar`, i `varbinary` typy danych, aby zezwolić na przechowywanie wartości jest większy niż 2 ^ 32 bajtów. Kolumny w tabeli i zmienne języka Transact-SQL może określić, czy `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` typów danych. W ADO.NET `max` typy danych mogą być pobierane przez `DataReader`i może zostać określony jako obie wartości parametrów wejściowych i wyjściowych, bez żadnej specjalnej obsługi. Dla dużych `varchar` typy danych, dane można je pobrać i zaktualizować przyrostowo.  
  
 `max` Typy danych mogą być używane, porównań, jako zmienne języka Transact-SQL i łączenia. One można również w DISTINCT, klauzula ORDER BY, klauzule GROUP BY w instrukcji SELECT, a także w agregacje, sprzężenia i podzapytania.  
  
 Poniższa tabela zawiera linki do dokumentacji w dokumentacji SQL Server — książki Online.  
  
 **SQL Server — książki Online**  
  
1.  [Używanie typów danych dużych wartości](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Ograniczenia typu duża wartość  
 Poniższe ograniczenia mają zastosowanie do `max` typy danych, które nie istnieją dla mniejszych typów danych:  
  
-   A `sql_variant` nie mogą zawierać dużą `varchar` typu danych.  
  
-   Duże `varchar` kolumn nie można określić jako kolumna klucza w indeksie. Są one dozwolone w kolumną dołączaną w nieklastrowanym indeksie.  
  
-   Duże `varchar` kolumn nie można używać jako kolumny klucza partycji.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Praca z typami dużej wartości w języku Transact-SQL  
 Języka Transact-SQL `OPENROWSET` funkcji jest metodą jednorazowego łączenia i uzyskiwania dostępu do danych zdalnych. Zawiera wszystkie informacje o połączeniu niezbędnych do uzyskania dostępu zdalnego danych ze źródła danych OLE DB. `OPENROWSET` mogą być przywoływane w klauzuli FROM zapytania, tak jakby był to nazwa tabeli. Jest również mogą być przywoływane jako tabeli docelowej instrukcji INSERT, UPDATE, lub instrukcję DELETE, zależą od możliwości dostawcy OLE DB.  
  
 `OPENROWSET` Funkcja zawiera `BULK` dostawcy zestawu wierszy, który umożliwia odczytywanie danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej. Dzięki temu można używać `OPENROWSET` w prostej instrukcji INSERT SELECT.  
  
 `OPENROWSET BULK` Argumentach opcji zapewniają znaczących kontrolę nad miejsce do rozpoczęcia i zakończenia, Odczyt danych, sposób postępowania z błędami i sposobu interpretowania danych. Na przykład można określić, że plik danych go odczytywać jako pojedynczy wiersz tabeli, jedna kolumna zestaw wierszy typu `varbinary`, `varchar`, lub `nvarchar`. O pełnej składni i opcjach zobacz dokumentację SQL Server — książki Online.  
  
 Poniższy przykład wstawia zdjęcie do tabeli ProductPhoto w przykładowej bazy danych AdventureWorks. Korzystając z `BULK OPENROWSET` dostawcę, należy podać nazwana lista kolumn, nawet jeśli nie są wstawiania wartości do każdej kolumny. Klucz podstawowy w tym przypadku jest zdefiniowana jako kolumna tożsamości i można pominąć na liście kolumn. Należy pamiętać, że nazwa korelacji na koniec należy również podać `OPENROWSET` instrukcję, która w tym przypadku jest thumbnailphoto usługa. To jest skorelowane z kolumną w `ProductPhoto` tabeli, w którym plik jest ładowany.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizowanie danych za pomocą aktualizacji. ZAPIS  
 Instrukcja UPDATE języka Transact-SQL zawiera nową składnię zapisu do modyfikowania zawartości `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` kolumn. Dzięki temu można przeprowadzić aktualizacje częściowe dane. Aktualizacja. ZAPISU czy składnia jest wyświetlana w tym miejscu, w skrócie:  
  
 UPDATE  
  
 {  *\<obiektu >* }  
  
 SET  
  
 { *column_name* = {. ZAPIS ( *wyrażenie* , @Offset , @Length )}  
  
 Metody zapisu określa, że część wartości *column_name* zostaną zmodyfikowane. Wyrażenie jest wartością, która zostanie skopiowany do *column_name*, `@Offset` to punkt początkowy, w którym zostanie zapisany wyrażenia, i `@Length` argument jest długość sekcji w kolumnie.  
  
|IF|Następnie|  
|--------|----------|  
|Wyrażenie ma wartość NULL|`@Length` jest ignorowana, a wartość w *column_name* został obcięty w określonym `@Offset`.|  
|`@Offset` ma wartość NULL|Operacja aktualizacji dołącza do wyrażenia na końcu istniejącej *column_name* wartość i `@Length` jest ignorowana.|  
|`@Offset` jest większa niż długość wartości column_name|Program SQL Server zwraca błąd.|  
|`@Length` ma wartość NULL|Operacja aktualizacji spowoduje usunięcie wszystkich danych z `@Offset` na końcu `column_name` wartość.|  
  
> [!NOTE]
>  Ani `@Offset` ani `@Length` może być liczbą ujemną.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie języka Transact-SQL aktualizuje wartość częściowa w DocumentSummary, `nvarchar(max)` kolumny w tabeli dokumentu w bazie AdventureWorks. Słowo "składniki" zastępuje słowo "funkcji", określając słowa zastępczego, lokalizacja początku (przesunięciem) programu word, który ma zostać zastąpione w istniejących danych i liczba znaków do zastąpienia (długości). Przykład zawiera instrukcji "SELECT" przed i po instrukcji UPDATE, aby porównać wyniki.  
  
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
 Możesz pracować z typu duża wartość w ADO.NET, określając typy duża wartość jako <xref:System.Data.SqlClient.SqlParameter> obiekty w <xref:System.Data.SqlClient.SqlDataReader> do zwrócenia wyniku zostały ustawione, lub za pomocą <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia `DataSet` / `DataTable`. Nie ma różnic między sposób pracy z typem dużej wartości i jej typem danych powiązane, mniejsze wartości.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Używanie GetSqlBytes do pobierania danych  
 `GetSqlBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Używanie GetSqlChars do pobierania danych  
 `GetSqlChars` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varchar(max)` lub `nvarchar(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `nvarchar(max)` danych z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Używanie GetSqlBinary do pobierania danych  
 `GetSqlBinary` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli i <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBinary> strumienia.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Używanie GetBytes do pobierania danych  
 `GetBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z przesunięcia określonej kolumny do tablicy typu byte, rozpoczynając od przesunięcia określonej tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , pobiera bajtów z tablicy bajtów. Należy zauważyć, że w przeciwieństwie do `GetSqlBytes`, `GetBytes` wymagany rozmiar buforu tablicy.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Pobieranie danych przy użyciu elementu GetValue  
 `GetValue` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje wartość od przesunięcia określonej kolumny do tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` pobiera dane binarne z pierwszej kolumny przesunięcie i następnie ciągu danych z drugiego przesunięcia kolumny.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Konwersja z typu duża wartość na typy CLR  
 Możesz przekonwertować zawartość `varchar(max)` lub `nvarchar(max)` kolumny przy użyciu dowolnej z metod konwersji ciągów, takich jak `ToString`. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.  
  
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
 Poniższy kod pobiera nazwę i `LargePhoto` obiektu z `ProductPhoto` tabelę `AdventureWorks` bazy danych i zapisuje je do pliku. Zestaw musi być skompilowana przy użyciu odwołania do <xref:System.Drawing> przestrzeni nazw.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.SqlTypes.SqlBytes> obiekt ujawniający `Stream` właściwości. Kod używa tych informacji do tworzenia nowego `Bitmap` obiektu, a następnie zapisuje je w plik Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Za pomocą parametrów typu duża wartość  
 Duża wartość mogą być używane w <xref:System.Data.SqlClient.SqlParameter> obiektów w taki sam sposób, możesz użyć wartości mniejsze typy w <xref:System.Data.SqlClient.SqlParameter> obiektów. Można pobrać typu duża wartość jako <xref:System.Data.SqlClient.SqlParameter> wartości, jak pokazano w poniższym przykładzie. W kodzie założono, że Poniższa procedura przechowywana GetDocumentSummary istnieje w przykładowej bazy danych AdventureWorks. Procedura składowana przyjmuje parametr wejściowy o nazwie @DocumentID i zwraca zawartość w kolumnie DocumentSummary @DocumentSummary parametr wyjściowy.  
  
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
 Tworzy kod ADO.NET <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiekty wykonywanie procedury przechowywane GetDocumentSummary i pobierania dokumentu podsumowania, które są przechowywane jako typu duża wartość. Kod przekazuje wartość @DocumentID wprowadź parametr i wyświetla wyniki przekazany z powrotem do @DocumentSummary parametr w oknie konsoli danych wyjściowych.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
