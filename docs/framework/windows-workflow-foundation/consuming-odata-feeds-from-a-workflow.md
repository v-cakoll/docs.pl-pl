---
title: Wykorzystywanie OData źródeł danych z przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: 9db52f734cbb9676f37c5d7a5a800b1d1efa7fbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Wykorzystywanie OData źródeł danych z przepływu pracy
Usługi danych WCF jest składnikiem [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do ujawnia i konsumowania danych za pośrednictwem sieci Web lub intranet przy użyciu semantyki representational stanu transfer (REST). OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikator URI. Wszelkie aplikacje mogą współdziałać z usługi OData na podstawie danych jeśli umożliwia wysyłanie żądania HTTP i przetworzyć źródła strumieniowego OData zwracanych usługi danych. Usługi danych WCF zawiera ponadto biblioteki klienta, które zapewniają bardziej rozbudowane środowisko programowania po używać źródła danych OData z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji. Ten temat zawiera omówienie używania OData podawania w przepływie pracy z użyciem biblioteki klienta i bez.  
  
## <a name="using-the-sample-northwind-odata-service"></a>Przy użyciu usługi Northwind OData próbki  
 Przykłady w tym temacie Użyj przykładu w lokalizacji usługi danych Northwind [ http://services.odata.org/Northwind/Northwind.svc/ ](http://go.microsoft.com/fwlink/?LinkID=187426). Usługa jest dostępna w ramach [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185248) i umożliwia dostęp tylko do odczytu do przykładowej bazy danych Northwind. Jeśli dostęp do zapisu, lub w razie potrzeby lokalnej usługi danych WCF można postępuj zgodnie z krokami [szybkiego startu usługi danych WCF](http://go.microsoft.com/fwlink/?LinkID=131076) utworzyć lokalną usługą OData, która zapewnia dostęp do bazy danych Northwind. Po wykonaniu procedury szybkiego startu, Zastąp lokalny identyfikator URI dla podanej w przykładowym kodzie w tym temacie.  
  
## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Wykorzystywanie źródła strumieniowego OData przy użyciu bibliotek klienta  
 Usługi danych WCF obejmuje bibliotek klienta, które umożliwiają łatwiej wykorzystać OData źródła danych z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] i aplikacje klienckie. Te biblioteki upraszczają wysyłanie i odbieranie wiadomości HTTP. Tłumaczenie one również ładunek komunikatu do obiektów CLR, które reprezentują danych jednostki. Dwa podstawowe klasy funkcji bibliotek klienckich <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Te klasy umożliwiają zapytania usługi danych, a następnie pracować z danymi zwróconą jednostkę jako obiekty CLR. W tej sekcji omówiono dwa podejścia do tworzenia działań korzystających z bibliotek klienta.  
  
### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Dodawanie odwołania do usługi do usługi danych WCF  
 Aby wygenerować Northwind bibliotek klienta, można użyć **Dodaj odwołanie do usługi** okno dialogowe w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] można dodać odwołania do usługi Northwind OData.  
  
 ![Dodaj odwołanie do usługi](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")  
  
 Należy pamiętać, że nie ma żadnych operacji usługi udostępniane przez usługę, a następnie w **usług** listy są elementy reprezentujące jednostek udostępnianych przez usługę danych Northwind. Dodanie odwołania do usługi klasy zostanie wygenerowany dla tych obiektów i ich użyciem w kodzie klienta. Przykłady w tym temacie używać tych klas i `NorthwindEntities` klasy do wykonania zapytania.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz [generowania biblioteki klienta usługi danych (usługi danych WCF)](http://go.microsoft.com/fwlink/?LinkID=191611).  
  
### <a name="using-asynchronous-methods"></a>Używanie metod asynchronicznych  
 Do rozwiązywania problemów możliwe opóźnienia, które mogą wystąpić podczas uzyskiwania dostępu do zasobów za pośrednictwem sieci Web, zaleca się asynchronicznie podczas uzyskiwania dostępu do usługi danych WCF. Biblioteki klienta usługi danych WCF obejmują metod asynchronicznych do wywoływania zapytania, a także Windows Workflow Foundation (WF) <xref:System.Activities.AsyncCodeActivity> klasa do tworzenia działań asynchronicznego. <xref:System.Activities.AsyncCodeActivity> mogą być zapisywane pochodzące od działania, aby móc korzystać z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] klas, metod asynchronicznych lub kod wykonany asynchronicznie mogą być wprowadzane do metody i wywoływane przy użyciu delegata. Ta sekcja zawiera dwa przykłady <xref:System.Activities.AsyncCodeActivity> pochodnej działanie; który korzysta z biblioteki klienta usługi danych WCF metod asynchronicznych i korzystającą delegata.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych (usługi danych WCF)](http://go.microsoft.com/fwlink/?LinkId=193396) i [tworzenia działań asynchroniczne](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
### <a name="using-client-library-asynchronous-methods"></a>Używanie metod asynchronicznych biblioteki klienta  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa udostępnia <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> i <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody asynchronicznie podczas badania usługi OData. Te metody mogą być wywoływane z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastąpień o <xref:System.Activities.AsyncCodeActivity> klasy. Gdy <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zwraca zastąpienie, przepływ pracy można go bezczynności (ale nie będą się powtarzać), a po zakończeniu pracy asynchroniczne <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jest wywołana w czasie wykonywania.  
  
 W poniższym przykładzie `OrdersByCustomer` działania jest zdefiniowany, że ma dwa wejściowych argumentów. `CustomerId` Argument reprezentuje klienta, który identyfikuje zamówienia przywrócić, i `ServiceUri` argument reprezentuje identyfikator URI usługi OData można wykonać zapytania. Ponieważ działania jest pochodną `AsyncCodeActivity<IEnumerable<Order>>` dostępna jest również <xref:System.Activities.Activity%601.Result%2A> output argumentu, który służy do zwracania wyników zapytania. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Zastąpienie tworzy zapytania LINQ, który wybiera wszystkie zamówienia określonego klienta. To zapytanie jest określony jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> z przekazany <xref:System.Activities.AsyncCodeActivityContext>, a następnie kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda jest wywoływana. Należy pamiętać, że wywołania zwrotnego i stanu, które są przekazywane do kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> są tymi, które zostały przekazane do działania <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metody. Zapytanie zakończył podczas wykonywania działania <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> wywołania metody. Zapytania są pobierane z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda jest wywoływana. Ta metoda zwraca <xref:System.Collections.Generic.IEnumerable%601> określonego typu jednostek; w takim przypadku `Order`. Ponieważ `IEnumerable<Order>` jest ogólny typ <xref:System.Activities.AsyncCodeActivity%601>, to `IEnumerable` jest ustawiony jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> działania.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]  
  
 W poniższym przykładzie `OrdersByCustomer` działanie pobiera listę zleceń, dla określonego klienta, a następnie <xref:System.Activities.Statements.ForEach%601> działanie wylicza zwrócony zleceń i zapisuje Data zamówienia do konsoli.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]  
  
 Po wywołaniu tego przepływu pracy następujące dane są zapisywane do konsoli:  
  
 **Wywołanie usługi danych WCF...**  
