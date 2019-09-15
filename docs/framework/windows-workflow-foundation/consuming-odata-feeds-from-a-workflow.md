---
title: Zużywanie strumieniowych danych OData z przepływu pracy — WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: e7cfa138a01719988586f9dce0a9009bea643076
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989767"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Zużywanie źródeł danych OData z przepływu pracy

Usługi danych programu WCF jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki przenoszenia stanu (REST). Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. Każda aplikacja może korzystać z usługi danych opartych na protokole OData, jeśli może wysyłać żądanie HTTP i przetwarzać źródło danych OData. Ponadto Usługi danych programu WCF obejmuje biblioteki klienckie, które zapewniają bogatsze środowisko programistyczne w przypadku korzystania ze źródeł danych OData z aplikacji .NET Framework. Ten temat zawiera omówienie używania źródła danych OData w przepływie pracy z i bez użycia bibliotek klienckich.

## <a name="using-the-sample-northwind-odata-service"></a>Korzystanie z przykładowej usługi OData Northwind

Przykłady w tym temacie wykorzystują przykładową usługę danych Northwind znajdującą <https://services.odata.org/Northwind/Northwind.svc/>się w. Ta usługa jest świadczona jako część [zestawu SDK OData](https://go.microsoft.com/fwlink/?LinkID=185248) i zapewnia dostęp tylko do odczytu do przykładowej bazy danych Northwind. Jeśli wymagana jest funkcja dostępu do zapisu lub jeśli jest wymagana lokalna usługa danych programu WCF, można wykonać kroki przedstawione w [usługi danych programu WCF przewodniku szybki start](https://go.microsoft.com/fwlink/?LinkID=131076) , aby utworzyć lokalną usługę OData, która zapewnia dostęp do bazy danych Northwind. W przypadku skorzystania z przewodnika Szybki Start należy zastąpić lokalny identyfikator URI dla tego, który został podany w przykładowym kodzie w tym temacie.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Zużywanie źródła danych OData przy użyciu bibliotek klienckich

Usługi danych programu WCF obejmuje biblioteki klienckie, które umożliwiają łatwiejsze korzystanie z kanału informacyjnego OData z aplikacji .NET Framework i klienckich. Te biblioteki upraszczają wysyłanie i otrzymywanie komunikatów HTTP. Tłumaczą one również ładunek komunikatów na obiekty CLR, które reprezentują dane jednostki. Biblioteki klienckie są wyposażone w dwie klasy <xref:System.Data.Services.Client.DataServiceContext> podstawowe i. <xref:System.Data.Services.Client.DataServiceQuery%601> Te klasy umożliwiają wykonywanie zapytań do usługi danych, a następnie współpracują z zwróconymi danymi jednostki jako obiektami CLR. Ta sekcja dotyczy dwóch metod tworzenia działań, które korzystają z bibliotek klienckich.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Dodawanie odwołania do usługi do usługi danych programu WCF

Aby wygenerować biblioteki klienckie Northwind, można użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio 2012 w celu dodania odwołania do usługi Northwind OData.

