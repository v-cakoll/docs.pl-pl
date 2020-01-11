---
title: Przegląd Usługi danych programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: a4121bb10de7bfe51c5fec6bc14a40ad4bdcdaf7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900890"
---
# <a name="wcf-data-services-overview"></a>Przegląd Usługi danych programu WCF
Usługi danych programu WCF umożliwia tworzenie i użycie usług danych dla sieci Web lub intranet przy użyciu protokołu Open Data Protocol (OData). Usługa OData umożliwia Uwidacznianie danych jako zasobów, które są adresowane przez identyfikatory URI. Dzięki temu można uzyskać dostęp do danych i zmienić je przy użyciu semantyki przenoszonego transferu stanu (REST), w tym standardowych czasowników HTTP funkcji GET, PUT, POST i DELETE. Ten temat zawiera omówienie wzorców i praktyk zdefiniowanych przez usługi OData, a także funkcje zapewniane przez Usługi danych programu WCF, aby korzystać z protokołu OData w aplikacjach opartych na .NET Framework.  
  
## <a name="address-data-as-resources"></a>Adresowanie danych jako zasobów  
 Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. Ścieżki zasobów są konstruowane na podstawie Konwencji relacji jednostek Entity Data Model. W tym modelu jednostki reprezentują jednostki operacyjne danych w domenie aplikacji, takie jak klienci, zamówienia, elementy i produkty. Aby uzyskać więcej informacji, zobacz [Entity Data Model](../adonet/entity-data-model.md).  
  
 W protokole OData zasoby jednostki są adresowane jako zestaw jednostek, który zawiera wystąpienia typów jednostek. Na przykład identyfikator URI <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders> zwraca wszystkie zamówienia z usługi danych `Northwind`, które są powiązane z klientem z wartością `CustomerID` `ALFKI.`  
  
 Wyrażenia zapytań umożliwiają wykonywanie tradycyjnych operacji zapytań względem zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład identyfikator URI <https://services.odata.org/Northwind/Northwind.svc/Customers("ALFKI")/Orders? $filter = fracht gt 50 > filtruje zasoby, aby zwracały tylko zamówienia z kosztem frachtu większym niż $50. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do zasobów usługi danych](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Dostęp do danych międzyoperacyjnych  
 Usługa OData kompiluje się w standardowych protokołach internetowych, aby zapewnić współdziałanie usług danych z aplikacjami, które nie używają .NET Framework. Ze względu na to, że można używać standardowych identyfikatorów URI do adresowania danych, aplikacja może uzyskiwać dostęp do danych i zmieniać je przy użyciu semantyki przenoszonego transferu Stanów (REST), w tym standardowych zleceń HTTP funkcji GET, PUT, POST i DELETE. Dzięki temu można uzyskać dostęp do tych usług z dowolnego klienta, który może analizować dane przesyłane za pośrednictwem standardowych protokołów HTTP i uzyskiwać do nich dostęp.  
  