**8/25/1997**   
**10/3/1997**   
**10/13/1997**   
**1/15/1998**   
**3/16/1998**   
**4/9/1998**    
> [!NOTE]
>  Jeśli nie można nawiązać połączenia z serwerem OData, możesz uzyskać wyjątek podobny do następującego wyjątku:  
>   
>  Nieobsługiwany wyjątek: System.InvalidOperationException: Wystąpił błąd podczas przetwarzania tego żądania. ---> System.Net.WebException: nie można nawiązać połączenia z serwerem zdalnym---> System.Net.Sockets.SocketException: próba połączenia nie powiodła się, ponieważ strona połączenia nie odpowiedziała poprawnie po okresie czasu lub ustanowić połączenia nie powiodła się. ponieważ połączony host nie odpowiada.  
  
 Jeśli wymagana jest dowolnego dodatkowego przetwarzania danych zwróconych przez zapytanie, może odbywać w działaniu <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> zastąpienia. Zarówno <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> są wywoływane przy użyciu wątku przepływu pracy i kod w te zastąpienia nie jest uruchamiane asynchronicznie. Jeśli dodatkowego przetwarzania jest obszernych lub długotrwałe lub wyników zapytania, należy rozważyć podejście omówiona w następnej sekcji, używa delegata w celu wykonania zapytania i wykonywać dodatkowe przetwarzanie asynchronicznie.  
  
