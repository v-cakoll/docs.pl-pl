---
title: "Optymistycznej współbieżności"
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
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 45939dcec8b8db8e1b06ebfc67d89bfead67575a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimistic-concurrency"></a>Optymistycznej współbieżności
W środowisku wielodostępnym są dwa modele aktualizacji danych w bazie danych: optymistycznej współbieżności i pesymistyczne współbieżności. <xref:System.Data.DataSet> Obiektu zaprojektowano w celu wspierać stosowanie optymistycznej współbieżności długotrwałe działań, np. danych zdalnych i interakcji z danymi.  
  
 Pesymistyczne współbieżności obejmuje blokowania wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w taki sposób, który ma wpływ na bieżącego użytkownika. Pesymistyczne modelu gdy użytkownik wykona akcję wywołującą blokady do zastosowania, inni użytkownicy nie można wykonać akcje, które spowodowałoby to konflikt z blokadą do momentu zwolnieniem właściciel blokady. Ten model jest używane głównie w środowiskach, w której jest mocno rywalizacji o danych, dzięki czemu koszty ochrony danych przy użyciu blokady jest mniejsza niż koszt wycofywanie transakcji, jeśli występują konflikty współbieżności.  
  
 W związku z tym modelem współbieżności pesymistyczne użytkownika, który aktualizuje wiersz ustanawia blokady. Dopóki użytkownik nie ma Zakończono aktualizację i zwolnione blokady, nikt można zmienić tego wiersza. Pesymistyczne współbieżności z tego powodu najlepiej jest implementowane, gdy blokady razy będzie krótkie, jak programowe przetwarzania rekordów. Pesymistyczne współbieżności nie jest opcją skalowalne, gdy użytkownicy są interakcji z danymi i powoduje rekordów do zablokowania dla stosunkowo dużej okresów.  
  
> [!NOTE]
>  Jeśli trzeba zaktualizować wiele wierszy w tej samej operacji, następnie utworzenie transakcji to opcja większą skalowalność niż przy użyciu pesymistyczne blokowanie.  
  
 Z kolei użytkowników, którzy korzystają optymistycznej współbieżności nie Blokuj wiersz podczas jej odczytywania. Gdy użytkownik chce, aby zaktualizować wiersza, aplikacja musi ustalić, czy inny użytkownik zmienił wiersza od czasu odczytu. Optymistycznej współbieżności jest zwykle używany w środowiskach o niskim rywalizacji danych. Optymistycznej współbieżności zwiększa wydajność, ponieważ nie blokowanie rekordów jest wymagane, i blokowanie rekordów wymaga dodatkowych zasobów serwera. Ponadto w celu utrzymania blokady rekordu, trwałe połączenie z serwerem bazy danych jest wymagane. Ponieważ nie jest to w przypadku modelu optymistycznej współbieżności, połączenia z serwerem mogą obsługiwać większą liczbę klientów w krótszym czasie.  
  
 W modelu optymistycznej współbieżności naruszenie jest uważana za miały miejsce w przypadku, gdy użytkownik otrzyma wartość z bazy danych, inny użytkownik modyfikuje wartość przed pierwszy użytkownik próbował go zmodyfikować. Jak serwer rozpoznaje Naruszenie współbieżności najlepiej jest wyświetlany przez pierwszego opisującym w poniższym przykładzie.  
  
 Poniższe tabele postępuj zgodnie z przykładem optymistycznej współbieżności.  
  
 O godzinie 13:00 Użytkownik1 odczytuje wiersz z bazy danych z następującymi wartościami:  
  
 **IDKlienta nazwisko imię**  
  
 Robert Smith 101  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|IDKlienta|101|101|101|  
|Nazwisko|Smith|Smith|Smith|  
|Imię|Robert|Robert|Robert|  
  
 O godzinie 13:01 Użytkownik2 odczytuje tego samego wiersza.  
  
 O godzinie 13:03, zmiany Użytkownik2 **imię** z "Bob" do "Robert" i aktualizuje bazę danych.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|IDKlienta|101|101|101|  
|Nazwisko|Smith|Smith|Smith|  
|Imię|Robert|Robert|Robert|  
  
 Aktualizacja powiedzie się, ponieważ oryginalne wartości, które ma Użytkownik2 pasuje do wartości w bazie danych w momencie aktualizacji.  
  
 O godzinie 13:05 Użytkownik1 zmiany "Bob" imię "Kuba" i podejmuje próbę zaktualizowania wiersza w tabeli.  
  
