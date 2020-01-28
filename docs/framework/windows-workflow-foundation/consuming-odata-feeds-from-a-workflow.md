---
title: Zużywanie strumieniowych danych OData z przepływu pracy — WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: ceac2c2d07351fcb79e2345068f07fa22f356411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743791"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Zużywanie źródeł danych OData z przepływu pracy

Usługi danych programu WCF jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki przenoszenia stanu (REST). Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. Każda aplikacja może korzystać z usługi danych opartych na protokole OData, jeśli może wysyłać żądanie HTTP i przetwarzać źródło danych OData. Ponadto Usługi danych programu WCF obejmuje biblioteki klienckie, które zapewniają bogatsze środowisko programistyczne w przypadku korzystania ze źródeł danych OData z aplikacji .NET Framework. Ten temat zawiera omówienie używania źródła danych OData w przepływie pracy z i bez użycia bibliotek klienckich.

## <a name="using-the-sample-northwind-odata-service"></a>Korzystanie z przykładowej usługi OData Northwind

Przykłady w tym temacie wykorzystują przykładową usługę danych Northwind znajdującą się w <https://services.odata.org/Northwind/Northwind.svc/>. Ta usługa jest świadczona jako część [zestawu SDK OData](https://www.odata.org/ecosystem/#sdk) i zapewnia dostęp tylko do odczytu do przykładowej bazy danych Northwind. Jeśli wymagana jest funkcja dostępu do zapisu lub jeśli jest wymagana lokalna usługa danych programu WCF, można wykonać kroki przedstawione w [usługi danych programu WCF przewodniku szybki start](../data/wcf/quickstart-wcf-data-services.md) , aby utworzyć lokalną usługę OData, która zapewnia dostęp do bazy danych Northwind. W przypadku skorzystania z przewodnika Szybki Start należy zastąpić lokalny identyfikator URI dla tego, który został podany w przykładowym kodzie w tym temacie.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Zużywanie źródła danych OData przy użyciu bibliotek klienckich

Usługi danych programu WCF obejmuje biblioteki klienckie, które umożliwiają łatwiejsze korzystanie z kanału informacyjnego OData z aplikacji .NET Framework i klienckich. Te biblioteki upraszczają wysyłanie i otrzymywanie komunikatów HTTP. Tłumaczą one również ładunek komunikatów na obiekty CLR, które reprezentują dane jednostki. Biblioteki klienckie oferują dwie klasy podstawowe <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Te klasy umożliwiają wykonywanie zapytań do usługi danych, a następnie współpracują z zwróconymi danymi jednostki jako obiektami CLR. Ta sekcja dotyczy dwóch metod tworzenia działań, które korzystają z bibliotek klienckich.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Dodawanie odwołania do usługi do usługi danych programu WCF

Aby wygenerować biblioteki klienckie Northwind, można użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio 2012 w celu dodania odwołania do usługi Northwind OData.

