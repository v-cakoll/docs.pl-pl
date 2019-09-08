---
title: Uzyskiwanie dostępu do zasobów usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: eff8d682004bf437a9b5470a4eb91c9bd52bfad5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791324"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Uzyskiwanie dostępu do zasobów usługi danych (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)][!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] program umożliwia udostępnianie danych w postaci kanału informacyjnego z zasobami, które są adresowane przez identyfikatory URI. Te zasoby są reprezentowane zgodnie z konwencjami relacji jednostek [Entity Data Model](../adonet/entity-data-model.md). W tym modelu jednostki reprezentują jednostki operacyjne danych, które są typami danych w domenie aplikacji, takie jak klienci, zamówienia, elementy i produkty. Dostęp do danych jednostki jest uzyskiwany i zmieniany przy użyciu semantyki przenoszonego transferu Stanów (REST), w tym standardowych czasowników HTTP GET, PUT, POST i DELETE.  
  
## <a name="addressing-resources"></a>Adresowanie zasobów  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]programie można rozwiązać wszystkie dane udostępniane przez model danych przy użyciu identyfikatora URI. Na przykład następujący identyfikator URI zwraca źródło, które jest zestawem jednostek Customers, który zawiera wpisy dla wszystkich wystąpień typu jednostki klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Jednostki mają specjalne właściwości o nazwie klucze jednostek. Klucz jednostki służy do jednoznacznej identyfikacji pojedynczej jednostki w zestawie jednostek. Pozwala to na rozwiązanie określonego wystąpienia typu jednostki w zestawie jednostek. Na przykład następujący identyfikator URI zwraca wpis dla określonego wystąpienia typu jednostki klienta, który ma kluczową wartość `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Pierwotne i złożone właściwości wystąpienia jednostki mogą również być adresowane indywidualnie. Na przykład następujący identyfikator URI zwraca element XML, który zawiera `ContactName` wartość właściwości dla określonego klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Po dołączeniu `$value` punktu końcowego do poprzedniego identyfikatora URI w komunikacie odpowiedzi jest zwracana tylko wartość właściwości pierwotnej. Poniższy przykład zwraca tylko ciąg "Maria Anders" bez elementu XML:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Relacje między jednostkami są zdefiniowane w modelu danych przez skojarzenia. Te skojarzenia umożliwiają adresowanie powiązanych jednostek przy użyciu właściwości nawigacji wystąpienia jednostki. Właściwość nawigacji może zwracać pojedynczą powiązaną jednostkę, w przypadku relacji wiele-do-jednego, lub zestaw powiązanych jednostek, w przypadku relacji jeden-do-wielu. Na przykład następujący identyfikator URI zwraca źródło danych będące zbiorem wszystkich zamówień związanych z określonym klientem:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Relacje, które są zwykle dwukierunkowe, są reprezentowane przez parę właściwości nawigacji. W przypadku odwrócenia relacji pokazanej w poprzednim przykładzie następujący identyfikator URI zwraca odwołanie do jednostki klienta, do której należy określona jednostka zamówienia:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]umożliwia również adresowanie zasobów na podstawie wyników wyrażeń zapytań. Dzięki temu możliwe jest filtrowanie zestawów zasobów na podstawie obliczonego wyrażenia. Na przykład następujący identyfikator URI filtruje zasoby, aby zwracały tylko zamówienia dla określonego klienta, które zostały dostarczone od 22 września 1997:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Aby uzyskać więcej informacji, [zobacz OData: Konwencje](https://go.microsoft.com/fwlink/?LinkId=185564)identyfikatora URI.  
  
## <a name="system-query-options"></a>Opcje zapytania systemowego  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje zestaw opcji zapytania systemowego, których można użyć do wykonywania tradycyjnych operacji zapytania względem zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład następujący identyfikator URI zwraca zestaw wszystkich `Order` jednostek, wraz z powiązanymi `Order_Detail` jednostkami, kody pocztowe, dla których nie kończy się `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Wpisy w zwracanym kanale informacyjnym są również uporządkowane według wartości właściwości ShipCity zamówień.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Program obsługuje następujące [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] opcje zapytania systemowego:  
  
