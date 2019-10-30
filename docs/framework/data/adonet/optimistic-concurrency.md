---
title: Optymistyczna współbieżność
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: ddb53c9224d56803c3528d79c5ccdf5534b9ab03
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039817"
---
# <a name="optimistic-concurrency"></a>Optymistyczna współbieżność
W środowisku wielodostępnym istnieją dwa modele aktualizowania danych w bazie danych: optymistyczne współbieżność i pesymistyczne współbieżności. Obiekt <xref:System.Data.DataSet> został zaprojektowany, aby zachęcić do użycia optymistycznej współbieżności dla długotrwałych działań, takich jak dane dotyczące komunikacji zdalnej i manipulowania danymi.  
  
 Współbieżność pesymistyczna polega na zablokowaniu wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w taki sposób, który ma wpływ na bieżącego użytkownika. W modelu pesymistycznym, gdy użytkownik wykonuje akcję, która powoduje stosowanie blokady, inni użytkownicy nie mogą wykonać akcji, które mogłyby spowodować konflikt z blokadą do momentu jego zwolnienia przez właściciela. Ten model jest używany głównie w środowiskach, w których istnieje intensywna rywalizacja o dane, dzięki czemu koszt ochrony danych z blokadami jest niższy niż koszt wycofywania transakcji w przypadku wystąpienia konfliktów współbieżności.  
  
 W związku z tym w modelu współbieżności pesymistycznej użytkownik, który aktualizuje wiersz, ustanawia blokadę. Do momentu zakończenia aktualizacji przez użytkownika i zwolnienia blokady nikt inny nie będzie mógł zmienić tego wiersza. Z tego powodu Współbieżność pesymistyczna jest najlepszym zaimplementowana, gdy czasy blokowania będą krótkie, jak programowe przetwarzanie rekordów. Współbieżność pesymistyczna nie jest skalowalna, gdy użytkownicy pracują z danymi i powodują, że rekordy są blokowane przez stosunkowo długi czas.  
  
> [!NOTE]
> Jeśli musisz zaktualizować wiele wierszy w tej samej operacji, tworzenie transakcji jest bardziej skalowalne, niż przy użyciu pesymistycznego blokowania.  
  
 Z kolei użytkownicy korzystający z optymistycznej współbieżności nie blokują wiersza podczas odczytu. Gdy użytkownik chce zaktualizować wiersz, aplikacja musi określić, czy inny użytkownik zmienił wiersz od czasu odczytu. Współbieżność optymistyczna jest zwykle używana w środowiskach z niską rywalizacją dla danych. Optymistyczna współbieżność zwiększa wydajność, ponieważ nie jest wymagane blokowanie rekordów, a blokowanie rekordów wymaga dodatkowych zasobów serwera. Ponadto w celu utrzymania blokad rekordów wymagane jest trwałe połączenie z serwerem bazy danych. Ponieważ nie jest to przypadek optymistyczny model współbieżności, połączenia z serwerem są bezpłatne, aby zapewnić większą liczbę klientów w krótszym czasie.  
  
 W modelu współbieżności optymistycznej uważa się, że wystąpiło naruszenie, jeśli po odebraniu przez użytkownika wartości z bazy danych inny użytkownik zmodyfikuje wartość przed próbą zmodyfikowania jej przez pierwszego użytkownika. Jak serwer rozpoznaje naruszenie współbieżności najlepiej ilustruje poniższy przykład.  
  
 W poniższych tabelach przedstawiono przykład optymistycznej współbieżności.  
  
 O godzinie 1:00, Użytkownik1 odczytuje wiersz z bazy danych o następujących wartościach:  
  
 **CustID nazwisko imię**  
  
 101 Kowalski Roberta  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Nazwisko|Nazwisk|Nazwisk|Nazwisk|  
|Imię|Wiadomość|Wiadomość|Wiadomość|  
  
 O godzinie 1:01, 13:00 odczytuje ten sam wiersz.  
  
 O godzinie 1:03 – 13:00 zmiany **FirstName** od "Roberta" do "Robert" i aktualizuje bazę danych.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Nazwisko|Nazwisk|Nazwisk|Nazwisk|  
|Imię|Wiadomość|Robert|Wiadomość|  
  
 Aktualizacja powiedzie się, ponieważ wartości w bazie danych w czasie aktualizacji pasują do oryginalnych wartości, które mają wartość od.  
  
 O godzinie 1:05, Użytkownik1 zmieni imię "Roberta" na "Kuba" i spróbuje zaktualizować wiersz.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Nazwisko|Nazwisk|Nazwisk|Nazwisk|  