![Zrzut ekranu przedstawiający okno dialogowe Dodaj odwołanie do usługi.](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Należy zauważyć, że usługa nie udostępnia żadnych operacji usługi, a na liście **usług** znajdują się elementy reprezentujące jednostki udostępniane przez usługę danych Northwind. Po dodaniu odwołania do usługi klasy zostaną wygenerowane dla tych jednostek i mogą być używane w kodzie klienta. Przykłady w tym temacie używają tych klas i klasy `NorthwindEntities` do wykonywania zapytań.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych (usługi danych programu WCF)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Korzystanie z metod asynchronicznych

Aby rozwiązać możliwe problemy z opóźnieniem, które mogą wystąpić podczas uzyskiwania dostępu do zasobów za pośrednictwem sieci Web, zalecamy asynchroniczne uzyskiwanie dostępu do Usługi danych programu WCF. Biblioteki klienta Usługi danych programu WCF zawierają metody asynchroniczne do wywoływania zapytań, a Windows Workflow Foundation (WF) udostępnia klasę <xref:System.Activities.AsyncCodeActivity> do tworzenia działań asynchronicznych. <xref:System.Activities.AsyncCodeActivity> działań pochodnych można napisać, aby wykorzystać klasy .NET Framework z metodami asynchronicznymi lub kod, który ma być wykonywany asynchronicznie, można umieścić w metodzie i wywołać za pomocą delegata. Ta sekcja zawiera dwa przykłady działań pochodnych <xref:System.Activities.AsyncCodeActivity>; jeden, który korzysta z metod asynchronicznych Usługi danych programu WCF bibliotek klienckich i jeden, który używa delegata.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne (usługi danych programu WCF)](../data/wcf/asynchronous-operations-wcf-data-services.md) i [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Korzystanie z metod asynchronicznych biblioteki klienta

Klasa <xref:System.Data.Services.Client.DataServiceQuery%601> dostarcza metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> i <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> do asynchronicznego wykonywania zapytań dotyczących usługi OData. Metody te mogą być wywoływane z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastąpień <xref:System.Activities.AsyncCodeActivity> klasy pochodnej. Gdy <xref:System.Activities.AsyncCodeActivity> przesłonić <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>, przepływ pracy może przejść w stan bezczynności (ale nie utrzymywać) i po ukończeniu pracy asynchronicznej <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jest wywoływany przez środowisko uruchomieniowe.

W poniższym przykładzie zdefiniowano działanie `OrdersByCustomer`, które ma dwa argumenty wejściowe. Argument `CustomerId` reprezentuje klienta, który identyfikuje, które zlecenia zwracają, a argument `ServiceUri` reprezentuje identyfikator URI usługi OData do zbadania. Ponieważ działanie pochodzi z `AsyncCodeActivity<IEnumerable<Order>>` istnieje również argument danych wyjściowych <xref:System.Activities.Activity%601.Result%2A>, który jest używany do zwracania wyników zapytania. Zastępowanie <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> powoduje utworzenie zapytania LINQ, które wybiera wszystkie zamówienia określonego klienta. To zapytanie jest określone jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> przekazaną <xref:System.Activities.AsyncCodeActivityContext>, a następnie wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> zapytania. Należy zauważyć, że wywołanie zwrotne i stan, które są przesyłane do <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> zapytania są te, które są przesyłane do metody <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> działania. Po zakończeniu wykonywania zapytania zostanie wywołana metoda <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> działania. Zapytanie jest pobierane z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> kwerendy. Ta metoda zwraca <xref:System.Collections.Generic.IEnumerable%601> określonego typu jednostki; w tym przypadku `Order`. Ponieważ `IEnumerable<Order>` jest typem ogólnym <xref:System.Activities.AsyncCodeActivity%601>, ten <xref:System.Collections.IEnumerable> jest ustawiany jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> działania.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

W poniższym przykładzie działanie `OrdersByCustomer` pobiera listę zamówień dla określonego klienta, a następnie działanie <xref:System.Activities.Statements.ForEach%601> wylicza zwrócone zamówienia i zapisuje datę każdego zamówienia w konsoli programu.

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
> Nieobsługiwany wyjątek: System. InvalidOperationException: Wystąpił błąd podczas przetwarzania tego żądania. ---> System .NET. WebException: nie można nawiązać połączenia z serwerem zdalnym---> System .NET. Sockets. SocketException: próba nawiązania połączenia nie powiodła się, ponieważ połączona Strona nie odpowiedziała prawidłowo po upływie określonego czasu lub nawiązane połączenie nie powiodło się ponieważ podłączony host nie odpowiedział.

Jeśli wymagane jest dodatkowe przetwarzanie danych zwróconych przez zapytanie, można je wykonać w przesłonięciu <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> działania. Zarówno <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A>, jak i <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> są wywoływane przy użyciu wątku przepływu pracy, a każdy kod w tych zastąpień nie działa asynchronicznie. Jeśli dodatkowe przetwarzanie jest rozległe lub długotrwałe lub wyniki zapytania są stronicowane, należy wziąć pod uwagę podejście omówione w następnej sekcji, która używa delegata do wykonywania zapytania i wykonywania dodatkowego przetwarzania asynchronicznego.

### <a name="using-a-delegate"></a>Korzystanie z delegata

Oprócz wywoływania asynchronicznej metody klasy .NET Framework, działania oparte na <xref:System.Activities.AsyncCodeActivity>można także zdefiniować dla logiki asynchronicznej w jednej z jej metod. Ta metoda jest określana za pomocą delegata w przesłonięciu <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> działania. Gdy metoda zwraca, środowisko uruchomieniowe wywoła przesłonięcie <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> działania. Podczas wywoływania usługi OData z przepływu pracy ta metoda może służyć do wysyłania zapytań do usługi i zapewnienia dodatkowego przetwarzania.

W poniższym przykładzie zdefiniowano działanie `ListCustomers`. To działanie wysyła zapytanie do przykładowej usługi danych Northwind i zwraca `List<Customer>`, która zawiera wszystkich klientów w bazie danych Northwind. Asynchroniczne działanie jest wykonywane przez metodę `GetCustomers`. Ta metoda wysyła zapytanie do usługi dla wszystkich klientów, a następnie kopiuje je do `List<Customer>`. Następnie sprawdza, czy wyniki są wyświetlane na stronie. Jeśli tak, wysyła zapytanie do usługi pod kątem następnej strony wyników, dodaje je do listy i kontynuuje do momentu pobrania wszystkich danych klienta.

> [!NOTE]
> Aby uzyskać więcej informacji na temat stronicowania w Usługi danych programu WCF, zobacz [How to: Loaded Results (usługi danych programu WCF)](../data/wcf/how-to-load-paged-results-wcf-data-services.md).

Po dodaniu wszystkich klientów zostanie zwrócona lista. Metoda `GetCustomers` jest określona w przesłonięciu <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> działania. Ponieważ metoda ma wartość zwracaną, tworzony jest `Func<string, List<Customer>>`, aby określić metodę.

> [!NOTE]
> Jeśli metoda wykonująca zadanie asynchroniczne nie ma wartości zwracanej, zamiast <xref:System.Func%601>zostanie użyta <xref:System.Action>. Przykłady tworzenia przykładu asynchronicznego przy użyciu obu podejścia można znaleźć w temacie [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).

Ta <xref:System.Func%601> jest przypisana do <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, a następnie `BeginInvoke` jest wywoływana. Ponieważ metoda, która ma zostać wywołana, nie ma dostępu do środowiska działania argumentów, wartość argumentu `ServiceUri` jest przenoszona jako pierwszy parametr wraz z wywołaniem zwrotnym i stanem, które zostały przekazane do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Gdy `GetCustomers` zwraca, środowisko uruchomieniowe wywoła <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kod w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> pobiera delegata z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, wywołuje `EndInvoke`i zwraca wynik, który jest listą klientów zwracanych z metody `GetCustomers`.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

W poniższym przykładzie działanie `ListCustomers` pobiera listę klientów, a następnie działanie <xref:System.Activities.Statements.ForEach%601> wylicza je i zapisuje nazwę firmy oraz nazwę kontaktu każdego klienta w konsoli programu.

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

Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. W przypadku korzystania z bibliotek klienckich te identyfikatory URI są tworzone dla Ciebie, ale nie trzeba używać bibliotek klienckich. W razie potrzeby usługi OData są dostępne bezpośrednio bez używania bibliotek klienckich. Gdy nie korzystasz z bibliotek klienckich, lokalizacja usługi i żądane dane są określone przez identyfikator URI, a wyniki są zwracane w odpowiedzi na żądanie HTTP. Te nieprzetworzone dane można następnie przetworzyć lub przetwarzać w odpowiedni sposób. Jednym ze sposobów pobierania wyników zapytania OData jest użycie klasy <xref:System.Net.WebClient>. W tym przykładzie zostanie pobrana nazwa kontaktu dla klienta reprezentowanego przez usługi Key ALFKI.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Po uruchomieniu tego kodu następujące dane wyjściowe są wyświetlane w konsoli programu:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

W przepływie pracy kod z tego przykładu można włączyć do <xref:System.Activities.CodeActivity.Execute%2A> przesłonięcia niestandardowego działania opartego na <xref:System.Activities.CodeActivity>, ale te same funkcje można także wykonać przy użyciu działania <xref:System.Activities.Expressions.InvokeMethod%601>. Działanie <xref:System.Activities.Expressions.InvokeMethod%601> umożliwia autorom przepływu pracy wywoływanie metod statycznych i wystąpień klasy, a także opcję wywołania określonej metody asynchronicznie. W poniższym przykładzie działanie <xref:System.Activities.Expressions.InvokeMethod%601> jest skonfigurowane do wywoływania metody <xref:System.Net.WebClient.DownloadString%2A> klasy <xref:System.Net.WebClient> i zwracania listy klientów.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> może wywoływać zarówno metody statyczne, jak i wystąpienia klasy. Ponieważ <xref:System.Net.WebClient.DownloadString%2A> jest metodą wystąpienia klasy <xref:System.Net.WebClient>, dla <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>określono nowe wystąpienie klasy <xref:System.Net.WebClient>. `DownloadString` jest określony jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identyfikator URI, który zawiera zapytanie, jest określony w kolekcji <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A>, a wartość zwracana jest przypisywana do wartości <xref:System.Activities.Activity%601.Result%2A>. Wartość <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> jest ustawiona na `true`, co oznacza, że wywołanie metody zostanie uruchomione asynchronicznie w odniesieniu do przepływu pracy. W poniższym przykładzie zostanie skonstruowany przepływ pracy, który używa działania <xref:System.Activities.Expressions.InvokeMethod%601>, aby wykonać zapytanie dotyczące przykładowej usługi danych Northwind o listę zamówień dla określonego klienta, a następnie zwrócone dane są zapisywane w konsoli programu.

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

Ten przykład zawiera jedną metodę, która może być używana przez autorów aplikacji przepływu pracy do korzystania z danych pierwotnych zwróconych z usługi OData. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do Usługi danych programu WCF przy użyciu identyfikatorów URI, zobacz [Uzyskiwanie dostępu do zasobów usługi Data Service (usługi danych programu WCF) i protokołu](../data/wcf/accessing-data-service-resources-wcf-data-services.md) [OData: URI](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).
