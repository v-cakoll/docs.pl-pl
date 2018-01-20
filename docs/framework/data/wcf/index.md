---
title: "Usługi danych WCF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5b27a51dcec17f72b86e77a7ee2ab773aec1dc3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-data-services-45"></a>Usługi danych WCF 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)](wcześniej znane jako "Usług danych ADO.NET") jest składnikiem programu .NET Framework, która umożliwia tworzenie usług, które używają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do ujawnia i konsumowania danych za pośrednictwem sieci Web lub intranet przy użyciu semantykę [representational stanu Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919). [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]przedstawia dane w postaci zasobów, które są adresowane przez identyfikator URI. Dane są dostępne i zmieniać przy użyciu standardowych poleceń HTTP z GET, PUT, POST i DELETE. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]używa konwencji Relacja jednostki z [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) do udostępnienia zasobów jako zestawy jednostek, które są powiązane przez skojarzenia.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]używa [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu adresowania i aktualizowanie zasobów. W ten sposób można dostępu tych usług za pomocą dowolnego klienta, który obsługuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]pozwala na żądanie i zapisać dane do zasobów przy użyciu formatów transferowania dobrze znanego: Atom, zbiór standardów wymiany i aktualizowanie danych jako XML i JavaScript Object Notation (JSON), format wymiany danych tekstowych bardzo często używane w aplikacji interfejsu AJAX.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]można ujawniać dane, które pochodzą z różnych źródeł jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych. Program Visual Studio tools ułatwiają tworzenie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi przy użyciu modelu danych programu ADO.NET Entity Framework. Można również utworzyć [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych na podstawie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) klas i danych nawet późnym wiązaniem lub wyrażeniami bez typu.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera także zestaw bibliotek klienta, jedno dla aplikacji klienckich, ogólne .NET Framework i jedno specjalnie dla aplikacji opartych na technologii Silverlight. Te biblioteki klienta zapewniają model programowania obiektu, gdy uzyskujesz dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych ze środowisk, takich jak .NET Framework i Silverlight.  
  
## <a name="where-should-i-start"></a>Gdzie powinna zaczynać?  
 W zależności od zainteresowania, należy rozważyć wprowadzenie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] w następujących tematach.  
  
 Chcę, aby od razu...  
 -   [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Szybki start Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Szybki start Silverlight dla systemu Windows Phone programowanie](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 Po prostu Pokaż kodu...  
 -   [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 Chcę, aby dowiedzieć się więcej o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]...  
 -   [Oficjalny dokument: Wprowadzenie do OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Otwórz witrynę sieci Web protokołu danych](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: zestaw SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: Często zadawane pytania](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 Chcę obejrzeć wideo niektóre...  
 -   [Przewodnik dla początkujących do usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [Filmy wideo dewelopera usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData: Witryna sieci Web deweloperów](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 Aby wyświetlić przykłady end-to-end  
 -   [Przykłady dokumentacji w galerii przykładów MSDN usługi danych WCF](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [Inne WCF Data Services próbek w galerii przykładów MSDN](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData: zestaw SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Jak można je zintegrować z programem Visual Studio?  
 -   [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 Co można zrobić z nim?  
 -   [Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Oficjalny dokument: Wprowadzenie do OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Scenariusze aplikacji](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Chcę użyć Silverlight...  
 -   [Szybki start Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Wprowadzenie do programu Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Chcę utworzyć aplikację Windows Phone...  
 -   [Szybki start Silverlight dla systemu Windows Phone programowanie](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Open Data Protocol (OData) klienta dla Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 Chcę użyć LINQ...  
 -   [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [Zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 Wciąż potrzebuję więcej informacji...  
 -   [Blog zespołu usługi danych WCF](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Zasoby](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [Centrum deweloperów usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Otwórz witrynę sieci Web protokołu danych](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Zawiera omówienie funkcji i możliwości, które są dostępne w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [What's New in usługi danych WCF](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 Zawiera opis nowych funkcji w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] i obsługę nowych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcji.  
  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Opisuje sposób ujawniać i korzystanie z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 Opisuje sposób tworzenia i konfigurowania usługi danych, który ujawnia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych.  
  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 Informacje dotyczące używania bibliotek klienckich zużyje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł z aplikacją kliencką programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)
