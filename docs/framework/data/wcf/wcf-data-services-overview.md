---
title: Przegląd Usługi danych programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 66dd61210e36210f5444eb05355612eeb75c155a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790242"
---
# <a name="wcf-data-services-overview"></a>Przegląd Usługi danych programu WCF
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia tworzenie i wykorzystywanie usług danych dla sieci Web lub intranet przy użyciu [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]umożliwia uwidocznienie danych jako zasobów, które są adresowane przez identyfikatory URI. Dzięki temu można uzyskać dostęp do danych i zmienić je przy użyciu semantyki przenoszonego transferu stanu (REST), w tym standardowych czasowników HTTP funkcji GET, PUT, POST i DELETE. Ten temat zawiera omówienie wzorców i praktyk zdefiniowanych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] program, a także udogodnienia zapewniane przez program, dzięki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] którym można [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] korzystać z aplikacji opartych na .NET Framework.  
  
## <a name="address-data-as-resources"></a>Adresowanie danych jako zasobów  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. Ścieżki zasobów są konstruowane na podstawie Konwencji relacji jednostek Entity Data Model. W tym modelu jednostki reprezentują jednostki operacyjne danych w domenie aplikacji, takie jak klienci, zamówienia, elementy i produkty. Aby uzyskać więcej informacji, zobacz [Entity Data Model](../adonet/entity-data-model.md).  
  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]programie adresowanie zasobów jednostki jako zestawu jednostek, który zawiera wystąpienia typów jednostek. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` zwraca wszystkie zamówienia `Northwind` z usługi danych, które są powiązane z klientem z `CustomerID` wartością`ALFKI.`  
  
 Wyrażenia zapytań umożliwiają wykonywanie tradycyjnych operacji zapytań względem zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtruje zasoby, aby zwracały tylko zamówienia z kosztem frachtu większym niż $50. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do zasobów usługi danych](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Dostęp do danych międzyoperacyjnych  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Program korzysta z standardowych protokołów internetowych, aby zapewnić, że usługi danych współdziałają z aplikacjami, które nie używają .NET Framework. Ze względu na to, że można używać standardowych identyfikatorów URI do adresowania danych, aplikacja może uzyskiwać dostęp do danych i zmieniać je przy użyciu semantyki przenoszonego transferu Stanów (REST), w tym standardowych zleceń HTTP funkcji GET, PUT, POST i DELETE. Dzięki temu można uzyskać dostęp do tych usług z dowolnego klienta, który może analizować dane przesyłane za pośrednictwem standardowych protokołów HTTP i uzyskiwać do nich dostęp.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje zestaw rozszerzeń protokołu publikowania Atom (AtomPub). Obsługuje żądania HTTP i odpowiedzi w więcej niż jednym formacie danych w celu uwzględnienia różnych aplikacji klienckich i platform. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Źródło danych może reprezentować dane w formacie Atom, JavaScript Object Notation (JSON) i jako zwykły kod XML. Gdy Atom jest formatem domyślnym, format kanału informacyjnego jest określony w nagłówku żądania HTTP. Aby uzyskać więcej informacji, [zobacz OData: Format](https://go.microsoft.com/fwlink/?LinkID=185794) Atom i [OData: Format](https://go.microsoft.com/fwlink/?LinkID=185795)json.  
  
 Gdy publikujesz dane jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródło danych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , opierają się na innych istniejących obiektach internetowych na potrzeby takich operacji jak buforowanie i uwierzytelnianie. Aby to osiągnąć, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z istniejącymi aplikacjami hostingu i usługami, takimi jak ASP.NET, Windows Communication Foundation (WCF) i Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Niezależność magazynu  
 Mimo że zasoby są rozkierowane na podstawie modelu relacji jednostki, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] uwidaczniaj [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych bez względu na bazowe źródło. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zaakceptowaniu żądania HTTP dla zasobu identyfikowanego przez identyfikator URI żądanie jest deserializowane i reprezentacja tego żądania jest przesyłana [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do dostawcy. Ten dostawca tłumaczy żądanie na format specyficzny dla źródła danych i wykonuje żądanie na źródłowym źródle danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zapewnia niezależność przestrzeni dyskowej, oddzielając model koncepcyjny, który dotyczy zasobów [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] wymaganych przez z określonego schematu bazowego źródła danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]integruje się z ADO.NET Entity Framework, aby umożliwić tworzenie usług danych, które uwidaczniają dane relacyjne. Za pomocą narzędzi Entity Data Model można utworzyć model danych, który zawiera zasoby adresowane jako jednostki i w tym samym czasie definiują mapowanie między tym modelem i tabelami w źródłowej bazie danych. Aby uzyskać więcej informacji, zobacz [Entity Framework Provider](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia także tworzenie usług danych, które uwidaczniają wszystkie struktury danych, które zwracają implementację <xref:System.Linq.IQueryable%601> interfejsu. Dzięki temu można tworzyć usługi danych, które uwidaczniają dane z typów .NET Framework. Operacje tworzenia, aktualizowania i usuwania są obsługiwane w <xref:System.Data.Services.IUpdatable> przypadku zaimplementowania interfejsu. Aby uzyskać więcej informacji, zobacz temat [dostawca odbicia](reflection-provider-wcf-data-services.md).  
  
 Aby zapoznać się z ilustracją [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integracji z tymi dostawcami danych, zobacz diagram architektoniczny w dalszej części tego tematu.  
  
## <a name="custom-business-logic"></a>Niestandardowa logika biznesowa  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ułatwia dodawanie niestandardowych logiki biznesowej do usługi danych za pomocą operacji usługi i przechwycenia. Operacje usługi to metody zdefiniowane na serwerze, które są adresowane przez identyfikatory URI w tym samym formularzu co zasoby danych. Operacje usługi mogą również używać składni wyrażeń zapytania do filtrowania, porządkowania i danych stronicowych zwracanych przez operację. Na przykład identyfikator URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` reprezentuje wywołanie operacji usługi o nazwie `GetOrdersByCity` w usłudze danych Northwind, która zwraca zamówienia dla klientów z Londyn, z wynikami stronicowanymi posortowanymi według `OrderDate`. Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).  
  
 Interceptory umożliwiają integrację niestandardowej logiki aplikacji w przetwarzaniu komunikatów żądania lub odpowiedzi przez usługę danych. Interceptory są wywoływane, gdy w określonym zestawie jednostek występuje akcja zapytania, wstawiania, aktualizacji lub usuwania. Interceptor może zmienić dane, wymusić zasady autoryzacji lub nawet przerwać operację. Metody przechwytywania muszą być jawnie zarejestrowane dla danego zestawu jednostek, który jest udostępniany przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Biblioteki klienckie  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje zestaw jednolitych wzorców do współpracy z usługami danych. Zapewnia to możliwość tworzenia składników wielokrotnego użytku, które są oparte na tych usługach, takich jak biblioteki po stronie klienta, które ułatwiają korzystanie z usług danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera biblioteki klienckie zarówno dla aplikacji klienckich opartych na .NET Framework, jak i Silverlight. Te biblioteki klienckie umożliwiają współpracę z usługami danych przy użyciu obiektów .NET Framework. Obsługują one również zapytania oparte na obiektach i zapytania LINQ, ładujące powiązane obiekty, śledzenie zmian i rozpoznawanie tożsamości. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF Biblioteka kliencka](wcf-data-services-client-library.md).  
  
 Oprócz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bibliotek klienckich dołączonych do .NET Framework i programu Silverlight istnieją inne biblioteki klienckie, które umożliwiają [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] korzystanie z kanału informacyjnego w aplikacjach klienckich, takich jak aplikacje PHP, AJAX i Java. Aby uzyskać więcej informacji, zobacz [zestaw SDK OData](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Omówienie architektury  
 Na poniższym diagramie przedstawiono [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architekturę udostępniania [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanałów informacyjnych i korzystania z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]tych źródeł:  
  
 ![Zrzut ekranu przedstawiający diagram architektury Usługi danych programu WCF.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Zobacz także

- [Usługi danych WCF 4.5](index.md)
- [Wprowadzenie](getting-started-with-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Uzyskiwanie dostępu do zasobów usługi danych (Usługi danych programu WCF)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Przenoszenie stanu reprezentacji (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
