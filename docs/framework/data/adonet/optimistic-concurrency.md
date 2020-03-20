---
title: Optymistyczna współbieżność
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: e8d24a3998ca97fdf45e647bc40c1f7d6018ec20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149456"
---
# <a name="optimistic-concurrency"></a>Optymistyczna współbieżność
W środowisku dla wielu administratorów istnieją dwa modele aktualizacji danych w bazie danych: optymistyczna współbieżność i współbieżność pesymistyczna. Obiekt <xref:System.Data.DataSet> ma na celu zachęcenie do korzystania z optymistycznej współbieżności dla długotrwałych działań, takich jak dane komunikacji zdalnej i interakcji z danymi.  
  
 Współbieżność pesymistyczne polega na blokowaniu wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w sposób, który wpływa na bieżącego użytkownika. W modelu pesymistycznym, gdy użytkownik wykonuje akcję, która powoduje, że blokada ma zostać zastosowana, inni użytkownicy nie mogą wykonywać akcji, które mogłyby spowodować konflikt z blokadą, dopóki właściciel blokady go nie zwolni. Ten model jest używany głównie w środowiskach, w których istnieje duże rywalizacji dla danych, tak aby koszt ochrony danych za pomocą blokad jest mniejsza niż koszt wycofywania transakcji, jeśli wystąpią konflikty współbieżności.  
  
 W związku z tym w modelu współbieżności pesymistyczne, użytkownik, który aktualizuje wiersz ustanawia blokadę. Dopóki użytkownik nie zakończy aktualizacji i nie wydał blokady, nikt inny nie może zmienić tego wiersza. Z tego powodu współbieżność pesymistyczna jest najlepiej zaimplementowana, gdy czasy blokady będą krótkie, tak jak w programowym przetwarzaniu rekordów. Współbieżność pesymistyczna nie jest skalowalną opcją, gdy użytkownicy wchodzą w interakcje z danymi i powodują, że rekordy są blokowane przez stosunkowo duże okresy czasu.  
  
> [!NOTE]
> Jeśli musisz zaktualizować wiele wierszy w tej samej operacji, tworzenie transakcji jest bardziej skalowalną opcją niż przy użyciu pesymistyczne blokowanie.  
  
 Z drugiej strony użytkownicy, którzy używają optymistycznej współbieżności nie blokują wiersza podczas jej odczytywania. Gdy użytkownik chce zaktualizować wiersz, aplikacja musi określić, czy inny użytkownik zmienił wiersz, ponieważ został przeczytany. Optymistyczna współbieżność jest zwykle używana w środowiskach o niskim rywalizacji o dane. Optymistyczna współbieżność zwiększa wydajność, ponieważ nie jest wymagane blokowanie rekordów, a blokowanie rekordów wymaga dodatkowych zasobów serwera. Ponadto w celu utrzymania blokad rekordów wymagane jest trwałe połączenie z serwerem bazy danych. Ponieważ nie jest to przypadek w modelu współbieżności optymistyczne, połączenia z serwerem mogą obsługiwać większą liczbę klientów w krótszym czasie.  
  
 W modelu współbieżności optymistyczne uważa się, że naruszenie wystąpiło, jeśli po użytkownik otrzyma wartość z bazy danych, inny użytkownik modyfikuje wartość przed pierwszym użytkownik próbował go zmodyfikować. Jak serwer rozwiązuje naruszenie współbieżności najlepiej jest pokazane przez pierwsze opisanie następującego przykładu.  
  
 W poniższych tabelach przedstawiono przykład optymistycznej współbieżności.  
  
 O godzinie 13:00 użytkownik1 odczytuje wiersz z bazy danych z następującymi wartościami:  
  
 **Nazwa pierwszej nazwy custID**  
  
 101 Kowalski Bob  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|Idklienta|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 O godzinie 13:01 użytkownik2 odczytuje ten sam wiersz.  
  
 O godzinie 13:03 użytkownik2 zmienia **imię z** "Bob" na "Robert" i aktualizuje bazę danych.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|Idklienta|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Aktualizacja powiedzie się, ponieważ wartości w bazie danych w momencie aktualizacji są zgodne z oryginalnymi wartościami, które ma Użytkownik2.  
  
 O godzinie 13:05 użytkownik1 zmienia imię "Bob" na "James" i próbuje zaktualizować wiersz.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|Idklienta|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 W tym momencie Użytkownik1 napotyka optymistyczne naruszenie współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest już zgodna z oryginalną wartością oczekiwaną przez użytkownika1 ("Bob"). Naruszenie współbieżności po prostu informuje, że aktualizacja nie powiodła się. Teraz należy podjąć decyzję, czy zastąpić zmiany dostarczone przez Użytkownika2 ze zmianami dostarczonymi przez Użytkownika1 lub anulować zmiany przez Użytkownika1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testowanie optymistycznych naruszeń współbieżności  
 Istnieje kilka technik testowania pod kątem naruszenia współbieżności optymistyczne. Jeden obejmuje dołączenie kolumny sygnatury czasowej w tabeli. Bazy danych często zapewniają funkcje sygnatury czasowej, które mogą służyć do identyfikowania daty i godziny ostatniej aktualizacji rekordu. Przy użyciu tej techniki kolumna sygnatury czasowej znajduje się w definicji tabeli. Za każdym razem, gdy rekord jest aktualizowany, sygnatura czasowa jest aktualizowana w celu odzwierciedlenia bieżącej daty i godziny. W teście dla optymistycznych naruszeń współbieżności kolumna sygnatura czasowa jest zwracana z dowolną kwerendą zawartości tabeli. Podczas próby aktualizacji wartość sygnatury czasowej w bazie danych jest porównywana z oryginalną wartością sygnatury czasowej zawartą w zmodyfikowanym wierszu. Jeśli są zgodne, aktualizacja jest wykonywana, a kolumna sygnatury czasowej jest aktualizowana o bieżący czas, aby odzwierciedlić aktualizację. Jeśli nie są one zgodne, wystąpiło naruszenie współbieżności optymistyczne.  
  
 Inną techniką testowania pod kątem naruszenia współbieżności optymistyczne jest sprawdzenie, czy wszystkie oryginalne wartości kolumn w wierszu nadal odpowiadają wartościom znalezionym w bazie danych. Rozważmy na przykład następujące zapytanie:  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Aby przetestować pod kątem naruszenia optymistycznej współbieżności podczas aktualizowania wiersza w **tabeli 1,** należy wydać następującą instrukcję UPDATE:  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak długo, jak oryginalne wartości są zgodne z wartościami w bazie danych, aktualizacja jest wykonywana. Jeśli wartość została zmodyfikowana, aktualizacja nie zmodyfikuje wiersza, ponieważ klauzula WHERE nie znajdzie dopasowania.  
  
 Należy zauważyć, że zaleca się zawsze zwracać unikatową wartość klucza podstawowego w kwerendzie. W przeciwnym razie poprzednia instrukcja UPDATE może zaktualizować więcej niż jeden wiersz, który może nie być twoim zamiarem.  
  
 Jeśli kolumna w źródle danych zezwala na wartości null, może być konieczne rozszerzenie klauzuli WHERE, aby sprawdzić, czy w tabeli lokalnej i w źródle danych nie ma odpowiedniego odwołania do wartości null. Na przykład następująca instrukcja UPDATE sprawdza, czy odwołanie null w wierszu lokalnym nadal pasuje do odwołania null w źródle danych lub że wartość w wierszu lokalnym nadal pasuje do wartości w źródle danych.  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Można również zastosować mniej restrykcyjne kryteria podczas korzystania z modelu współbieżności optymistyczne. Na przykład użycie tylko kolumn klucza podstawowego w klauzuli WHERE powoduje, że dane mają zostać zastąpione niezależnie od tego, czy inne kolumny zostały zaktualizowane od ostatniej kwerendy. Można również zastosować klauzulę WHERE tylko do określonych kolumn, co powoduje zastępowanie danych, chyba że określone pola zostały zaktualizowane od czasu ostatniego zapytania.  
  
