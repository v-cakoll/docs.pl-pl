---
title: Optymistyczna współbieżność
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: f2fc69867ae1659a342161b00dfd91852441fa5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126220"
---
# <a name="optimistic-concurrency"></a>Optymistyczna współbieżność
W środowisku wielodostępnym, istnieją dwa modele aktualizacji danych w bazie danych: optymistycznej współbieżności i pesymistycznej współbieżności. <xref:System.Data.DataSet> Obiektu jest przeznaczona do zachęcać do stosowania funkcji optymistycznej współbieżności dla długotrwałych działań, takich jak dane usług zdalnych i wchodzenie w interakcje z danymi.  
  
 Współbieżność pesymistyczna polega na blokowanie wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w sposób, który ma wpływ na bieżącego użytkownika. Pesymistyczne modelu gdy użytkownik wykona akcję, która powoduje, że blokady do zastosowania, inni użytkownicy nie można wykonać akcje, które spowodowałoby to konflikt z blokadą do momentu właściciel blokady zwalnia go. Ten model jest używany głównie w środowiskach, w której jest mocno rywalizacji o danych, tak, aby koszty ochrony danych przy użyciu blokady jest mniejsza niż koszt wycofywanie transakcji, jeśli występują konflikty współbieżności.  
  
 W związku z tym w modelu pesymistycznej współbieżności, użytkownik, który aktualizuje wiersz ustanawia blokadę. Dopóki użytkownik nie ma Zakończono aktualizację i ogólnie blokady, nikt inny nie można zmienić tego wiersza. Współbieżność pesymistyczna z tego powodu najlepiej jest implementowane, gdy czasy blokady będą krótki, tak jak programowe przetwarzania rekordów. Współbieżność pesymistyczna nie jest to skalowalne rozwiązanie, gdy użytkownicy są wchodzenie w interakcje z danymi i powodują, że rekordy zostanie zablokowane przez stosunkowo dużej ilości okresy.  
  
> [!NOTE]
>  Jeśli trzeba zaktualizować wiele wierszy w tej samej operacji, następnie utworzenie transakcji jest bardziej skalowalna opcji niż przy użyciu pesymistycznego blokowania.  
  
 Z drugiej strony Użytkownicy, którzy używaj optymistycznej współbieżności nie Blokuj wiersz podczas jej odczytywania. Gdy użytkownik chce, aby zaktualizować wiersza, aplikacji należy określić, czy inny użytkownik zmienił wiersza, ponieważ została ona odczytana. Optymistyczna współbieżność jest zazwyczaj używane w środowiskach z niskim rywalizacji o zasoby danych. Optymistyczna współbieżność zwiększa wydajność, ponieważ wymagana jest nie blokowania rekordów i blokowanie rekordów wymaga dodatkowych zasobów serwera. Ponadto w celu utrzymania blokady rekordu, trwałe połączenie z serwerem bazy danych jest wymagana. Ponieważ nie jest w przypadku modelu optymistycznej współbieżności, połączenia z serwerem są bezpłatne do obsługi większej liczby klientów w krótszym czasie.  
  
 W modelu optymistycznej współbieżności naruszenie uznaje się miała miejsce, jeśli po użytkownik otrzymuje wartość z bazy danych, inny użytkownik modyfikuje wartość, zanim pierwszy użytkownik próbował go zmodyfikować. Jak serwer rozpoznaje Naruszenie współbieżności najlepiej jest wyświetlany przy pierwszym opisujące w poniższym przykładzie.  
  
 Poniższe tabele postępuj zgodnie z przykładem optymistycznej współbieżności.  
  
 O 1:00 Użytkownik1 odczytuje wiersz z bazy danych z następującymi wartościami:  
  
 **CustID nazwisko imię**  
  
 101 Bob Smith  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Nowak|Nowak|Nowak|  
|FirstName|Bob|Bob|Bob|  
  
 1 o godzinie: 01 Użytkownik2 odczytuje w tym samym wierszu.  
  
 1 o godzinie: 03, zmienia się Użytkownik2 **FirstName** z "Bob" do "Robert" i aktualizuje bazę danych.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Nowak|Nowak|Nowak|  
|FirstName|Bob|Robert|Bob|  
  
 Aktualizacja zakończy się pomyślnie, ponieważ oryginalne wartości, które ma Użytkownik2 pasuje do wartości w bazie danych w czasie aktualizacji.  
  
 1 o godzinie: 05 Użytkownik1 zmiany "Bob" imię "James" i podejmuje próbę zaktualizowania wiersza w tabeli.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Nowak|Nowak|Nowak|  
