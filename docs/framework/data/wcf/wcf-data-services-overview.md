---
title: "Omówienie usług danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88d586ead18e4129707728733029c735083b477c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-overview"></a>Omówienie usług danych WCF
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia tworzenie i korzystania z usług danych sieci Web lub w sieci intranet przy użyciu [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Umożliwia udostępnianie danych jako zasoby, które są adresowane przez identyfikator URI. Dzięki temu można uzyskać dostęp i zmian danych przy użyciu semantyki representational stanu transfer (REST), w szczególności standardowe polecenia HTTP z GET PUT, POST i usuwania. Ten temat zawiera omówienie wzorców i rozwiązań zdefiniowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i również urządzenia, które są udostępniane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] przeprowadzać [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] w aplikacjach opartych na programie .NET Framework.  
  
## <a name="address-data-as-resources"></a>Dane adresów jako zasoby  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]przedstawia dane w postaci zasobów, które są adresowane przez identyfikator URI. Ścieżki zasobów są zbudowane oparte na Konwencji Relacja jednostki w modelu danych jednostki. W tym modelu jednostki reprezentują operacyjne jednostek danych w domenie aplikacji, takich jak klienci, zamówienia, elementy i produktów. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 W [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], adresów zasobów jednostki jako zestaw jednostek, który zawiera wystąpień typów jednostek. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` zwraca wszystkie zamówień z `Northwind` usługi danych, które są powiązane z klienta z `CustomerID` wartości`ALFKI.`  
  
 Wyrażenia zapytań umożliwiają wykonywanie operacji tradycyjnych zapytań względem zasobów, takich jak filtrowanie, sortowanie i stronicowanie. Na przykład identyfikator URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtruje zasoby do zwrócenia tylko zamówienia z kosztem transport więcej niż 50. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Dostęp do danych interoperacyjne  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Bazując na standardowych protokołach internetowych aby danych usługi współdziałanie z aplikacjami, które nie korzystają z programu .NET Framework. Ponieważ można używać standardowych identyfikatorów URI danych adresów, mogą uzyskiwać dostęp do aplikacji i zmian danych przy użyciu semantyki representational stanu transfer (REST), w szczególności standardowe polecenia HTTP z GET PUT, POST i usuwania. Umożliwia dostęp do tych usług z dowolnego klienta, który można analizować i uzyskać dostępu do danych są przesyłane za pośrednictwem standardowych protokołów HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje zestaw rozszerzeń protokołu publikowania Atom (AtomPub). Obsługuje żądania i odpowiedzi HTTP w więcej niż jeden format danych, aby zmieścił się w różnych platform i aplikacje klienckie. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Źródła danych może reprezentować danych Atom, JavaScript Object Notation (JSON), a jako zwykły kod XML. Atom jest domyślny format, format źródła danych jest określony w nagłówku żądania HTTP. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](http://go.microsoft.com/fwlink/?LinkID=185794) i [OData: JSON Format](http://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Podczas publikowania danych jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zależy od innych istniejących Internetu do działania, takie jak buforowanie i uwierzytelniania. Aby to osiągnąć, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z istniejącymi aplikacjami hostingu i usług, takich jak ASP.NET, usług Windows Communication Foundation (WCF) i usługi Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Niezależność magazynu  
 Mimo że zasoby są opisane na podstawie modelu Relacja jednostki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ujawnia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła niezależnie od tego źródła danych. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] akceptuje żądania HTTP dla zasobu, który identyfikuje identyfikator URI, żądanie jest deserializacji i reprezentacja tego żądania jest przekazywana do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostawcy. Ten dostawca przetwarza żądanie na format specyficzne dla źródła danych i wykonuje żądanie w źródle danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]osiąga niezależność magazynu oddzielając dotyczące zasobów określone w modelu koncepcyjnym [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] od określonego schematu źródła danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]integruje się z ADO.NET Entity Framework, aby umożliwić tworzenie usług danych, które udostępniają relacyjnej bazie danych. Narzędzia modelu Entity Data Model do tworzenia modelu danych, który zawiera zasoby mogą być adresowane jednostki i jednocześnie zdefiniować mapowanie między ten model i tabele w bazie danych. Aby uzyskać więcej informacji, zobacz [dostawcy programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia także tworzenie usług danych, które udostępniają żadnych struktury danych, które zwracają implementacja <xref:System.Linq.IQueryable%601> interfejsu. Dzięki temu można utworzyć usług danych, które udostępniają dane z typu .NET Framework. Tworzenia, aktualizacji i usuwania operacji są obsługiwane w przypadku także implementować <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawcy odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Ilustracja jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integruje się z tych dostawców danych Zobacz diagram architektury w dalszej części tego tematu.  
  
## <a name="custom-business-logic"></a>Niestandardowe reguły biznesowe  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]można łatwo dodać niestandardowe reguły biznesowe do usługi danych za pośrednictwem operacji usługi i interceptory. Operacje usług metodami zdefiniowanego na serwerze adresowane przez identyfikatory URI, w tym samym formularzu jako zasobów danych. Operacje usług można także użyć składni wyrażenia zapytania filtru, kolejności i dane strony zwrócony przez operację. Na przykład identyfikator URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` reprezentuje wywołania operacji usługi o nazwie `GetOrdersByCity` w usłudze danych Northwind zwraca zleceń dla klientów z Londynu, z stronicowanej wyniki posortowane według `OrderDate`. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Interceptory włączyć niestandardowej logiki aplikacji powinny zostać włączone do przetwarzania komunikatów żądania lub odpowiedzi przez usługę danych. Interceptory są wywoływane, gdy zapytanie, insert, update lub Akcja usuwania, która występuje na zestawie określonej jednostki. Interceptora, a następnie mogą zmieniać danych, wymuszać zasady autoryzacji lub nawet zakończyć operację. Metody interceptora musi być jawnie zarejestrowany dla danego zestawu jednostek udostępnianym przez usługi danych. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Biblioteki klienta  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definiuje zestaw wzorców uniform interakcji z usług danych. Zapewnia możliwość tworzenia składników wielokrotnego użytku, które są oparte na tych usług, takich jak biblioteki po stronie klienta, które ułatwiają korzystanie z usług danych.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera biblioteki klienta dla obu aplikacji klienckich opartych na programie .NET Framework i oparte na technologii Silverlight. Te biblioteki klienta umożliwiają interakcję z usług danych przy użyciu obiektów .NET Framework. Również obsługiwać zapytań na podstawie obiektu i zapytań LINQ, ładowanie powiązanych obiektów śledzenia zmian oraz rozpoznawania tożsamości. Aby uzyskać więcej informacji, zobacz [biblioteki klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Oprócz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] klienta biblioteki dołączony z programu .NET Framework i Silverlight, istnieją inne biblioteki klienta, które umożliwiają korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w aplikacjach klienckich, takich jak aplikacje PHP, AJAX i Java. Aby uzyskać więcej informacji, zobacz [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Przegląd architektury  
 Na poniższym diagramie przedstawiono [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architektura udostępnianie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła i przy użyciu tych źródeł danych w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— włączone bibliotek klienta:  
  
 ![Diagram architektury usługi danych WCF](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi danych WCF 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Definiowanie usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Uzyskiwanie dostępu do usługi danych (usługi danych WCF)](http://msdn.microsoft.com/en-us/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)