### <a name="the-dataadapterrowupdated-event"></a>Zdarzenie DataAdapter.RowUpdated  
 **Zdarzenie RowUpdated** <xref:System.Data.Common.DataAdapter> obiektu może służyć w połączeniu z technik opisanych wcześniej, aby zapewnić powiadomienie do aplikacji optymistyczne naruszenia współbieżności. **RowUpdated** występuje po każdej próbie aktualizacji **zmodyfikowanego** wiersza z **zestawu danych**. Dzięki temu można dodać specjalny kod obsługi, w tym przetwarzania, gdy wystąpi wyjątek, dodawanie informacji o błędzie niestandardowe, dodawanie logiki ponawiania i tak dalej. Obiekt <xref:System.Data.Common.RowUpdatedEventArgs> zwraca właściwość **RecordsAffected** zawierającą liczbę wierszy, których dotyczy określone polecenie aktualizacji dla zmodyfikowanego wiersza w tabeli. Ustawiając polecenie aktualizacji, aby przetestować optymistyczną współbieżność, **RecordsAffected** właściwość zwróci wartość 0, gdy wystąpiło naruszenie współbieżności optymistyczne, ponieważ nie zostały zaktualizowane żadne rekordy. W takim przypadku zostanie zgłoszony wyjątek. **Zdarzenie RowUpdated** umożliwia obsługę tego wystąpienia i uniknięcie wyjątku, ustawiając odpowiednią wartość **RowUpdatedEventArgs.Status,** taką jak **UpdateStatus.SkipCurrentRow**. Aby uzyskać więcej informacji na temat **zdarzenia RowUpdated,** zobacz [Obsługa zdarzeń dataadapter](handling-dataadapter-events.md).  
  
 Opcjonalnie można ustawić **DataAdapter.ContinueUpdateOnError** na **true**, przed wywołaniem **Update**i odpowiedzieć na informacje o błędzie przechowywane we właściwości **RowError** określonego wiersza po zakończeniu **aktualizacji.** Aby uzyskać więcej informacji, zobacz [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Przykład optymistycznej współbieżności  
 Poniżej przedstawiono prosty przykład, który ustawia **UpdateCommand** **dataAdapter** do testowania optymistycznej współbieżności, a następnie używa **RowUpdated** zdarzenia do testowania optymistycznych naruszeń współbieżności. Po napotkaniu naruszenia współbieżności optymistyczne, aplikacja ustawia **RowError** wiersza, dla których aktualizacja została wystawiona w celu odzwierciedlenia naruszenia współbieżności optymistyczne.  
  
 Należy zauważyć, że wartości parametrów przekazanych do klauzuli WHERE polecenia UPDATE są mapowane na **oryginalne** wartości ich odpowiednich kolumn.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)
- [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
