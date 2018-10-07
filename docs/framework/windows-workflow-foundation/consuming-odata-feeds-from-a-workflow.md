---
title: Zużyć OData, źródła danych z przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: 8d08a58cecead105f6e1f580ea40175cac93e417
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842414"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Zużyć OData, źródła danych z przepływu pracy

Usługi danych WCF jest składnikiem [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umożliwiająca tworzenie usług, które używają Open Data Protocol (OData) do prezentowania i wykorzystywania danych w Internecie lub intranecie przy użyciu semantyki (REST) representational state transfer. OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI. Każda aplikacja może współdziałać z usługi OData na podstawie danych można wysyłać żądania HTTP i przetwarzania strumieniowego źródła danych OData zwracanych usługi danych. Ponadto WCF Data Services zawiera biblioteki klienckie, które oferują więcej możliwości programowania, jeśli korzystasz ze źródłami danych OData z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji. Ten temat zawiera omówienie zużyć OData, źródła danych w przepływie pracy z lub bez korzystania z bibliotek klienckich.

## <a name="using-the-sample-northwind-odata-service"></a>Za pomocą przykładowej usługi Northwind OData

Przykłady w tym temacie Użyj przykładu Northwind usługi danych znajdującym się w [ http://services.odata.org/Northwind/Northwind.svc/ ](https://go.microsoft.com/fwlink/?LinkID=187426). Ta usługa jest dostarczana jako część [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248) i zapewnia dostęp tylko do odczytu do przykładowej bazy danych Northwind. Jeśli dostęp do zapisu lub razie lokalnej usługi danych WCF można postępuj zgodnie z instrukcjami z [Szybki Start usług danych WCF](https://go.microsoft.com/fwlink/?LinkID=131076) do utworzenia lokalnej usługi OData, która zapewnia dostęp do bazy danych Northwind. W przypadku użycia opcji szybkiego startu, Zastąp lokalny identyfikator URI dla podano w przykładowym kodzie, w tym temacie.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Korzystanie ze źródłem danych OData przy użyciu biblioteki klienta

WCF Data Services zawiera biblioteki klienckie, które umożliwiają używanie źródła danych z OData [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] i aplikacje klienckie. Te biblioteki upraszczają wysyłanie i odbieranie komunikatów HTTP. Mogą również wykonuje translację elementu ładunek komunikatu do obiektów CLR, które reprezentują dane jednostki. Biblioteki klienckie są wyposażone w dwóch głównych klas <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Klasy te umożliwiają zapytań usługi danych, a następnie pracować z danymi zwróconą jednostkę jako obiekty typu CLR. W tej sekcji omówiono dwa podejścia do tworzenia działań korzystających z bibliotek klienckich.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Dodawanie odwołania do usługi do usługi danych WCF

Aby wygenerować Northwind bibliotek klienta, można użyć **Dodaj odwołanie do usługi** okno dialogowe w programie Visual Studio 2012 można dodać odwołania do usługi Northwind OData.

![Dodaj odwołanie do usługi](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")

Należy pamiętać, że nie istnieją żadne operacje usługi udostępniane przez usługę, a następnie w **usług** listy istnieją elementów reprezentujących podmioty udostępnianych przez usługę danych Northwind. Po dodaniu odwołania do usługi, klas, które będą generowane dla tych jednostek i mogą być używane w kodzie klienta. W przykładach w tym temacie używany w ramach tych zajęć i `NorthwindEntities` klasy do wykonywania zapytań.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [Generowanie biblioteki klienta usługi danych (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkID=191611).

### <a name="using-asynchronous-methods"></a>Używanie metod asynchronicznych

Do adresu możliwych problemów z opóźnieniem, które mogą wystąpić podczas uzyskiwania dostępu do zasobów w sieci Web, zaleca się korzystanie z usług danych WCF asynchronicznie. Biblioteki klienta usługi danych WCF zawierają metody asynchroniczne wywoływanie zapytania, a także Windows Workflow Foundation (WF) <xref:System.Activities.AsyncCodeActivity> klasa do tworzenia działań asynchronicznych. <xref:System.Activities.AsyncCodeActivity> pochodne działania mogą być zapisywane z zalet [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] klas, które mają metod asynchronicznych lub kod, aby być wykonywany asynchronicznie, które mogą być wprowadzane do metody i wywoływane za pomocą delegata. Ta sekcja zawiera dwa przykłady <xref:System.Activities.AsyncCodeActivity> działanie pochodne; taki, który korzysta z biblioteki klienta usługi danych WCF metod asynchronicznych i jedną, która używa delegata.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193396) i [tworzenie działań asynchronicznych](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Używanie metod asynchronicznych biblioteki klienta

<xref:System.Data.Services.Client.DataServiceQuery%601> Klasa udostępnia <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> i <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody asynchroniczne wykonywanie zapytań usługi OData. Te metody mogą być wywoływane z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> przesłonięć o <xref:System.Activities.AsyncCodeActivity> klasy pochodnej. Gdy <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zwraca zastąpienie, przepływ pracy można go bezczynności (ale nie utrzymują), a po ukończeniu pracę asynchroniczną <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jest wywoływana w czasie wykonywania.

W poniższym przykładzie `OrdersByCustomer` działania jest zdefiniowana, że ma dwa wprowadzanie argumentów. `CustomerId` Argument reprezentuje klienta, który identyfikuje zamówienia przywrócić, i `ServiceUri` argument reprezentuje identyfikator URI usługi OData można wykonywać zapytania. Ponieważ pochodzi od klasy działania `AsyncCodeActivity<IEnumerable<Order>>` dostępna jest również <xref:System.Activities.Activity%601.Result%2A> danych wyjściowych argumentu, który służy do zwracania wyników zapytania. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Zastąpienie tworzy zapytanie LINQ, który wybiera wszystkie zamówienia klienta określony. To zapytanie jest określony jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> przekazanych <xref:System.Activities.AsyncCodeActivityContext>, a następnie kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda jest wywoływana. Należy pamiętać, że wywołania zwrotnego i stanu, które są przekazywane do kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> są tymi, które są przekazywane do działania <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metody. Gdy zapytanie zostało zakończone, wykonywania działań <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metoda jest wywoływana. Zapytanie jest pobierana z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie kwerendy <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda jest wywoływana. Ta metoda zwraca <xref:System.Collections.Generic.IEnumerable%601> określonego typu jednostek; w tym przypadku `Order`. Ponieważ `IEnumerable<Order>` jest ogólny typ <xref:System.Activities.AsyncCodeActivity%601>ten `IEnumerable` jest ustawiony jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> działania.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

W poniższym przykładzie `OrdersByCustomer` działanie pobiera listę zamówień dla określonego klienta, a następnie <xref:System.Activities.Statements.ForEach%601> działania wylicza zwrócone zamówień i zapisuje daty każde zamówienie do konsoli.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Po wywołaniu tego przepływu pracy następujące dane są zapisywane do konsoli:

```console
Calling WCF Data Service...
8/25/1997
10/3/1997
10/13/1997
1/15/1998
3/16/1998
4/9/1998
```

> [!NOTE]
> Jeśli nie można ustanowić połączenia z serwerem OData, wyjątek zostanie wyświetlony podobny do następującego wyjątku:
>
> Nieobsługiwany wyjątek: System.InvalidOperationException: Wystąpił błąd podczas przetwarzania tego żądania. ---> System.Net.WebException: nie można nawiązać połączenia z serwerem zdalnym---> System.Net.Sockets.SocketException: próba połączenia nie powiodło się, ponieważ strona połączona nie odpowiedziała poprawnie po określonym czasie lub ustanowionych połączeń nie powiodło się. ponieważ połączony host nie odpowiedział.

Jeśli wymagana jest dowolnym dodatkowego przetwarzania danych zwróconych przez zapytanie, możesz zrobić w ramach działania <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> zastąpienia. Zarówno <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> są wywoływane za pomocą wątku przepływu pracy, a każdy kod te zastąpienia nie jest uruchamiane asynchronicznie. Jeśli dodatkowego przetwarzania jest wykonanie obszernych lub długotrwałe lub wyniki zapytania są stronicowane, należy rozważyć podejście omówiona w następnej sekcji używa delegata, aby wykonać zapytanie i wykonać dodatkowe przetwarzanie asynchroniczne.

### <a name="using-a-delegate"></a>Używanie delegata

Oprócz asynchroniczne wywołanie metody z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] klasy <xref:System.Activities.AsyncCodeActivity>— w jednej z jego metod działania na podstawie można również zdefiniować logiki przetwarzania asynchronicznego. Ta metoda jest określana za pomocą delegata w ramach działania <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zastąpienia. Gdy metoda zwróci wartość, środowisko uruchomieniowe wywołuje działania <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastąpienia. Podczas wywoływania usługi OData z przepływu pracy, ta metoda może służyć do tworzenia zapytań usługi i Podaj wszelkie dodatkowe przetwarzanie.

W poniższym przykładzie `ListCustomers` działania jest zdefiniowana. To działanie wysyła zapytanie usługi przykładowych danych Northwind i zwraca `List<Customer>` zawierającą wszystkich klientów w bazie danych Northwind. Asynchroniczne zadanie jest wykonywane przez `GetCustomers` metody. Ta metoda wysyła zapytanie do usługi dla wszystkich klientów, a następnie kopiuje je do `List<Customer>`. Następnie sprawdza, jeśli są stronicowane wyniki. Jeśli tak, wysyła zapytanie do usługi dla następnej strony wyników, dodaje je do listy i jest powtarzany do momentu pobraniu wszystkich danych klientów.

> [!NOTE]
> Aby uzyskać więcej informacji na temat stronicowania w usługach danych programu WCF Zobacz. [Porady: ładowanie stronicowanych wyników (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193452).

Po dodaniu wszystkich klientów, zwracana jest lista. `GetCustomers` Metoda jest określona w działaniu <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> zastąpienia. Ponieważ metoda nie zwraca wartości, `Func<string, List<Customer>>` zostanie utworzony, aby określić metodę.

> [!NOTE]
> Jeśli metoda, która wykonuje pracę asynchroniczną nie jest zwracana wartość <xref:System.Action> jest używana zamiast <!--zz <xref:System.Func> --> `System.Func`. Przykłady tworzenia asynchronicznych przykład użycia obu metod, zobacz [tworzenie działań asynchronicznych](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

To <!--zz <xref:System.Func> --> `System.Func` jest przypisany do <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie `BeginInvoke` jest wywoływana. Ponieważ wywoływanej metody nie ma dostępu do tego działania środowiska argumentów i wartości `ServiceUri` argument jest przekazywany jako pierwszy parametr, wraz z wywołania zwrotnego i stanu, które zostały przekazane do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Gdy `GetCustomers` zwróci wartość, środowisko uruchomieniowe wywołuje <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kod w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> pobiera delegata z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, wywołania `EndInvoke`i zwraca wynik, który znajduje się lista klientów zwróciło `GetCustomers` metody.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

W poniższym przykładzie `ListCustomers` działanie pobiera listę klientów, a następnie <xref:System.Activities.Statements.ForEach%601> działanie wylicza je i zapisuje nazwy firmy i nazwisko osoby kontaktowej każdego klienta w konsoli.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Po wywołaniu tego przepływu pracy następujące dane są zapisywane do konsoli. Ponieważ ta kwerenda zwraca wielu klientów, w tym miejscu jest wyświetlany tylko część danych wyjściowych.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Wykorzystywanie źródłem danych OData bez korzystania z bibliotek klienckich

OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI. Kiedy użyć bibliotek klienckich są tworzone następujące identyfikatory URI, ale nie trzeba korzystać z bibliotek klienta. Jeśli to konieczne, dostęp do usługi OData są dostępne bezpośrednio, bez korzystania z bibliotek klienckich. Bez korzystania z biblioteki klienta lokalizacji usługi i żądane dane są określone przez identyfikator URI, a wyniki są zwracane w odpowiedzi na żądania HTTP. Można następnie przetwarzane tych pierwotnych danych lub zmieniane w żądany sposób. Jednym ze sposobów pobierania wyników zapytania OData jest za pomocą <xref:System.Net.WebClient> klasy. W tym przykładzie jest pobierana nazwa kontaktu dla klientów, reprezentowane przez klucz ALFKI.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Po uruchomieniu tego kodu następujące dane wyjściowe są wyświetlane w konsoli:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

W przepływie pracy, kod w tym przykładzie można włączyć do <xref:System.Activities.CodeActivity.Execute%2A> zastępowania <xref:System.Activities.CodeActivity>— na podstawie niestandardowych działań, ale taką samą funkcjonalność może być również wykonywane przy użyciu <xref:System.Activities.Expressions.InvokeMethod%601> działania. <xref:System.Activities.Expressions.InvokeMethod%601> Działanie umożliwia autorom zawartości przepływu pracy do wywołania statycznych lub wystąpienie metody klasy i ma również możliwość wywołania określonej metody asynchronicznie. W poniższym przykładzie <xref:System.Activities.Expressions.InvokeMethod%601> działanie jest skonfigurowane do wywołania <xref:System.Net.WebClient.DownloadString%2A> metody <xref:System.Net.WebClient> klasy i powrócić do listy klientów.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> można wywołać statycznych i wystąpienia metody klasy. Ponieważ <xref:System.Net.WebClient.DownloadString%2A> jest metodą wystąpienia elementu <xref:System.Net.WebClient> nowe wystąpienie klasy <xref:System.Net.WebClient> klasy jest określona dla <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` jest określony jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identyfikator URI, który zawiera zapytanie jest określona w <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> kolekcji i wartość zwracana jest przypisany do <xref:System.Activities.Activity%601.Result%2A> wartości. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Wartość jest równa `true`, co oznacza, że wywołanie metody będą wykonywane asynchronicznie w odniesieniu do przepływu pracy. W poniższym przykładzie przepływu pracy jest tworzony, który używa <xref:System.Activities.Expressions.InvokeMethod%601> działania do wykonywania zapytań z przykładowych danych Northwind usługi lista zamówień dla danego klienta, a następnie zwrócone dane są zapisywane do konsoli.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli. Ponieważ ta kwerenda zwraca kilka zamówień, tylko część danych wyjściowych jest wyświetlane w tym miejscu.

```console
Calling WCF Data Service...
Raw data returned:

<?xml version="1.0" encoding="utf-8" standalone="yes"?>*
<feed
xml:base="http://services.odata.org/Northwind/Northwind.svc/"
xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices"
xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"
xmlns="http://www.w3.org/2005/Atom">
<title type="text">Orders\</title>
<id>http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders\</id>
<updated>2010-05-19T19:37:07Z\</updated>
<link rel="self" title="Orders" href="Orders" />
<entry>
<id>http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id>
<title type="text">\</title>
<updated>2010-05-19T19:37:07Z\</updated>
<author>
<name />
</author>
<link rel="edit" title="Order" href="Orders(10643)" />
<link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer" type="application/atom+xml;type=entry" title="Customer" href="Orders(10643)/Customer" />
...
```

W tym przykładzie zawiera jedną metodę, która umożliwia używanie nieprzetworzonych danych zwróconych z usługi OData autorzy aplikacji przepływu pracy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do usługi danych programu WCF za pomocą identyfikatorów URI, zobacz [uzyskiwania dostępu do zasobów usługi danych (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193397) i [OData: identyfikator URI konwencje](https://go.microsoft.com/fwlink/?LinkId=185564).