Usługa OData definiuje zestaw rozszerzeń protokołu publikowania Atom (AtomPub). Obsługuje żądania HTTP i odpowiedzi w więcej niż jednym formacie danych w celu uwzględnienia różnych aplikacji klienckich i platform. Źródło danych OData może reprezentować dane w formacie Atom, JavaScript Object Notation (JSON) i jako zwykły kod XML. Gdy Atom jest formatem domyślnym, format kanału informacyjnego jest określony w nagłówku żądania HTTP. Aby uzyskać więcej informacji, zobacz Format [OData: Atom](https://www.odata.org/documentation/odata-version-2-0/atom-format/) i [OData: JSON](https://www.odata.org/documentation/odata-version-2-0/json-format/).  
  
 Gdy dane są publikowane jako źródło danych OData, Usługi danych programu WCF opiera się na innych istniejących obiektach internetowych na potrzeby takich operacji jak buforowanie i uwierzytelnianie. Aby to osiągnąć, Usługi danych programu WCF integruje się z istniejącymi aplikacjami hostingu i usługami, takimi jak ASP.NET, Windows Communication Foundation (WCF) i Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Niezależność magazynu  
 Mimo że zasoby są rozkierowane na podstawie modelu relacji jednostek, Usługi danych programu WCF uwidaczniaj źródła danych OData niezależnie od bazowego źródła. Gdy Usługi danych programu WCF akceptuje żądanie HTTP dla zasobu identyfikowanego przez identyfikator URI, żądanie jest deserializowane i reprezentacja tego żądania jest przesyłana do dostawcy Usługi danych programu WCF. Ten dostawca tłumaczy żądanie na format specyficzny dla źródła danych i wykonuje żądanie na źródłowym źródle danych. Usługi danych programu WCF zapewnia niezależność przestrzeni dyskowej przez oddzielenie modelu koncepcyjnego, który dotyczy zasobów wymaganych przez OData z określonego schematu bazowego źródła danych.  
  
 Usługi danych programu WCF integruje się z Entity Framework ADO.NET, aby umożliwić tworzenie usług danych, które uwidaczniają dane relacyjne. Za pomocą narzędzi Entity Data Model można utworzyć model danych, który zawiera zasoby adresowane jako jednostki i w tym samym czasie definiują mapowanie między tym modelem i tabelami w źródłowej bazie danych. Aby uzyskać więcej informacji, zobacz [Entity Framework Provider](entity-framework-provider-wcf-data-services.md).  
  
 Usługi danych programu WCF umożliwia również tworzenie usług danych, które uwidaczniają wszystkie struktury danych, które zwracają implementację interfejsu <xref:System.Linq.IQueryable%601>. Dzięki temu można tworzyć usługi danych, które uwidaczniają dane z typów .NET Framework. Operacje tworzenia, aktualizowania i usuwania są obsługiwane w przypadku zaimplementowania interfejsu <xref:System.Data.Services.IUpdatable>. Aby uzyskać więcej informacji, zobacz temat [dostawca odbicia](reflection-provider-wcf-data-services.md).  
  
 Aby zapoznać się z ilustracją, jak Usługi danych programu WCF integrują się z tymi dostawcami danych, zapoznaj się z diagramem architektury w dalszej części tego tematu.  
  
## <a name="custom-business-logic"></a>Niestandardowa logika biznesowa  
 Usługi danych programu WCF ułatwia dodawanie niestandardowych logiki biznesowej do usługi danych za pomocą operacji usługi i przechwycenia. Operacje usługi to metody zdefiniowane na serwerze, które są adresowane przez identyfikatory URI w tym samym formularzu co zasoby danych. Operacje usługi mogą również używać składni wyrażeń zapytania do filtrowania, porządkowania i danych stronicowych zwracanych przez operację. Na przykład identyfikator URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` reprezentuje wywołanie operacji usługi o nazwie `GetOrdersByCity` w usłudze danych Northwind, która zwraca zamówienia dla klientów z Londyn, z wynikami stronicowanymi posortowanymi przez `OrderDate`. Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).  
  
 Interceptory umożliwiają integrację niestandardowej logiki aplikacji w przetwarzaniu komunikatów żądania lub odpowiedzi przez usługę danych. Interceptory są wywoływane, gdy w określonym zestawie jednostek występuje akcja zapytania, wstawiania, aktualizacji lub usuwania. Interceptor może zmienić dane, wymusić zasady autoryzacji lub nawet przerwać operację. Metody przechwytywania muszą być jawnie zarejestrowane dla danego zestawu jednostek, który jest udostępniany przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Biblioteki klienckie  
 Usługa OData definiuje zestaw jednolitych wzorców do współpracy z usługami danych. Zapewnia to możliwość tworzenia składników wielokrotnego użytku, które są oparte na tych usługach, takich jak biblioteki po stronie klienta, które ułatwiają korzystanie z usług danych.  
  
 Usługi danych programu WCF obejmuje biblioteki klienckie zarówno dla aplikacji klienckich opartych na .NET Framework, jak i Silverlight. Te biblioteki klienckie umożliwiają współpracę z usługami danych przy użyciu obiektów .NET Framework. Obsługują one również zapytania oparte na obiektach i zapytania LINQ, ładujące powiązane obiekty, śledzenie zmian i rozpoznawanie tożsamości. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF Biblioteka kliencka](wcf-data-services-client-library.md).  
  
 Oprócz bibliotek klienckich OData zawartych w .NET Framework i z technologią Silverlight istnieją inne biblioteki klienckie umożliwiające korzystanie z kanału informacyjnego OData w aplikacjach klienckich, takich jak aplikacje PHP, AJAX i Java. Aby uzyskać więcej informacji na temat zestawu OData SDK, zobacz [kod przykładowy usługi OData SDK](https://www.odata.org/ecosystem/#sdk).
  
## <a name="architecture-overview"></a>Omówienie architektury  
 Na poniższym diagramie przedstawiono architekturę Usługi danych programu WCF do udostępniania źródeł danych OData i korzystania z tych źródeł w bibliotekach klienta z obsługą protokołu OData:  
  
 ![Zrzut ekranu przedstawiający diagram architektury Usługi danych programu WCF.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Zobacz także

- [Usługi danych WCF 4.5](index.md)
- [Wprowadzenie](getting-started-with-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Uzyskiwanie dostępu do zasobów usługi danych (Usługi danych programu WCF)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Przenoszenie stanu reprezentacji (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
