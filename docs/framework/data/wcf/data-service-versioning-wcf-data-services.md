---
title: "Przechowywanie wersji usługi danych (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 824abc79ae8d7ddd36b907977057a659aca86f20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-service-versioning-wcf-data-services"></a>Przechowywanie wersji usługi danych (usługi danych WCF)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Umożliwia tworzenie usług danych, dzięki czemu klienci mają dostęp do danych jako zasoby przy użyciu identyfikatorów URI, które są oparte na modelu danych. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]obsługuje również definicji operacji usługi. Po początkowym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia tych usług danych może być konieczne zostanie zmieniony z różnych powodów, takich jak zmieniające się potrzeby biznesowe, wymagania dotyczące technologii informacji, lub w celu rozwiązania innych problemów. Po wprowadzeniu zmian w istniejącej usłudze danych, należy rozważyć możliwość definiowania nowej wersji danych usługi i jak najlepiej zminimalizować wpływ na istniejące aplikacje klienckie. W tym temacie znajdują się wskazówki dotyczące kiedy i jak utworzyć nową wersję usługi danych. Opisano również sposób [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje wymiany między klientami a usług danych, które obsługują różne wersje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu.  
  
## <a name="versioning-a-wcf-data-service"></a>Przechowywanie wersji usługi danych WCF  
 Po wdrożeniu usługi danych i używania danych, zmiany w usłudze danych ma może spowodować problemy ze zgodnością z istniejącymi aplikacjami klienta. Jednak ponieważ ogólną potrzeb usługi często wymaga zmiany, należy rozważyć kiedy i jak utworzyć nową wersję usługi danych z najmniejszy wpływ na kliencie aplikacji.  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Zmiany modelu danych, które zalecane jest nowa wersja usługi danych  
 Podczas określania, czy publikować nową wersję usługi danych, ważne jest zrozumienie, jak różnego rodzaju zmiany mogą wpłynąć na aplikacje klienckie. Zmiany w usłudze danych, która może wymagać utworzyć nową wersję usługi danych można podzielić na następujące dwie kategorie:  
  
-   Zmienia się na kontrakt usługi, które obejmują aktualizacje do operacji usługi, zmiany w dostępności zestawów jednostek (źródła danych), zmiany wersji i inne zmiany zachowania usługi.  
  
-   Zmienia się na kontrakt danych, które uwzględnienia zmian w modelu danych, źródła danych formatów lub źródła danych dostosowania.  
  
 Szczegóły tabeli następujące rodzaje zmian, które należy rozważyć publikowanie nowa wersja usługi danych:  
  
|Typ zmiany|Wymaga nowej wersji|Nowa wersja nie jest wymagane|  
|--------------------|----------------------------|----------------------------|  
|Operacje usługi|-Dodaj nowy parametr<br />— Zmień typ zwracany<br />-Usuń operacji usługi|— Usunięcie istniejących parametrów<br />-Dodaj nowe operacji usługi|  
|Zachowania usług|— Wyłączanie liczba żądań<br />-Wyłączyć obsługę projekcji<br />-Zwiększ numer wersji usługi danych|-Włącz liczba żądań<br />-Włącz obsługę projekcji<br />-Zmniejsz wersja usługi danych|  
|Zestaw jednostek uprawnień|-Ograniczyć uprawnienia zestaw jednostek<br />-Zmień kod odpowiedzi (nowe pierwsza wartość cyfr) <sup>1</sup>|-Zmniejszą jednostki Ustawianie uprawnień<br />-Zmień kod odpowiedzi (tego samego pierwsza wartość cyfra)|  
|Właściwości jednostki|-Usuń istniejącą właściwość lub relacji<br />-Dodaj właściwości niedopuszczającej wartości null<br />-Zmień istniejącą właściwość|-Dodaj właściwość nullable<sup>2</sup>|  
|Zestawy jednostek|-Usuń zestaw jednostek|-Dodaj typu pochodnego<br />— Zmień typ podstawowy<br />-Dodaj zestaw jednostek|  
|Dostosowywanie źródła|-Zmień mapowanie właściwości jednostki||  
  
 <sup>1</sup> to może zależeć od jak ściśle aplikacji klienckiej opiera się na odbieranie określonego kodu błędu.  
  
 <sup>2</sup> można ustawić <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwości `true` aby klienci Ignoruj wszystkie nowe właściwości wysłanych przez usługę danych, które nie są zdefiniowane na kliencie. Podczas operacji wstawiania, nieuwzględnionych przez klienta w żądaniu POST właściwości są ustawione wartości domyślne. W przypadku aktualizacji istniejących danych we właściwości nieznany do klienta mogą zostać zastąpione wartościami domyślnymi. W takim przypadku należy wysłać aktualizacji, jak żądanie scalania, która jest ustawiona domyślnie. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontekstu danych usługi](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
### <a name="how-to-version-a-data-service"></a>Jak wersja usługi danych  
 Gdy jest to wymagane, nowa wersja usługi danych jest definiowany przez tworzenie nowego wystąpienia usługi z modelem danych lub kontrakt zaktualizowany. Nowej usługi jest następnie udostępniany przy użyciu nowego identyfikatora URI punktu końcowego, który odróżnia go od poprzedniej wersji. Na przykład:  
  
-   Stara wersja:`http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   Nowa wersja:`http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 Podczas uaktualniania usług danych, klienci muszą również zostać zaktualizowany oparte na nowe metadane usługi danych i chcesz użyć nowego katalogu głównego identyfikatora URI. Jeśli to możliwe, należy zachować poprzedniej wersji usługi danych do obsługi klientów, które nie zostały jeszcze uaktualnione do nowej wersji. Można usunąć starszej wersji usługi danych, gdy są już potrzebne. Warto rozważyć zachowanie punktu końcowego usługi danych identyfikatora URI w pliku konfiguracyjnym zewnętrznych.  
  
## <a name="odata-protocol-versions"></a>Wersji protokołu OData  
 Jako nowe wersje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zostały zwolnione, aplikacje klienckie mogą nie używać tę samą wersję programu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu, który jest obsługiwany przez usługę danych. Starszych aplikacji klient może uzyskać dostępu do obsługującego nowsza wersja usługi danych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Aplikacja kliencka również używając nowszej wersji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, która obsługuje nowsza wersja [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] niż Usługa danych, który jest dostępny.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]wykorzystuje pomocy technicznej [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do obsługi takich scenariuszy kontroli wersji. Jest również Obsługa generowania i przy użyciu metadanych modelu danych do tworzenia klas usługi danych klienta, jeśli klient używa innej wersji [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] niż Usługa danych używa. Aby uzyskać więcej informacji, zobacz [OData: przechowywanie wersji protokołu](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
### <a name="version-negotiation"></a>Negocjowanie wersji  
 Usługi danych można skonfigurować w celu zdefiniowania najwyższej wersji [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu, który będzie używany przez usługę, niezależnie od wersji żądanego przez klienta. Można to zrobić, określając <xref:System.Data.Services.Common.DataServiceProtocolVersion> wartość <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> właściwość <xref:System.Data.Services.DataServiceBehavior> używane przez usługę danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Jeśli aplikacja używa [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotek klienta do dostępu do danych usługi, biblioteki automatycznie ustawioną poprawnych wartości, w zależności od wersji tych nagłówków [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i funkcje, które są używane w aplikacji. Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używa Najniższa wersja protokołu, który obsługuje żądanej operacji.  
  
 W poniższej tabeli przedstawiono wersje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] i [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] zawierające [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługę określonych wersji [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu.  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Wersja protokołu|Obsługa wprowadzone w systemie...|  
|-----------------------------------------------------------------------------------|----------------------------|  
|W wersji 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Z dodatkiem Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]w wersji 3|  
|W wersji 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Aktualizacja [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] z dodatkiem SP1. Można pobrać i zainstalować aktualizację z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]w wersji 4|  
|W wersji 3|— Można pobrać i zainstalować wersję wstępną, która obsługuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] w wersji 3 z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=203885).|  
  
### <a name="metadata-versions"></a>Wersje metadanych  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używa wersji 1.1 CSDL reprezentujące model danych. Jest to zawsze w przypadku modeli danych, które są oparte na dostawcy odbicia lub dostawcy usług danych niestandardowych. Jednak gdy model danych jest definiowana za pomocą [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], wersja pliku CSDL zwracane jest taka sama jak wersja używanego przez [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. Wersja pliku CSDL jest określany przez obszar nazw [elementu schematu](http://msdn.microsoft.com/en-us/396074d8-f99c-4f50-a073-68bce848224f). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Specyfikacja [ \[MC CSDL\]: koncepcyjny formatu pliku definicji schematu](http://go.microsoft.com/fwlink/?LinkId=159072).  
  
 `DataServices` Zawiera również element metadane zwrócony `DataServiceVersion` atrybut, który ma taką samą wartość jak `DataServiceVersion` nagłówka w komunikacie odpowiedzi. Aplikacje klienckie, takie jak **Dodaj odwołanie do usługi** okno dialogowe w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], te informacje służą do generowania klasy usługi danych klienta, które działają poprawnie, wersja [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] który hosta usługi danych. Aby uzyskać więcej informacji, zobacz [OData: przechowywanie wersji protokołu](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