![Zrzut ekranu przedstawiający okno dialogowe Dodaj odwołanie do usługi.](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Należy zauważyć, że usługa nie udostępnia żadnych operacji usługi, a na liście **usług** znajdują się elementy reprezentujące jednostki udostępniane przez usługę danych Northwind. Po dodaniu odwołania do usługi klasy zostaną wygenerowane dla tych jednostek i mogą być używane w kodzie klienta. Przykłady w tym temacie używają tych klas i `NorthwindEntities` klasy do wykonywania zapytań.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych (usługi danych programu WCF)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Korzystanie z metod asynchronicznych

Aby rozwiązać możliwe problemy z opóźnieniem, które mogą wystąpić podczas uzyskiwania dostępu do zasobów za pośrednictwem sieci Web, zalecamy asynchroniczne uzyskiwanie dostępu do Usługi danych programu WCF. Biblioteki klienta usługi danych programu WCF zawierają metody asynchroniczne do wywoływania zapytań, a Windows Workflow Foundation (WF) udostępnia <xref:System.Activities.AsyncCodeActivity> klasę do tworzenia działań asynchronicznych. <xref:System.Activities.AsyncCodeActivity>działania pochodne można napisać, aby korzystać z .NET Framework klas, które mają metody asynchroniczne, lub kod, który ma być wykonywany asynchronicznie, można umieścić w metodzie i wywołać za pomocą delegata. Ta sekcja zawiera dwa przykłady <xref:System.Activities.AsyncCodeActivity> działania pochodnego, które korzysta z metod asynchronicznych usługi danych programu WCF bibliotek klienckich i jednego, który używa delegata.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne (usługi danych programu WCF)](../data/wcf/asynchronous-operations-wcf-data-services.md) i [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Korzystanie z metod asynchronicznych biblioteki klienta

Klasa zawiera <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> i<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody wysyłania zapytań do usługi OData asynchronicznie. <xref:System.Data.Services.Client.DataServiceQuery%601> Metody te mogą być wywoływane z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> przesłonięć <xref:System.Activities.AsyncCodeActivity> klasy pochodnej. Gdy przesłonięcie zwraca, przepływ pracy może przechodzić bezczynnie (ale nie utrzymywać), a po zakończeniu pracy <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> asynchronicznej jest wywoływany przez środowisko uruchomieniowe. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity>

W poniższym przykładzie `OrdersByCustomer` zdefiniowano działanie, które ma dwa argumenty wejściowe. Argument reprezentuje klienta, który identyfikuje, które zlecenia zwracają, `ServiceUri` a argument reprezentuje identyfikator URI usługi OData do zbadania. `CustomerId` Ponieważ działanie pochodzi z `AsyncCodeActivity<IEnumerable<Order>>` <xref:System.Activities.Activity%601.Result%2A> również argumentu danych wyjściowych, który jest używany do zwracania wyników zapytania. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Zastąpienie powoduje utworzenie zapytania LINQ, które wybiera wszystkie zamówienia określonego klienta. To zapytanie jest określone jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> zakończone <xref:System.Activities.AsyncCodeActivityContext>, <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a następnie wywoływana jest metoda zapytania. Należy zauważyć, że wywołanie zwrotne i stan, które są przesyłane <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> do zapytania, są tymi, które są przesyłane do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metody działania. Po zakończeniu wykonywania zapytania zostanie wywołana <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> Metoda działania. Zapytanie jest pobierane z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie wywoływana jest <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> Metoda zapytania. Ta metoda zwraca <xref:System.Collections.Generic.IEnumerable%601> dla określonego typu jednostki; w tym przypadku `Order`. Ponieważ `IEnumerable<Order>` jest typem <xref:System.Activities.AsyncCodeActivity%601>ogólnym, jest <xref:System.Collections.IEnumerable> <xref:System.Activities.Activity%601.Result%2A> toustawieniejakodziałanie.<xref:System.Activities.OutArgument%601>

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

W poniższym przykładzie `OrdersByCustomer` działanie pobiera listę zamówień dla określonego klienta, a <xref:System.Activities.Statements.ForEach%601> następnie działanie wylicza zwrócone zamówienia i zapisuje datę każdego zamówienia w konsoli programu.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Po wywołaniu tego przepływu pracy w konsoli zapisywane są następujące dane:

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
> Jeśli nie można nawiązać połączenia z serwerem OData, zostanie wyświetlony wyjątek podobny do następującego:
>
> Nieobsłużony wyjątek: System.InvalidOperationException: Wystąpił błąd podczas przetwarzania tego żądania. ---> System .NET. WebException: Nie można nawiązać połączenia z serwerem zdalnym---> System .NET. Sockets. SocketException: Próba nawiązania połączenia nie powiodła się, ponieważ połączona Strona nie odpowiedziała prawidłowo po upływie określonego czasu lub nawiązane połączenie nie powiodło się, ponieważ podłączony host nie odpowiedział.

Jeśli wymagane jest dodatkowe przetwarzanie danych zwróconych przez zapytanie, można je wykonać w <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> przesłonięciu działania. Oba <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> i<xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> są wywoływane przy użyciu wątku przepływu pracy, a każdy kod w tych zastąpień nie działa asynchronicznie. Jeśli dodatkowe przetwarzanie jest rozległe lub długotrwałe lub wyniki zapytania są stronicowane, należy wziąć pod uwagę podejście omówione w następnej sekcji, która używa delegata do wykonywania zapytania i wykonywania dodatkowego przetwarzania asynchronicznego.

### <a name="using-a-delegate"></a>Korzystanie z delegata

Oprócz wywoływania asynchronicznej metody klasy .NET Framework, <xref:System.Activities.AsyncCodeActivity>działające na podstawie można także zdefiniować logikę asynchroniczną w jednej z jej metod. Ta metoda jest określona za pomocą delegata w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> przesłonięciu działania. Gdy metoda zwraca, środowisko uruchomieniowe wywołuje <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> przesłonięcie działania. Podczas wywoływania usługi OData z przepływu pracy ta metoda może służyć do wysyłania zapytań do usługi i zapewnienia dodatkowego przetwarzania.

W poniższym przykładzie `ListCustomers` zdefiniowano działanie. To działanie wysyła zapytanie do przykładowej usługi danych Northwind i `List<Customer>` zwraca wartość zawierającą wszystkich klientów w bazie danych Northwind. Asynchroniczne działanie jest wykonywane przez `GetCustomers` metodę. Ta metoda wysyła zapytanie do usługi dla wszystkich klientów, a następnie kopiuje je do `List<Customer>`programu. Następnie sprawdza, czy wyniki są wyświetlane na stronie. Jeśli tak, wysyła zapytanie do usługi pod kątem następnej strony wyników, dodaje je do listy i kontynuuje do momentu pobrania wszystkich danych klienta.

> [!NOTE]
> Aby uzyskać więcej informacji na temat stronicowania w [usługi danych programu WCF, zobacz How to: Załaduj stronicowane wyniki (Usługi danych programu WCF](../data/wcf/how-to-load-paged-results-wcf-data-services.md)).

Po dodaniu wszystkich klientów zostanie zwrócona lista. Metoda jest określona w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> przesłonięciu działania. `GetCustomers` Ponieważ metoda ma wartość zwracaną, `Func<string, List<Customer>>` jest tworzona, aby określić metodę.

> [!NOTE]
> Jeśli metoda wykonująca zadanie asynchroniczne nie ma wartości zwracanej, <xref:System.Action> zamiast elementu <xref:System.Func%601>zostanie użyta wartość. Przykłady tworzenia przykładu asynchronicznego przy użyciu obu podejścia można znaleźć w temacie [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).

Jest <xref:System.Func%601> on przypisywany <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>do, a następnie `BeginInvoke` jest wywoływany. Ponieważ metoda, która ma zostać wywołana, nie ma dostępu do środowiska działania argumentów, wartość `ServiceUri` argumentu jest przenoszona jako pierwszy parametr wraz z wywołaniem zwrotnym i stanem, który został <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>przekazano. Gdy `GetCustomers` zwraca, środowisko uruchomieniowe <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>wywołuje. Kod w programie <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> pobiera delegata <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>z, wywołuje `EndInvoke`i zwraca wynik, który `GetCustomers` jest listą klientów zwracanych z metody.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

W poniższym przykładzie `ListCustomers` działanie pobiera listę klientów, a <xref:System.Activities.Statements.ForEach%601> następnie wylicza je i zapisuje nazwę firmy oraz nazwę kontaktu każdego klienta w konsoli programu.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Po wywołaniu tego przepływu pracy następujące dane są zapisywane w konsoli programu. Ponieważ to zapytanie zwraca wielu klientów, w tym miejscu jest wyświetlana tylko część danych wyjściowych.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Zużywanie źródła danych OData bez użycia bibliotek klienckich

Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. W przypadku korzystania z bibliotek klienckich te identyfikatory URI są tworzone dla Ciebie, ale nie trzeba używać bibliotek klienckich. W razie potrzeby usługi OData są dostępne bezpośrednio bez używania bibliotek klienckich. Gdy nie korzystasz z bibliotek klienckich, lokalizacja usługi i żądane dane są określone przez identyfikator URI, a wyniki są zwracane w odpowiedzi na żądanie HTTP. Te nieprzetworzone dane można następnie przetworzyć lub przetwarzać w odpowiedni sposób. Jednym ze sposobów pobierania wyników zapytania OData jest użycie <xref:System.Net.WebClient> klasy. W tym przykładzie zostanie pobrana nazwa kontaktu dla klienta reprezentowanego przez usługi Key ALFKI.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Po uruchomieniu tego kodu następujące dane wyjściowe są wyświetlane w konsoli programu:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

W przepływie pracy kod z tego przykładu może zostać włączony do <xref:System.Activities.CodeActivity.Execute%2A> zastąpienia <xref:System.Activities.CodeActivity>niestandardowego działania opartego na bazie, ale te same funkcje można także <xref:System.Activities.Expressions.InvokeMethod%601> wykonać przy użyciu działania. <xref:System.Activities.Expressions.InvokeMethod%601> Działanie umożliwia autorom przepływu pracy wywoływanie metod statycznych i wystąpień klasy, a także opcję wywołania określonej metody asynchronicznie. W poniższym przykładzie <xref:System.Activities.Expressions.InvokeMethod%601> działanie jest skonfigurowane do <xref:System.Net.WebClient.DownloadString%2A> wywoływania metody <xref:System.Net.WebClient> klasy i zwracają listę klientów.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601>może wywoływać zarówno metody statyczne, jak i wystąpienia klasy. Ponieważ <xref:System.Net.WebClient.DownloadString%2A> jest to metoda <xref:System.Net.WebClient> wystąpienia klasy, dla <xref:System.Net.WebClient> <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>elementu należy określić nowe wystąpienie klasy. `DownloadString`jest określony jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identyfikator URI, który zawiera zapytanie jest określony <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> w kolekcji, a <xref:System.Activities.Activity%601.Result%2A> wartość zwracana jest przypisana do wartości. Wartość jest ustawiona na `true`, co oznacza, że wywołanie metody zostanie uruchomione asynchronicznie w odniesieniu do przepływu pracy. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> W poniższym przykładzie zostanie skonstruowany przepływ pracy, który używa <xref:System.Activities.Expressions.InvokeMethod%601> działania do wysyłania zapytań do przykładowej usługi danych Northwind o listę zamówień dla określonego klienta, a następnie zwrócone dane są zapisywane w konsoli programu.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu. Ponieważ to zapytanie zwraca kilka zamówień, w tym miejscu są wyświetlane tylko część danych wyjściowych.

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

Ten przykład zawiera jedną metodę, która może być używana przez autorów aplikacji przepływu pracy do korzystania z danych pierwotnych zwróconych z usługi OData. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do usługi danych programu WCF przy użyciu identyfikatorów URI, zobacz [Uzyskiwanie dostępu do zasobów usługi danych (usługi danych programu WCF)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) i [OData: Konwencje](https://go.microsoft.com/fwlink/?LinkId=185564)identyfikatora URI.
