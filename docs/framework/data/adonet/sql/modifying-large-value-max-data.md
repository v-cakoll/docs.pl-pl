---
title: "Modyfikowanie dużej wartości (wartość maksymalna) danych ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3a80f316ffc3380408802fefe1a26d71e5e76ac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modyfikowanie dużej wartości (wartość maksymalna) danych ADO.NET
Typy danych dużego obiektu (LOB) to przekracza maksymalny rozmiar wiersza 8 kilobajtów (KB). Program SQL Server stanowi `max` specyfikatora `varchar`, `nvarchar`, i `varbinary` typy danych umożliwiają przechowywanie wartości tak duże jak 2 ^ 32 bajtów. Kolumny tabeli i zmienne języka Transact-SQL może określać `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` typów danych. W ADO.NET `max` typy danych mogą być pobierane przez `DataReader`, a także można określić jako wartości obu parametrów wejściowych i wyjściowych bez żadnej specjalnej obsługi. Dla dużych `varchar` typy danych, dane można je pobrać i zaktualizować przyrostowo.  
  
 `max` Dla porównania jako zmienne języka Transact-SQL i łączenia można używać typów danych. Ich można również w DISTINCT, ORDER BY, klauzul GROUP BY w instrukcji SELECT, a także w agregacji, sprzężeń i podzapytania.  
  
 Poniższa tabela zawiera linki do dokumentacji programu SQL Server — książki Online.  
  
 **SQL Server — książki Online**  
  