|Nazwa kolumny|Oryginalna wartość|Bieżąca wartość|Wartość w bazie danych|  
|-----------------|--------------------|-------------------|-----------------------|  
|IDKlienta|101|101|101|  
|Nazwisko|Smith|Smith|Smith|  
|Imię|Robert|Kuba|Robert|  
  
 W tym momencie Użytkownik1 napotka naruszenie optymistycznej współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest już zgodny oryginalnej wartości, że Użytkownik1 oczekiwała ("Bob"). Naruszenie współbieżności umożliwia po prostu wiedzieć, że aktualizacja nie powiodła się. Teraz decyzji musi można zastąpić zmiany dostarczonych przez Użytkownik2 ze zmianami dostarczone przez użytkownika Użytkownik1 lub Anuluj zmiany wprowadzone przez użytkownika Użytkownik1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testowanie pod kątem naruszeń optymistycznej współbieżności  
 Istnieje kilka technik testowania dla naruszenia optymistycznej współbieżności. Jeden polega na tym kolumny znaczników czasu w tabeli. Bazy danych często udostępniają funkcje sygnatury czasowej, który może służyć do identyfikowania datę i godzinę ostatniej aktualizacji rekordu. Ta technika kolumny znaczników czasu znajduje się w definicji tabeli. Przy każdej aktualizacji rekordu sygnatury czasowej jest aktualizowany w celu odzwierciedlenia bieżącej daty i godziny. W teście naruszeń optymistycznej współbieżności kolumny znaczników czasu jest zwracany za każde zapytanie zawartość tej tabeli. Próba aktualizacji wartości znaczników czasu w bazie danych jest porównywany oryginalna wartość sygnatury czasowej w zmodyfikowanych wierszy. Jeśli są zgodne, aktualizacja jest wykonywana, a kolumny znaczników czasu jest aktualizowany przy użyciu bieżącego czasu w celu uwzględnienia tej aktualizacji. Jeśli nie są zgodne, ma nastąpiło naruszenie zasad optymistycznej współbieżności.  
  
 Sprawdź, czy wszystkie oryginalnej wartości kolumn w wierszu nadal odpowiadają występujące w bazie danych jest innej techniki testowania dla naruszenia optymistycznej współbieżności. Na przykład wziąć pod uwagę następujące zapytanie:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Do testowania naruszenia optymistycznej współbieżności podczas aktualizowania wiersza w **Table1**, czy wystawiać następującą instrukcję aktualizacji:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak długo, jak oryginalne wartości są takie same wartości w bazie danych, aktualizacja jest wykonywana. W przypadku modyfikacji wartości aktualizacji nie spowoduje zmiany wiersza, ponieważ klauzula WHERE nie będzie zawierał dopasowania.  
  
 Należy pamiętać, że zalecane jest zawsze zwracać unikatowe wartości klucza podstawowego w zapytaniu. W przeciwnym razie powyższych instrukcji UPDATE mogą aktualizować więcej niż jeden wiersz, która nie może być Twoich zamiarów.  
  
 Kolumny w źródle danych dopuszcza wartości null, może być konieczne rozszerzenie z klauzuli WHERE, która Wyszukaj pasujące odwołanie o wartości null w tabeli lokalnej i w źródle danych. Na przykład następująca instrukcja aktualizacji sprawdza, czy odwołanie o wartości null w wierszu lokalnego nadal odpowiada odwołanie o wartości null w źródle danych, lub że wartość w lokalnych wierszu nadal jest zgodna z wartością w źródle danych.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Można również zastosować mniej restrykcyjne kryteria, korzystając z modelu optymistycznej współbieżności. Na przykład za pomocą tylko kolumny klucza podstawowego w klauzuli WHERE powoduje, że dane zostaną zastąpione niezależnie od tego, czy inne kolumny zostały zaktualizowane od czasu ostatniej kwerendy. Klauzuli WHERE można również zastosować tylko do określonych kolumn, dane zostaną zastąpione, chyba że niektóre pola zostały zaktualizowane od czasu ostatniego skierowano.  
  
### <a name="the-dataadapterrowupdated-event"></a>Zdarzenie DataAdapter.RowUpdated  
 **RowUpdated** zdarzenie <xref:System.Data.Common.DataAdapter> obiektu można użyć w połączeniu z techniki opisane wcześniej, aby zapewnić powiadomienia do aplikacji naruszeń optymistycznej współbieżności. **RowUpdated** występuje po każdej próby zaktualizowania **zmodyfikowane** wiersz z tabeli **zestawu danych**. Dzięki temu można dodać kod specjalnej obsługi, w tym przetwarzania po wystąpieniu wyjątku, dodawanie informacji o niestandardowych komunikatów o błędach, Dodawanie logiki ponawiania próby i tak dalej. <xref:System.Data.Common.RowUpdatedEventArgs> Zwraca obiekt **RecordsAffected** właściwości zawierające liczbę wierszy objętych polecenia aktualizacji określonej dla zmodyfikowanych wierszy w tabeli. Przez ustawienie polecenia Aktualizuj w celu zbadania optymistycznej współbieżności **RecordsAffected** właściwości w związku z tym zwróci wartość 0, jeśli nastąpiło naruszenie optymistycznej współbieżności, ponieważ żadne rekordy nie zostały zaktualizowane. Jeśli jest to możliwe, jest zwracany wyjątek. **RowUpdated** zdarzenie pozwala obsługiwać to wystąpienie i uniknąć wyjątek, ustawiając odpowiednią **RowUpdatedEventArgs.Status** wartości, takich jak  **UpdateStatus.SkipCurrentRow**. Aby uzyskać więcej informacji na temat **RowUpdated** zdarzeń, zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 Opcjonalnie można ustawić **DataAdapter.ContinueUpdateOnError** do **true**, przed wywołaniem **aktualizacji**i reagowanie na informacje o błędzie, przechowywane w **RowError** właściwości określonego wiersza, kiedy **aktualizacji** zostało zakończone. Aby uzyskać więcej informacji, zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Przykład optymistycznej współbieżności  
 Poniżej przedstawiono prosty przykład, który ustawia **UpdateCommand** z **element DataAdapter** do testowania optymistycznej współbieżności, a następnie używa **RowUpdated** zdarzeń do testowania naruszeń optymistycznej współbieżności. W przypadku naruszenia optymistycznej współbieżności aplikacji ustawia **RowError** wiersza, aby odzwierciedlić naruszenia optymistycznej współbieżności wystawiony dla aktualizacji.  
  
 Należy pamiętać, że wartości parametrów przekazane do klauzuli WHERE polecenia aktualizacji są mapowane na **oryginalnego** wartości odpowiednich kolumnach.  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
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
 [Trwa pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Aktualizowanie źródła danych za pomocą obiektów DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
