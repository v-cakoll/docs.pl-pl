---
title: Uzyskiwanie dostępu do zasobów usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: d4f4de1fa12418bd56f9680e5414bfe7dd0aa128
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586769"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Uzyskiwanie dostępu do zasobów usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] aby uwidocznić dane jako źródło danych z zasobami, które są adresowane przez identyfikatory URI. Te zasoby są reprezentowane zgodnie z konwencjami Relacja jednostki z [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md). W tym modelu jednostki reprezentują operacyjnej jednostek danych, które są typy danych w domenie aplikacji, takich jak klienci, zamówienia, elementy i produktów. Dane jednostki jest dostępne i zmienić przy użyciu semantyki REST representational state transfer (), w szczególności standardowych poleceń HTTP GET, PUT, POST i DELETE.  
  
## <a name="addressing-resources"></a>Adresowania zasobów  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], rozwiązać wszelkie dane udostępniane przez model danych za pomocą identyfikatora URI. Na przykład następujący identyfikator URI zwraca źródła danych, które jest zestaw jednostek klientów, która zawiera wpisy dla wszystkich wystąpień tego typu jednostki klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Jednostki mają specjalne właściwości o nazwie kluczy jednostek. Klucz jednostki jest używany do jednoznacznego identyfikowania pojedynczej jednostki w zestawie jednostek. Dzięki temu można rozwiązać konkretnego wystąpienia typu jednostki w zestawie jednostek. Na przykład, następujący identyfikator URI zwraca wpis dla konkretnego wystąpienia typu jednostki klienta, który ma wartość klucza `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Pierwotne i złożone właściwości wystąpienia jednostki można również uwzględnione indywidualnie. Na przykład następujący identyfikator URI zwróci element XML, który zawiera `ContactName` wartości właściwości dla konkretnego klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Jeśli dołączysz `$value` punktu końcowego w identyfikatorze URI poprzedniej, zwracana jest wartość tylko właściwość typu pierwotnego w komunikacie odpowiedzi. Poniższy przykład zwraca tylko ciąg "Maria Piotrowska" bez elementu XML:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Relacje między jednostkami są zdefiniowane w modelu danych przez skojarzenia. Skojarzenia te umożliwiają adresów powiązanymi jednostkami za pomocą właściwości nawigacji wystąpienia jednostki. Właściwość nawigacji wrócić albo jednej powiązanej jednostki, w przypadku relacji wiele do jednego lub zestaw powiązanych jednostek w przypadku relacji jeden do wielu. Na przykład następujący identyfikator URI zwraca źródła danych, które ustawiono wszystkie zamówienia, które są powiązane z określonym klientem:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Relacje, które są zazwyczaj dwukierunkowej, są reprezentowane przez parę właściwości nawigacji. Jako odwrotnej relacji w poprzednim przykładzie następujący identyfikator URI zwraca odwołanie do jednostki odbiorcy, do której należy określone jednostki zamówienia:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] można również do adresowania zasobów w oparciu o wyniki wyrażenia zapytania. Dzięki temu możliwe do filtrowania zestaw zasobów, w oparciu o obliczane wyrażenie. Na przykład następujący identyfikator URI z filtrów zasobów, aby zwrócić tylko zamówienia dla określonego klienta, które zostały wydane od 22 września 1997 r.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Aby uzyskać więcej informacji, zobacz [OData: identyfikator URI konwencje](https://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Opcje zapytań systemu  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definiuje zestaw Opcje zapytań systemu, które służy do wykonywania zapytań z tradycyjnym operacji dotyczących zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład, następujący identyfikator URI zwraca zestaw wszystkich `Order` jednostek oraz powiązanych `Order_Detail` jednostek, kody pocztowe, które nie kończą się na `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Wpisy w źródle danych zwracany również są uporządkowane według wartości właściwości ShipCity zamówień.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje następujące [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Opcje zapytań systemu:  
  
|Stosowanie opcji zapytania|Opis|  
|------------------|-----------------|  
|`$orderby`|Określa domyślną kolejność sortowania dla jednostek w zwróconego źródła danych. Następujące zapytanie zamówień klientów zwróconego źródła danych, Powiat i Miasto:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcji zapytania OrderBy systemu ($orderby)](https://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Określa liczbę jednostek, które mają zostać objęte zwróconego źródła danych. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca następny 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: stosowanie opcji zapytania Top systemu ($top)](https://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Określa liczbę jednostek do pominięcia przed rozpoczęciem do zwrócenia jednostki w źródle danych. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca następny 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcja zapytania Skip — System ($skip)](https://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Definiuje wyrażenie, które filtry zwracane jednostki w źródle danych na podstawie określonych kryteriów. Tej opcji zapytania obsługuje zestaw operatory logiczne, operatory arytmetyczne i funkcje wstępnie zdefiniowanego zapytania, które są używane do oceny wyrażenia filtru. Poniższy przykład zwraca wszystkie zamówienia, kody pocztowe, które nie kończą się na 100:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcja zapytania filtra systemu ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Określa, które z powiązanymi obiektami są zwracane przez zapytanie. Pokrewne jednostki są uwzględniane jako źródło danych lub wbudowany wpis z jednostką zwróconych przez zapytanie. Poniższy przykład zwraca zamówienia dla klienta "ALFKI" wraz ze szczegółami elementu dla każdego zamówienia:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: rozwiń węzeł systemu stosowanie opcji zapytania ($expand)](https://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Określa projekcji, która definiuje właściwości jednostki są zwracane w projekcji. Domyślnie wszystkie właściwości jednostki są zwracane w źródle danych. Następujące zapytanie zwraca tylko dla trzech właściwości `Customer` jednostki:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: wybierz opcję zapytania systemu ($select)](https://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Żądania, liczbę obiektów zwracanych w kanale informacyjnym zostanie uwzględniona w źródle danych. Aby uzyskać więcej informacji, zobacz [OData: stosowanie opcji zapytania Inlinecount systemu ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>Adresowanie relacji  
 Oprócz adresowania, zestawów encji i wystąpień jednostek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pozwala również na adres skojarzenia, które reprezentują relacje między jednostkami. Ta funkcja jest wymagany, aby można było utworzyć lub zmienić relację między dwoma wystąpieniami jednostki, takie jak nadawca, który jest powiązany z danym zamówienia w bazie danych Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje `$link` operator umożliwiającą specjalnie skojarzenia między jednostkami. Na przykład następujący identyfikator URI jest określony w komunikacie żądania HTTP PUT można zmienić shipper dla określonej kolejności na nowe shipper.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Aby uzyskać więcej informacji, zobacz [OData: adresowania łącza między wpisami](https://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Korzystanie z zwróconego źródła danych  
 Identyfikator URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zasobów umożliwia utworzenie adresu jednostki danych udostępnianych przez usługę. Po wprowadzeniu identyfikatora URI do pola adresu w przeglądarce sieci Web [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanału informacyjnego reprezentacja żądany zasób jest zwracany. Aby uzyskać więcej informacji, zobacz [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Mimo że przeglądarki sieci Web mogą być przydatne do testowania, że zasób usługi danych zwraca oczekiwanych danych, usług danych produkcyjnych, które również można utworzyć, aktualizowanie i usuwanie danych zazwyczaj są używane przez kod aplikacji lub skryptów języków na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz witrynę sieci Web protokołu danych](https://go.microsoft.com/fwlink/?LinkID=182204)