### <a name="using-a-delegate"></a>Przy użyciu delegata  
 Oprócz asynchroniczne wywołanie metody z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] klasy <xref:System.Activities.AsyncCodeActivity>— oparte na działania można również zdefiniować asynchroniczne logiki w jednej z metod. Ta metoda jest określana za pomocą delegata w działaniu <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zastąpienia. Gdy metoda zwróci wartość, środowisko uruchomieniowe wywołuje aktywność <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastąpienia. Podczas wywoływania usługi OData z przepływu pracy, ta metoda może służyć do wysłać zapytania do usługi i Podaj wszelkie dodatkowe przetwarzanie.  
  
 W poniższym przykładzie `ListCustomers` zdefiniowano działania. To działanie wysyła zapytanie do usługi danych Northwind próbki i zwraca `List<Customer>` zawierający wszystkich klientów w bazie danych Northwind. Asynchroniczne zadanie jest wykonywane przez `GetCustomers` metody. Ta metoda korzysta z usługi dla wszystkich klientów, a następnie kopiuje je do `List<Customer>`. Następnie sprawdza, czy wyniki są stronicowanej. Jeśli tak, wysyła zapytanie do usługi dla następnej strony wyników, dodaje je do listy, a będzie wykonywany do momentu pobraniu wszystkich danych klienta.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat stronicowania w usługi danych WCF Zobacz. [Porady: obciążenia stronicowanej wyników (usługi danych WCF)](http://go.microsoft.com/fwlink/?LinkId=193452).  
  
 Po dodaniu wszystkich klientów, jest zwracana lista. `GetCustomers` Metody jest określony w działaniu <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zastąpienia. Ponieważ metoda ma wartość zwracaną `Func<string, List<Customer>>` jest tworzony, aby określić metodę.  
  
> [!NOTE]
>  Jeśli metodę, która wykonuje asynchroniczne nie ma wartości zwracanej <xref:System.Action> jest używany zamiast <!--zz <xref:System.Func> --> `System.Func`. Przykłady tworzenia przykład asynchronicznych za pomocą obu metod można znaleźć [tworzenia działań asynchroniczne](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 To <!--zz <xref:System.Func> --> `System.Func` jest przypisany do <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie `BeginInvoke` jest wywoływana. Ponieważ wywoływanej metody nie ma dostępu do środowiska działania argumentów, wartość `ServiceUri` argument jest przekazywany jako pierwszego parametru wywołania zwrotnego i stanu, które zostały przekazane do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Gdy `GetCustomers` zwraca wywołuje środowiska uruchomieniowego <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kod w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> pobiera delegata z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, wywołania `EndInvoke`i zwraca wynik, który znajduje się lista klientów zwracanych z `GetCustomers` metody.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]  
  
 W poniższym przykładzie `ListCustomers` działanie pobiera listę klientów, a następnie <xref:System.Activities.Statements.ForEach%601> działanie wylicza je i zapisuje nazwy firmy i nazwisko osoby kontaktowej każdego klienta w konsoli.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]  
  
 Po wywołaniu tego przepływu pracy następujące dane są zapisywane do konsoli. Ponieważ ta kwerenda zwraca wielu klientów, w tym miejscu jest wyświetlany tylko część danych wyjściowych.  
  
 **Wywołanie usługi danych WCF...**  
**Futterkiste Alfreds, skontaktuj się z pomocą: Maria Anders**   
**Ana Trujillo Emparedados y helados, skontaktuj się z: Ana Trujillo**   
**Antonio Moreno Taquería, skontaktuj się z pomocą: Antonio Moreno**   
**Wokół sygnał dźwiękowy, skontaktuj się z: Hardy blogu Thomasa**   
**Snabbköp Berglunds, skontaktuj się z: Aneta Kowalski**   
**...**    
## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Wykorzystywanie źródła strumieniowego OData bez konieczności używania bibliotek klienta  
 OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikator URI. Gdy użyć bibliotek klienckich te identyfikatory URI są tworzone automatycznie, ale nie trzeba użyć bibliotek klienckich. W razie potrzeby bezpośrednio, bez używania bibliotek klienta są dostępne usługi OData. Gdy nie za pomocą biblioteki klienta lokalizację usługi i żądane dane są określane przez identyfikator URI i wyniki są zwracane w odpowiedzi na żądania HTTP. Te dane pierwotne można następnie przetworzenia lub manipulować w żądany sposób. Jednym ze sposobów pobrać wyniki zapytania OData jest za pomocą <xref:System.Net.WebClient> klasy. W tym przykładzie nazwa kontaktu klienta reprezentowany przez klucz ALFKI są pobierane.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]  
  
 Po uruchomieniu tego kodu, wyświetlane są następujące dane wyjściowe do konsoli:  
  
 **Nieprzetworzone dane zwrócone:**  