|Opcja zapytania|Opis|  
|------------------|-----------------|  
|`$orderby`|Definiuje domyślną kolejność sortowania dla jednostek w zwróconym kanale informacyjnym. Następujące zapytania umożliwiają zlecenie zwrotów zwróconych odbiorców według powiatu i miasta:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Opcja kwerendy systemowej OrderBy ($orderby](https://go.microsoft.com/fwlink/?LinkId=186968)).|  
|`$top`|Określa liczbę jednostek do uwzględnienia w zwracanym źródle danych. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca następnych 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Opcja zapytania z największą krawędzią systemu](https://go.microsoft.com/fwlink/?LinkId=186969)($Top).|  
|`$skip`|Określa liczbę jednostek do pominięcia przed rozpoczęciem zwracania jednostek w kanale informacyjnym. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca następnych 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Pomiń opcję kwerendy systemowej ($skip](https://go.microsoft.com/fwlink/?LinkId=186971)).|  
|`$filter`|Definiuje wyrażenie filtrujące jednostki zwracane w kanale informacyjnym na podstawie określonych kryteriów. Ta opcja zapytania obsługuje zestaw logicznych operatorów porównania, operatorów arytmetycznych i wstępnie zdefiniowanych funkcji zapytań, które są używane do obliczania wyrażenia filtru. Poniższy przykład zwraca wszystkie zamówienia kodów pocztowych, których nie kończy się w 100:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Opcja filtrowania systemu ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Określa, które powiązane jednostki są zwracane przez zapytanie. Powiązane jednostki są dołączone jako źródło danych lub wpis w postaci wbudowanej do jednostki zwróconej przez zapytanie. Poniższy przykład zwraca kolejność dla klienta "ALFKI" oraz szczegóły elementu dla każdego zamówienia:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Rozwiń opcję kwerendy systemowej ($expand](https://go.microsoft.com/fwlink/?LinkId=186973)).|  
|`$select`|Określa projekcję definiującą właściwości jednostki, które są zwracane w projekcji. Domyślnie wszystkie właściwości jednostki są zwracane w kanale informacyjnym. Następujące zapytanie zwraca tylko trzy właściwości `Customer` jednostki:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Aby uzyskać więcej informacji, [zobacz OData: Wybierz opcję kwerendy systemowej ($select](https://go.microsoft.com/fwlink/?LinkID=186076)).|  
|`$inlinecount`|Żąda dołączenia liczby jednostek zwracanych w strumieniu informacyjnym do źródła danych. Aby uzyskać więcej informacji, [zobacz OData: Opcja zapytania systemu inlinecount ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>Relacje adresów  
 Oprócz zestawów jednostek i wystąpień jednostek, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] można również rozwiązać skojarzenia, które reprezentują relacje między jednostkami. Ta funkcja jest wymagana, aby można było utworzyć lub zmienić relację między dwoma wystąpieniami jednostek, takimi jak spedytor, który jest powiązany z daną kolejnością w przykładowej bazie danych Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]`$link` obsługuje operator w celu uzyskania szczegółowych adresów między jednostkami. Na przykład następujący identyfikator URI jest określony w komunikacie żądania HTTP PUT, aby zmienić spedytora dla określonej kolejności dla nowego nadawcy.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Aby uzyskać więcej informacji, [zobacz OData: Adresowanie linków między](https://go.microsoft.com/fwlink/?LinkId=187351)wpisami.  
  
## <a name="consuming-the-returned-feed"></a>Zużywanie zwróconego kanału informacyjnego  
 Identyfikator URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zasobu umożliwia adresowanie danych jednostki udostępnianych przez usługę. Po wprowadzeniu identyfikatora URI w polu adres przeglądarki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sieci Web zwracana jest reprezentacja kanału informacyjnego żądanego zasobu. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md). Mimo że przeglądarka sieci Web może być przydatna do testowania, że zasób usługi danych zwraca oczekiwane dane, usługi danych produkcyjnych, które mogą również tworzyć, aktualizować i usuwać dane, są zwykle używane przez kod aplikacji lub języki skryptów na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi danych w aplikacji klienckiej](using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Otwórz witrynę sieci Web protokołu Data Protocol](https://go.microsoft.com/fwlink/?LinkID=182204)