|FirstName|Bob|James|Robert|  
  
 W tym momencie użytkownik User1 napotyka naruszenie optymistycznej współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest zgodna z oryginalnej wartości, że użytkownik User1 oczekiwała ("Bob"). Naruszenie współbieżności po prostu informuje o tym, że aktualizacja nie powiodła się. Teraz decyzja należy zastąpić zmiany dostarczonych przez Użytkownik2 ze zmianami, dostarczone przez użytkownika Użytkownik1 lub Anuluj zmiany przy użyciu konta użytkownik1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testowanie pod kątem naruszeń optymistycznej współbieżności  
 Istnieje kilka technik testowania dla naruszenia optymistycznej współbieżności. Jeden polega na tym kolumnę sygnatur czasowych w tabeli. Bazy danych zwykle zapewniają funkcje sygnatury czasowej, który może służyć do identyfikowania Data i godzina, kiedy rekord był ostatnio aktualizowany. Ta technika kolumnę sygnatur czasowych znajduje się w definicji tabeli. Zawsze wtedy, gdy rekord zostanie zaktualizowany, sygnatura czasowa jest aktualizowana w celu odzwierciedlenia bieżącej daty i godziny. W teście naruszeń optymistycznej współbieżności kolumnę sygnatur czasowych, jest zwracany za pomocą dowolnego zapytania zawartość tabeli. Próba aktualizacji wartości sygnatur czasowych w bazie danych jest porównywany oryginalna wartość sygnatury czasowej znajdujących się w wierszu zmodyfikowane. Jeśli są zgodne, wykonywania aktualizacji, a kolumny sygnatur czasowych zostanie zaktualizowany bieżący czas w celu uwzględnienia aktualizacji. Jeśli nie są zgodne, wystąpiło naruszenie optymistycznej współbieżności.  
  
 Inna technika testowanie pod kątem naruszenie optymistycznej współbieżności jest Sprawdź, czy wszystkie oryginalne wartości kolumn w wierszu nadal odpowiadają tych dostępnych w bazie danych. Na przykład należy wziąć pod uwagę następujące zapytanie:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Do testowania naruszenie optymistycznej współbieżności podczas aktualizowania wiersza w **Tabela1**, czy wystawiać następującą instrukcję aktualizacji:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak długo, jak oryginalne wartości odpowiadają wartościom w bazie danych, aktualizacja jest wykonywana. W przypadku modyfikowania wartość aktualizacji nie będą modyfikować wiersza, ponieważ klauzula WHERE nie znajdzie dopasowania.  
  
 Należy pamiętać, że zalecane jest zawsze zwracać unikatowe wartości klucza podstawowego w zapytaniu. W przeciwnym razie poprzednich instrukcji UPDATE może być aktualizowana więcej niż jeden wiersz, który może nie być zgodne z zamiarami użytkownika.  
  
 Kolumny w źródle danych dopuszcza wartości null, może być konieczne rozszerzenie usługi klauzuli WHERE, aby wyszukać pasujące odwołanie o wartości null w Twojej lokalnej tabeli, a w źródle danych. Na przykład następującą instrukcję aktualizacji sprawdza, czy odwołanie o wartości null w wierszu lokalne nadal odpowiada odwołanie o wartości null w źródle danych, lub że wartość w lokalnych wierszu nadal odpowiada wartości w źródle danych.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Można również zastosować mniej restrykcyjne uprawnienia kryteria, korzystając z modelu optymistycznej współbieżności. Na przykład za pomocą tylko kolumny klucza podstawowego w klauzuli WHERE powoduje, że dane zostaną zastąpione, niezależnie od tego, czy inne kolumny zostały zaktualizowane od czasu ostatniego zapytania. Klauzula WHERE można również zastosować tylko do określonych kolumn skutkuje danych zostaną zastąpione, chyba że niektóre pola zostały zaktualizowane od czasu ostatniego wykonano.  
  
### <a name="the-dataadapterrowupdated-event"></a>Zdarzenie DataAdapter.RowUpdated  
 **RowUpdated** zdarzenia <xref:System.Data.Common.DataAdapter> obiekt może być używany w połączeniu z technik opisanych wcześniej, aby powiadomienie do aplikacji naruszeń optymistycznej współbieżności. **RowUpdated** występuje po każdej próby zaktualizowania **zmodyfikowane** wiersz z tabeli **zestawu danych**. Dzięki temu można dodać kodu specjalnej obsługi, w tym przetwarzanie, gdy wystąpi wyjątek, dodawania niestandardowej informacji o błędzie, dodanie logiki ponawiania prób i tak dalej. <xref:System.Data.Common.RowUpdatedEventArgs> Zwraca obiekt **RecordsAffected** Właściwość zawierająca liczby wierszy na polecenie określonej aktualizacji dla zmodyfikowanych wierszy w tabeli. Ustawiając polecenia update do testowania optymistycznej współbieżności **RecordsAffected** właściwości co w efekcie zwróci wartość 0, jeśli nastąpiło naruszenie zasad optymistycznej współbieżności, ponieważ żadne rekordy nie zostały zaktualizowane. Jeśli jest to możliwe, jest zgłaszany wyjątek. **RowUpdated** zdarzenie pozwala na obsługę tego wystąpienia i uniknąć wyjątek, ustawiając odpowiednią **RowUpdatedEventArgs.Status** wartości, takich jak  **UpdateStatus.SkipCurrentRow**. Aby uzyskać więcej informacji na temat **RowUpdated** zdarzeń, zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 Opcjonalnie możesz ustawić **DataAdapter.ContinueUpdateOnError** do **true**, przed wywołaniem **aktualizacji**i reagować na informacje o błędzie, przechowywane w **RowError** właściwości określonego wiersza, kiedy **aktualizacji** zostało zakończone. Aby uzyskać więcej informacji, zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Przykład optymistycznej współbieżności  
 Poniżej przedstawiono prosty przykład, który ustawia **elementu UpdateCommand** z **DataAdapter** do testowania optymistycznej współbieżności, a następnie używa **RowUpdated** zdarzeń do testowania naruszenia optymistycznej współbieżności. W przypadku naruszenia optymistycznej współbieżności, aplikacja ustawia **RowError** wiersza, który aktualizacji został wystawiony dla, aby odzwierciedlić naruszenie optymistycznej współbieżności.  
  
 Należy zauważyć, że wartości parametrów przekazanych do klauzuli WHERE polecenia UPDATE są mapowane na **oryginalnego** wartościami odpowiednimi kolumnami.  
  
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

- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)
- [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
