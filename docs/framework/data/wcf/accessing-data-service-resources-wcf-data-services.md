---
title: Dostęp do danych usługi zasobów (usługi danych WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: f1af991d7db9bfeeb0737e65a0517629f359f4a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365332"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Dostęp do danych usługi zasobów (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do udostępnienia danych jako źródło danych z zasobami, które są adresowane przez identyfikator URI. Te zasoby są reprezentowane zgodnie z Konwencją Relacja jednostki z [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md). W tym modelu jednostki reprezentują operacyjne moduły danych, które są typy danych w domenie aplikacji, takich jak klienci, zamówienia, elementy i produktów. Jednostki dane są dostępne i zmieniać za pomocą semantyki representational stanu transfer (REST), w szczególności standardowa zleceń HTTP GET, PUT, POST i DELETE.  
  
## <a name="addressing-resources"></a>Adresowania zasobów  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adresów żadnych danych, udostępnione przez model danych za pomocą identyfikatora URI. Na przykład następujący identyfikator URI zwraca strumieniowe klientów zestawu jednostek, który zawiera wpisy dla wszystkich wystąpień typu jednostki klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Mają specjalne właściwości o nazwie kluczy jednostek. Klucz jednostki jest używany do jednoznacznego identyfikowania pojedynczej jednostki w zestawie jednostek. Dzięki temu można rozwiązać określonego wystąpienia typu jednostki w zestawie jednostek. Na przykład następujący identyfikator URI zwraca wpis dla określonego wystąpienia typu jednostki klienta, który ma wartość klucza `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Pierwotne i złożone właściwości wystąpienia jednostki można również uwzględnione pojedynczo. Na przykład następujący identyfikator URI zwraca element XML, który zawiera `ContactName` wartości właściwości dla określonego klienta:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Jeśli dołączysz `$value` punktu końcowego w poprzednim identyfikator URI, tylko wartość pierwotna właściwość jest zwracana w komunikacie odpowiedzi. Poniższy przykład zwraca tylko ciąg "Maria Anders" bez elementu XML:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Relacje między obiektami są definiowane w modelu danych przez skojarzenia. Te skojarzenia umożliwiają adresów powiązanych jednostek przy użyciu właściwości nawigacji wystąpienia jednostki. Właściwość nawigacji może zwrócić albo pojedynczy obiekt pokrewny, w przypadku relacji wiele do jednego lub zestawu jednostek pokrewnych, w przypadku relacji jeden do wielu. Na przykład następujący identyfikator URI zwraca strumieniowe to zestaw wszystkich zleceń, które są powiązane z określonym klientem:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Relacje, które są zazwyczaj dwukierunkowe, są reprezentowane przez pary właściwości nawigacji. Jako odwrotna relacji w poprzednim przykładzie następujący identyfikator URI zwraca odwołanie do jednostki odbiorcy, do którego należy do określonej jednostki kolejności:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] można również do adresowania zasobów na podstawie wyników wyrażenia zapytania. Umożliwia filtrowanie zestawy zasobów oparty na obliczane wyrażenie. Na przykład następujący identyfikator URI filtruje zasobów, aby zwrócić tylko zleceń dla określonego klienta, które zostały dostarczone od 22 września 1997:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Aby uzyskać więcej informacji, zobacz [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Opcje zapytania systemu  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definiuje zestaw opcji zapytania systemu, które służą do wykonywania operacji tradycyjnych zapytań względem zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład następujący identyfikator URI zwraca zestaw wszystkich `Order` jednostek oraz powiązanych `Order_Detail` jednostek kodów pocztowych, które nie kończą się na `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Wpisy w źródle danych zwróconych również są uporządkowane według wartości właściwości MiastoOdbiorcy zleceń.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje następujące [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] systemu opcje zapytania:  
  
|Opcji zapytania|Opis|  
|------------------|-----------------|  
|`$orderby`|Określa domyślną kolejność sortowania dla jednostek w źródle danych zwracanych. Następujące zapytanie porządkuje zwrócony klientów źródła danych przez województwo i Miasto:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcji zapytania OrderBy systemu ($orderby)](http://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Określa liczbę jednostek do uwzględnienia w źródle danych zwracanych. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca dalej 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcji zapytania Top systemu ($top)](http://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Określa liczbę jednostek, aby pominąć przed rozpoczęciem zwraca jednostek w źródle danych. Poniższy przykład pomija pierwszych 10 klientów, a następnie zwraca dalej 10:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcji zapytania Skip systemu ($skip)](http://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Określa wyrażenie, które filtry zwracane jednostki w źródle danych na podstawie określonych kryteriów. Tej opcji zapytania obsługuje zestaw operatorów logicznych, operatorów arytmetycznych i funkcje wstępnie zdefiniowanego zapytania, które są używane do analizowania wyrażenia filtru. Poniższy przykład zwraca wszystkie zamówienia kodów pocztowych, które nie kończą się na 100:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: opcja zapytania filtra systemu ($filter)](http://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Określa, które powiązanych jednostek są zwracane przez zapytanie. Powiązanych jednostek są dołączone jako źródło danych lub wpis wierszu jednostek zwróconych przez kwerendę. Poniższy przykład zwraca kolejności dla klienta "ALFKI" oraz szczegóły elementu dla każdego zlecenia:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: rozwiń węzeł systemu opcji zapytania ($expand)](http://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Określa projekcję, która definiuje właściwości jednostki są zwracane w projekcji. Domyślnie wszystkie właściwości obiektu są zwracane w źródło danych. Następujące zapytanie zwraca tylko trzy właściwości `Customer` jednostki:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Aby uzyskać więcej informacji, zobacz [OData: wybierz opcję zapytania systemu ($select)](http://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Żądania, że liczba Liczba zwróconych w źródle danych zostanie uwzględniona w źródle danych. Aby uzyskać więcej informacji, zobacz [OData: opcji zapytania Inlinecount systemu ($inlinecount)](http://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>Adresowanie relacji  
 Oprócz zestawów jednostek i wystąpień jednostek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] umożliwia także adresów powiązania, które reprezentują relacje między obiektami. Ta funkcja jest wymagana, aby można było utworzyć lub zmienić relacji między dwoma wystąpieniami jednostki, takich jak nadawca, powiązanej z podanej kolejności w bazie danych Northwind. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje `$link` operatora w szczególności adresu skojarzenia między jednostkami. Na przykład następujący identyfikator URI jest określony w komunikacie żądania HTTP PUT można zmienić nadawcy dla określonej kolejności na nowy nadawca.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Aby uzyskać więcej informacji, zobacz [OData: adresowania łącza między wpisami](http://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Wykorzystywanie zwrócony źródła danych  
 Identyfikator URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zasobów umożliwia adres jednostki danych udostępnianych przez usługę. Po wprowadzeniu identyfikatora URI do pola adresu przeglądarki sieci Web [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła reprezentację żądany zasób jest zwracany. Aby uzyskać więcej informacji, zobacz [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Mimo że przeglądarki sieci Web mogą być przydatne podczas testowania, że zasób usługi danych zwraca oczekiwanych danych, usług danych produkcyjnych, które również mogą tworzenia, aktualizacji i usuwania danych zwykle są używane przez kod aplikacji lub skryptów języków na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz witrynę sieci Web protokołu danych](http://go.microsoft.com/fwlink/?LinkID=182204)