|Imię|Wiadomość|Tomasz|Robert|  
  
 W tym momencie Użytkownik1 napotyka optymistyczne naruszenie współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest już zgodna z oryginalną wartością oczekiwaną przez Użytkownik1 ("Robert"). Naruszenie współbieżności pozwala stwierdzić, że aktualizacja nie powiodła się. Należy teraz podjąć decyzję, czy zastąpić zmiany wprowadzone przez użytkownika, wprowadzając zmiany podane przez Użytkownik1, lub aby anulować zmiany przez Użytkownik1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testowanie dla optymistycznych naruszeń współbieżności  
 Istnieje kilka technik testowania dla optymistycznego naruszenia współbieżności. Jeden z nich obejmuje dołączenie kolumny timestamp do tabeli. Bazy danych często zapewniają funkcję sygnatur czasowych, która może służyć do identyfikowania daty i godziny ostatniej aktualizacji rekordu. Korzystając z tej techniki, w definicji tabeli jest dołączona kolumna sygnatur czasowych. Za każdym razem, gdy rekord zostanie zaktualizowany, sygnatura czasowa jest aktualizowana w celu odzwierciedlenia bieżącej daty i godziny. W teście dla optymistycznych naruszeń współbieżności kolumna sygnatury czasowej jest zwracana z dowolnego zapytania o zawartość tabeli. Po próbie aktualizacji wartość sygnatury czasowej w bazie danych jest porównywana z oryginalną wartością sygnatury czasowej zawartej w zmodyfikowanym wierszu. Jeśli są one zgodne, aktualizacja jest wykonywana, a kolumna sygnatury czasowej zostaje zaktualizowana o bieżący czas, aby odzwierciedlić aktualizację. Jeśli nie są zgodne, nastąpiło jednooptymistyczne naruszenie współbieżności.  
  
 Inna technika testowania dla optymistycznego naruszenia współbieżności polega na sprawdzeniu, czy wszystkie oryginalne wartości kolumn w wierszu nadal pasują do nazw znalezionych w bazie danych. Rozważmy na przykład następujące zapytanie:  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Aby sprawdzić optymistyczne naruszenie współbieżności podczas aktualizowania wiersza w tabeli **Tabela1**, należy wydać następującą instrukcję AKTUALIZUJĄCĄ:  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak długo, jak oryginalne wartości pasują do wartości w bazie danych, jest przeprowadzana aktualizacja. Jeśli wartość została zmodyfikowana, aktualizacja nie zmodyfikuje wiersza, ponieważ klauzula WHERE nie znajdzie dopasowania.  
  
 Należy zauważyć, że zaleca się zawsze zwrócenie unikatowej wartości klucza podstawowego do zapytania. W przeciwnym razie Poprzednia instrukcja UPDATE może zaktualizować więcej niż jeden wiersz, co może nie być Twoim zamiarem.  
  
 Jeśli kolumna w źródle danych dopuszcza wartości null, może być konieczne przeciągnięcie klauzuli WHERE, aby sprawdzić pasujące odwołanie o wartości null w lokalnej tabeli i w źródle danych. Na przykład następująca instrukcja UPDATE sprawdza, czy odwołanie o wartości null w wierszu lokalnym nadal pasuje do odwołania o wartości null w źródle danych lub czy wartość w wierszu lokalnym nadal pasuje do wartości w źródle danych.  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Można również zastosować mniej restrykcyjne kryteria przy użyciu optymistycznego modelu współbieżności. Na przykład użycie tylko kolumn klucza podstawowego w klauzuli WHERE powoduje zastąpienie danych bez względu na to, czy inne kolumny zostały zaktualizowane od czasu ostatniego zapytania. Można również zastosować klauzulę WHERE tylko do określonych kolumn, co spowoduje zastąpienie danych, chyba że określone pola zostały zaktualizowane od czasu ostatniego zapytania.  
  
### <a name="the-dataadapterrowupdated-event"></a>Zdarzenie DataAdapter. RowUpdated  
 Zdarzenie **RowUpdated** obiektu <xref:System.Data.Common.DataAdapter> może być używane w połączeniu z opisanymi wcześniej technikami w celu dostarczenia powiadomienia do aplikacji optymistycznych naruszeń współbieżności. **RowUpdated** występuje po każdej próbie zaktualizowania **zmodyfikowanego** wiersza z **zestawu danych**. Dzięki temu można dodać specjalny kod obsługi, w tym przetwarzanie w przypadku wystąpienia wyjątku, dodanie niestandardowych informacji o błędzie, dodanie logiki ponawiania i tak dalej. Obiekt <xref:System.Data.Common.RowUpdatedEventArgs> zwraca właściwość **RecordsAffected** zawierającą liczbę wierszy, na które miało wpływ określone polecenie Update dla zmodyfikowanego wiersza w tabeli. Ustawiając polecenie Update do testowania optymistycznej współbieżności, właściwość **RecordsAffected** będzie w efekcie zwracać wartość 0 w przypadku wystąpienia naruszenia optymistycznej współbieżności, ponieważ żadne rekordy nie zostały zaktualizowane. W takim przypadku zostanie zgłoszony wyjątek. Zdarzenie **RowUpdated** umożliwia obsługę tego wystąpienia i uniknięcie wyjątku przez ustawienie odpowiedniej wartości **RowUpdatedEventArgs. status** , takiej jak **UpdateStatus. SkipCurrentRow**. Aby uzyskać więcej informacji o zdarzeniu **RowUpdated** , zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).  
  
 Opcjonalnie można ustawić **Właściwość DataAdapter. ContinueUpdateOnError** na **wartość true**, przed wywołaniem funkcji **Update**, a następnie odpowiedzieć na informacje o błędzie przechowywane we właściwości **RowError** określonego wiersza po zakończeniu **aktualizacji** . Aby uzyskać więcej informacji, zobacz [wiersz informacje o błędzie](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Przykład optymistycznej współbieżności  
 Poniżej przedstawiono prosty przykład, który ustawia element **UpdateCommand** elementu **DataAdapter** do testowania optymistycznej współbieżności, a następnie używa zdarzenia **RowUpdated** do testowania optymistycznych naruszeń współbieżności. Po napotkaniu optymistycznego naruszenia współbieżności aplikacja ustawia **RowError** wiersza, dla którego aktualizacja została wystawiona, aby odzwierciedlał optymistyczne naruszenie współbieżności.  
  
 Należy zauważyć, że wartości parametrów przesyłane do klauzuli WHERE polecenia UPDATE są mapowane na **oryginalne** wartości odpowiednich kolumn.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](updating-data-sources-with-dataadapters.md)
- [Informacje o błędzie wiersza](./dataset-datatable-dataview/row-error-information.md)
- [Transakcje i współbieżność](transactions-and-concurrency.md)
- [Omówienie ADO.NET](ado-net-overview.md)
