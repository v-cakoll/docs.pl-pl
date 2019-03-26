---
title: Omówienie usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: b7e8d0842b705a2fc8897511e1b2e01441d9c6b9
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465844"
---
# <a name="wcf-data-services-overview"></a>Omówienie usług danych WCF
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia tworzenie i użycie usług data services dla sieci Web lub w sieci intranet przy użyciu [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Umożliwia udostępnianie danych jako zasoby, które są adresowane przez identyfikatory URI. Dzięki temu można uzyskać dostęp i zmian danych przy użyciu semantyki REST representational state transfer (), specjalnie standardowych poleceń HTTP z GET PUT, POST i usuwania. Ten temat zawiera omówienie wzorców i praktyk, zdefiniowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i również urządzeń, które są dostarczane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z zalet [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] w aplikacjach opartych na programie .NET Framework.  
  
## <a name="address-data-as-resources"></a>Dane adresów jako zasoby  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI. Ścieżki zasobu są konstruowane na podstawie na konwencjach Relacja jednostki w modelu Entity Data Model. W tym modelu jednostki reprezentują operacyjnej jednostek danych w domenie aplikacji, takich jak klienci, zamówienia, elementy i produktów. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adres jednostki zasoby jako zestaw jednostek, zawierającej wystąpienia typów jednostek. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` zwraca wszystkie zamówienia z `Northwind` usługi danych, które są związane z klientem za pomocą `CustomerID` wartość `ALFKI.`  
  
 Wyrażenia zapytania umożliwiają wykonywanie zapytań z tradycyjnym operacji dotyczących zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtry zasobów, aby zwrócić tylko zamówienia z kosztem Fracht więcej niż 50 USD. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Dostęp do danych międzyoperacyjnych  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] opiera się na standardowych protokołów internetowych, aby usługi danych współpracujący z aplikacji, które nie korzystają z programu .NET Framework. Ponieważ można użyć standardowego identyfikatorów URI danych adresów, mogą uzyskiwać dostęp do aplikacji i zmian danych przy użyciu semantyki REST representational state transfer (), specjalnie standardowych poleceń HTTP z GET PUT, POST i usuwania. Dzięki temu można uzyskać dostęp do tych usług z dowolnego klienta, który można analizować i dostęp do danych, które są przesyłane za pośrednictwem standardowych protokołów HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definiuje zestaw rozszerzeń protokołu publikowania Atom (AtomPub). Obsługuje żądania i odpowiedzi HTTP w więcej niż jeden format danych w celu uwzględnienia różnych platform i aplikacje klienckie. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Źródło danych może reprezentować danych w Atom, JavaScript Object Notation (JSON) oraz jako zwykłego kodu XML. Atom jest domyślny format, format źródła danych jest określony w nagłówku żądania HTTP. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](https://go.microsoft.com/fwlink/?LinkID=185794) i [OData: JSON Format](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Podczas publikowania danych jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanału informacyjnego, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zależy od innych istniejących urządzeń Internetu dla tych operacji oraz buforowania uwierzytelniania. Aby to osiągnąć, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z istniejących hostowanie aplikacji i usług, takich jak ASP.NET, Windows Communication Foundation (WCF) i Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Niezależność od magazynu  
 Mimo że zasoby zostały rozwiązane w oparciu o model Relacja jednostki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ujawnić [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych, niezależnie od tego, w źródle danych. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] akceptuje żądania HTTP dla zasobu, który określa identyfikator URI żądania jest przeprowadzona i reprezentację to żądanie jest przekazywane do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostawcy. Ten dostawca tłumaczy żądania na format specyficznymi dla źródła danych i wykonuje żądanie na źródle danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] osiąga niezależność od magazynu, oddzielając modelu koncepcyjnego, odnoszący się do zasobów z zaleceniami [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z określonego schematu źródła danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z ADO.NET Entity Framework umożliwia tworzenie usług danych, które uwidaczniają opartego na danych relacyjnych. Narzędzia modelu Entity Data Model można utworzyć modelu danych, która zawiera zasoby mogą być adresowane jako jednostki, a w tym samym czasie zdefiniować mapowanie między ten model i tabele w bazie danych. Aby uzyskać więcej informacji, zobacz [dostawcy Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia także tworzenie usług danych, które uwidaczniają wszelkich struktur danych, które zwracają implementację <xref:System.Linq.IQueryable%601> interfejsu. Pozwala na tworzenie usług danych, które uwidaczniają dane z typów programu .NET Framework. Tworzenie, aktualizacji i operacje usuwania są obsługiwane w przypadku także implementować <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawcy odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Ilustracja jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z tych dostawców danych Zobacz diagram architektury w dalszej części tego tematu.  
  
## <a name="custom-business-logic"></a>Niestandardowej logiki biznesowej  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ułatwia dodawanie niestandardowej logiki biznesowej do usługi danych za pośrednictwem operacji usługi i interceptory. Operacje usługi są metody zdefiniowane na serwerze, które są adresowane przez identyfikatory URI w tym samym formularzu jako zasobów danych. Operacje usługi można również użyć składni wyrażeń zapytania filtru, kolejności i dane strony zwrócony przez operację. Na przykład identyfikator URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` reprezentuje wywołanie do operacji usługi o nazwie `GetOrdersByCity` na Usługa danych Northwind zwraca zamówienia dla klientów z Londynu, za pomocą stronicowane wyniki posortowane według `OrderDate`. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Interceptory umożliwiają niestandardowej logiki aplikacji powinny zostać włączone w czasie przetwarzania komunikatów żądania lub odpowiedzi przez usługę danych. Interceptory są wywoływane, gdy zapytania, wstawiania, aktualizacji lub Akcja usuwania występuje w zestawie określonej jednostki. Interceptor, a następnie mogą zmieniać dane, wymusić zasady autoryzacji lub nawet zakończyć operację. Metody interceptor musi być jawnie zarejestrowany dla danego zestawu jednostek udostępnianego przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Biblioteki klienckie  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Definiuje zbiór jednolitych wzorców do interakcji z usługami danych. Dzięki temu można tworzyć składniki wielokrotnego użytku, które są oparte na tych usług, takich jak biblioteki po stronie klienta, które ułatwiają korzystanie z usług danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zawiera biblioteki klienckie dla obu aplikacji klienckich opartych na programie .NET Framework i opartych na technologii Silverlight. Tych bibliotek klienckich umożliwiają interakcję z usługami danych przy użyciu obiektów .NET Framework. Obsługują one również zapytania w oparciu o obiekt i zapytań LINQ, trwa ładowanie powiązanych obiektów do śledzenia zmian i rozwiązanie tożsamości. Aby uzyskać więcej informacji, zobacz [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Oprócz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bibliotek klienckich, które są uwzględnione w środowisku .NET Framework i z technologią Silverlight, istnieją inne bibliotek klienckich, które umożliwiają używanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w aplikacjach klienckich, takich jak aplikacje PHP, technologii AJAX i Java. Aby uzyskać więcej informacji, zobacz [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Omówienie architektury  
 Na poniższym diagramie przedstawiono [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architektury udostępnianie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła i przy użyciu tych źródeł danych w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— włączone bibliotek klienta:  
  
 ![Zrzut ekranu przedstawiający diagram architektury WCF Data Services.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Zobacz także
- [Usługi danych WCF 4.5](../../../../docs/framework/data/wcf/index.md)
- [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Uzyskiwanie dostępu do zasobów usługi danych (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