1.  [Używanie typów danych dużych wartości](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Ograniczenia typu duża wartość  
 Następujące ograniczenia dotyczące `max` typy danych, które nie istnieją dla mniejszych typów danych:  
  
-   A `sql_variant` nie może zawierać dużej `varchar` — typ danych.  
  
-   Duże `varchar` kolumny nie można określić jako kolumna klucza w indeksie. Mogą w kolumnie uwzględnione w nieklastrowanym indeksie.  
  
-   Duże `varchar` kolumn nie można używać jako kolumny klucza partycji.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Praca z typami duża wartość w języku Transact-SQL  
 Języka Transact-SQL `OPENROWSET` funkcja to jednorazowe metoda łączenia i uzyskiwania dostępu do danych zdalnych. Zawiera wszystkie informacje o połączeniu niezbędnych do uzyskania dostępu zdalnego danych ze źródła danych OLE DB. `OPENROWSET`może być przywoływany w klauzuli FROM zapytania tak, jakby była nazwą tabeli. Jego mogą się też odwoływać jako do tabeli docelowej instrukcji INSERT, UPDATE, lub usuń instrukcji, zależnie od możliwości dostawcy OLE DB.  
  
 `OPENROWSET` Funkcja zawiera `BULK` dostawca zestawów wierszy, dzięki czemu można odczytać danych bezpośrednio z pliku bez ładowania danych do tabeli docelowej. Pozwala na użycie `OPENROWSET` w prostej instrukcji INSERT SELECT.  
  
 `OPENROWSET``BULK` Argumentów opcji zapewniają znaczny kontrolę nad gdzie rozpoczynać i kończyć odczytywanie danych, sposób postępowania z błędami i interpretacji danych. Na przykład określić, że plik danych go odczytywać jako pojedynczy wiersz, pojedynczej kolumny zestawu wierszy typu `varbinary`, `varchar`, lub `nvarchar`. Pełną składnię i opcje zobacz dokumentację SQL Server — książki Online.  
  
 Poniższy przykład wstawia zdjęcie do tabeli ProductPhoto w bazie danych AdventureWorks. Korzystając z `BULK``OPENROWSET` dostawcy, należy podać nazwana lista kolumn, nawet jeśli wartości nie są wstawianie do każdej kolumny. W takim przypadku klucz podstawowy jest zdefiniowany jako kolumny tożsamości i można pominąć na liście kolumn. Należy pamiętać, że nazwa korelacji na koniec należy również podać `OPENROWSET` instrukcji w tym przypadku jest ThumbnailPhoto. To są powiązane z kolumną w `ProductPhoto` tabeli, w której plik jest ładowany.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizowanie danych za pomocą aktualizacji. ZAPISU  
 Instrukcja Transact-SQL UPDATE ma nowej składni zapisu do modyfikowania zawartości `varchar(max)`, `nvarchar(max)`, lub `varbinary(max)` kolumn. Dzięki temu można wykonywać częściowej aktualizacji danych. Aktualizacja. Składnia jest tutaj wyświetlane w formie skróconej zapisu:  
  
 UPDATE  
  
 {  *\<obiektu >* }  
  
 ZESTAW  
  
 { *column_name* = {. ZAPIS ( *wyrażenie* , @Offset , @Length )}  
  
 Metoda WRITE Określa, że sekcja wartości *column_name* zostaną zmodyfikowane. Wyrażenie jest wartością, której zostaną skopiowane do *column_name*, `@Offset` jest punkt początkowy, w którym zostanie zapisany wyrażenie, i `@Length` argument jest długość sekcji w kolumnie.  
  
|IF|Następnie|  
|--------|----------|  
|Wyrażenie ma wartość NULL|`@Length`jest ignorowana, a wartością w *column_name* został obcięty w określonym `@Offset`.|  
|`@Offset`ma wartość NULL|Operacja aktualizacji dołącza wyrażenia na końcu istniejące *column_name* wartość i `@Length` jest ignorowana.|  
|`@Offset`jest większa niż długość wartości nazwa_kolumny|Program SQL Server zwraca błąd.|  
|`@Length`ma wartość NULL|Operacja aktualizacji powoduje usunięcie wszystkich danych z `@Offset` na końcu `column_name` wartość.|  
  
> [!NOTE]
>  Ani `@Offset` ani `@Length` może być liczbą ujemną.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie języka Transact-SQL aktualizuje wartości częściowej w DocumentSummary, `nvarchar(max)` kolumny w tabeli dokumentu w bazie danych AdventureWorks. Wyraz "składniki" zastępuje według słów "funkcji" określenie słowa zastępczego położenie początku (przesunięcie) słowa, które mają zostać zastąpione w istniejących danych i liczbę znaków do zastąpienia (długości). Przykład obejmuje instrukcji "SELECT" przed i po instrukcji UPDATE do porównywania wyników.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Praca z typami duża wartość w ADO.NET  
 Możesz pracować z typami duża wartość w ADO.NET, określając typy duża wartość jako <xref:System.Data.SqlClient.SqlParameter> obiekty w <xref:System.Data.SqlClient.SqlDataReader> do zwrócenia wyniku ustawiona, lub za pomocą <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia `DataSet` / `DataTable`. Nie ma żadnej różnicy między sposób pracy z typu duża wartość a jego typu danych powiązane, mniejszą wartość.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Używanie GetSqlBytes do pobierania danych  
 `GetSqlBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
 `GetSqlChars` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varchar(max)` lub `nvarchar(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `nvarchar(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.  
  
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
 `GetSqlBinary` Metody <xref:System.Data.SqlClient.SqlDataReader> może służyć do pobierania zawartości `varbinary(max)` kolumny. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlCommand> obiektu o nazwie `cmd` który wybiera `varbinary(max)` danych z tabeli a <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane jako <xref:System.Data.SqlTypes.SqlBinary> strumienia.  
  
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
 `GetBytes` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje strumień bajtów z przesunięciem określonej kolumny do tablicy typu byte, rozpoczynając od przesunięcia określonej tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` który pobiera bajtów do tablicy typu byte. Należy zauważyć, że w przeciwieństwie do `GetSqlBytes`, `GetBytes` wymagany rozmiar buforu tablicy.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Używanie GetValue do pobierania danych  
 `GetValue` Metody <xref:System.Data.SqlClient.SqlDataReader> odczytuje wartość od przesunięcia określona kolumna w tablicy. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` przesunięcie pobiera dane binarne z pierwszej kolumny, a następnie dane z drugiego przesunięcia kolumny ciągu.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Konwersja z typu duża wartość do typów CLR  
 Można konwertować zawartości `varchar(max)` lub `nvarchar(max)` kolumny przy użyciu dowolnej z metod konwersji ciągów, takich jak `ToString`. Poniższy fragment kodu zakłada <xref:System.Data.SqlClient.SqlDataReader> obiektu o nazwie `reader` , który pobiera dane.  
  
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
 Poniższy kod pobiera nazwę i `LargePhoto` obiekt z `ProductPhoto` w tabeli `AdventureWorks` bazy danych i zapisuje je w pliku. Musi być kompilowana przy użyciu odwołania do zestawu <xref:System.Drawing> przestrzeni nazw.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.SqlTypes.SqlBytes> obiekt ujawniający `Stream` właściwości. W kodzie użyto, to aby utworzyć nową `Bitmap` obiektu i jest zapisywany w formacie Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Za pomocą parametrów typu duża wartość  
 Duża wartość mogą być używane w <xref:System.Data.SqlClient.SqlParameter> obiektów taki sam sposób, możesz użyć wartości mniejsze typy w <xref:System.Data.SqlClient.SqlParameter> obiektów. Można pobrać typu duża wartość jako <xref:System.Data.SqlClient.SqlParameter> wartości, jak pokazano w poniższym przykładzie. Kod przyjęto założenie, że poniższej procedury przechowywane GetDocumentSummary istnieje w bazie danych AdventureWorks. Procedura składowana przyjmuje parametr wejściowy o nazwie @DocumentID i zwraca zawartość w kolumnie DocumentSummary @DocumentSummary parametru wyjściowego.  
  
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
 Tworzy kod ADO.NET <xref:System.Data.SqlClient.SqlConnection> i <xref:System.Data.SqlClient.SqlCommand> obiekty do wykonywania procedury przechowywane GetDocumentSummary i pobierania dokumentu podsumowania, które są przechowywane jako typu duża wartość. Kod przekazuje wartość @DocumentID danych wejściowych parametru i wyświetla wyniki przekazany z powrotem do @DocumentSummary dane wyjściowe parametru w oknie konsoli.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dane binarne i duża wartość serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