**\<? wersji xml = "1.0" encoding = "utf-8" autonomiczny = "yes"? >**   
**\<Nazwa kontaktu xmlns = "http://schemas.microsoft.com/ado/2007/08/dataservices" > Maria Anders\</ContactName >** w przepływie pracy, w tym przykładzie kodu można włączyć do <xref:System.Activities.CodeActivity.Execute%2A> zastąpienie <xref:System.Activities.CodeActivity>— na podstawie działania niestandardowego, ale takie same funkcja może być również wykonywane przy użyciu <xref:System.Activities.Expressions.InvokeMethod%601> działania. <xref:System.Activities.Expressions.InvokeMethod%601> Działania umożliwia autorom przepływu pracy Wywołaj statyczne i wystąpienie metody klasy, a ma również opcję, aby wywołać określonej metody asynchronicznie. W poniższym przykładzie <xref:System.Activities.Expressions.InvokeMethod%601> działanie jest skonfigurowane tak, aby wywołać <xref:System.Net.WebClient.DownloadString%2A> metody <xref:System.Net.WebClient> klasy i powrócić do listy odbiorców.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> można wywołać obu statyczna i wystąpienia metody klasy. Ponieważ <xref:System.Net.WebClient.DownloadString%2A> jest metodą wystąpienia <xref:System.Net.WebClient> klasy nowe wystąpienie klasy <xref:System.Net.WebClient> jest określona dla <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` jest określony jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identyfikator URI, który zawiera zapytanie jest określona w <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> kolekcji, a wartość zwracana jest przypisany do <xref:System.Activities.Activity%601.Result%2A> wartości. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Ma wartość `true`, co oznacza, że wywołanie metody będą wykonywane asynchronicznie w odniesieniu do przepływu pracy. W poniższym przykładzie przepływ pracy jest tworzony, który używa <xref:System.Activities.Expressions.InvokeMethod%601> działanie, aby zbadać przykładowych danych Northwind usługi listę zleceń dla określonego klienta, a następnie zwrócone dane są zapisywane do konsoli.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli. Ponieważ ta kwerenda zwraca kilku zamówień, tylko część danych wyjściowych jest wyświetlany w tym miejscu.  
  
 **Wywołanie usługi danych WCF...**  
**Nieprzetworzone dane zwrócone:**   
**\<? wersji xml = "1.0" encoding = "utf-8" autonomiczny = "yes"? >**   
**\<źródła danych**   
 **XML:Base = "http://services.odata.org/Northwind/Northwind.svc/"**  
 **xmlns:d = "http://schemas.microsoft.com/ado/2007/08/dataservices"**  
 **xmlns:m = "http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"**  
 **xmlns = "http://www.w3.org/2005/Atom" >**  
 **\<Typ title = "text" > zamówień \< /title >**  
 **\<Identyfikator >http://services.odata.org/Northwind/Northwind.svc/Customers("ALFKI") / porządkuje \< /identyfikator >**  
 **\<Zaktualizowano > 2010-05-19T19:37:07Z\</ zaktualizować >**  
 **\<Link rel = "Auto" title = "Zamówienia" href = "Zamówienia" / >**  
 **\<Wpis >**  
 **\<Identyfikator >http://services.odata.org/Northwind/Northwind.svc/Orders(10643) \< /identyfikator >**  
 **\<Typ title = "text" > \< /title >**  
 **\<Zaktualizowano > 2010-05-19T19:37:07Z\</ zaktualizować >**  
 **\<Autor >**  
 **\<nazwa / >**  
 **\</ author >**  
 **\<Link rel = "edit" title = "Order" href="Orders(10643)" / >**  
 **\<Link rel = "http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer"**  
 **Typ = "application/atom + xml; typ = entry" title = "Klient" href = "Zamówienia (10643) / klienta" / >**  
**...**  W poniższym przykładzie przedstawiono jedną metodę, która umożliwia korzystać nieprzetworzonych danych zwróconych z usługi OData autorzy aplikacji przepływu pracy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do usługi danych WCF za pomocą identyfikatorów URI, zobacz [podczas uzyskiwania dostępu do zasobów usługi danych (usługi danych WCF)](http://go.microsoft.com/fwlink/?LinkId=193397) i [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564).
