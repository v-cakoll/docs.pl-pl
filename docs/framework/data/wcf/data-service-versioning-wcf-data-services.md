---
title: Przechowywanie wersji usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 9a92346267012d3651d04648b357bbf530097e34
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221574"
---
# <a name="data-service-versioning-wcf-data-services"></a>Przechowywanie wersji usługi danych (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Pozwala na tworzenie usług danych, dzięki czemu klienci mają dostęp do danych jako zasoby przy użyciu identyfikatorów URI, które są oparte na modelu danych. OData obsługuje również definicji operacji usługi. Po początkowym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia te usługi danych może być konieczne zostanie zmieniony z różnych powodów, takich jak zmieniających się potrzeb biznesowych, wymagań dotyczących technologii informacji, lub aby rozwiązać inne problemy. Po wprowadzeniu zmian do istniejącej usługi danych należy rozważyć czy należy zdefiniować nową wersję usługi danych usługi i najlepszy sposób zminimalizować wpływ na istniejące aplikacje klienckie. W tym temacie znajdują się wskazówki dotyczące kiedy i jak utworzyć nową wersję usługi danych. Opisano również, jak usługi danych WCF obsługuje wymiany między klientami i usług danych, które obsługują różne wersje protokołu OData.

## <a name="versioning-a-wcf-data-service"></a>Przechowywanie wersji usługi danych WCF
 Po wdrożeniu usługi danych i używania danych, zmiany do usługi danych zostały potencjalnie powodować problemy ze zgodnością przy użyciu istniejących aplikacji klienckich. Jednak ponieważ często wymaga zmiany potrzeb biznesowych ogólnej usługi, należy rozważyć kiedy i jak utworzyć nową wersję usługi danych z najmniejszy wpływ na kliencie aplikacji.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Zmiany modelu danych, które zaleca się nowej wersji usługi danych
 Rozważając opublikować nową wersję usługi danych, ważne jest zrozumienie, jak różne rodzaje zmian, może mieć wpływ na aplikacje klienckie. Zmiany do usługi danych, która może być konieczna utworzyć nową wersję usługi danych można podzielić na dwie następujące kategorie:

-   Zmienia się na kontrakt usługi, które obejmują aktualizacje do operacji usługi, zmiany w dostępności zestawy jednostek (źródła), zmiany wersji i inne zmiany zachowania usługi.

-   Zmienia się na kontrakt danych, który zawiera zmiany w modelu danych, kanału informacyjnego w formatach lub źródła danych dostosowań.

 Poniższe szczegóły tabeli, dla których rodzaje zmian, należy rozważyć publikowanie nową wersję usługi danych:

|Typ zmiany|Wymaga nowej wersji|Nowa wersja nie jest wymagane|
|--------------------|----------------------------|----------------------------|
|Operacje usługi|— Dodać nowego parametru<br />— Zmień zwracany typ<br />-Usuń operacji usługi|-Usuń istniejące parametr<br />— Dodawanie nowych operacji usługi|
|Zachowania usług|— Wyłącz liczba żądań<br />-Wyłącz obsługę projekcji<br />— Zwiększ numer wersji usługi wymaganych danych|-Włącz liczba żądań<br />-Włącz obsługę projekcji<br />— Zmniejsz wersja usługi danych wymagane|
|Uprawnienia zestawu jednostek|— Ogranicz uprawnienia do zestawu jednostek<br />-Zmiany kodu odpowiedzi (nowe pierwsza wartość cyfr) <sup>1</sup>|-Zwalnia jednostki Ustawianie uprawnień<br />-Zmiany kodu odpowiedzi (tego samego pierwsza wartość cyfr)|
|Właściwości jednostki|-Usuń istniejącą właściwość lub relacji<br />— Dodawanie właściwości niedopuszczającej<br />-Zmiany istniejącej właściwości|-Dodaj właściwość nullable<sup>2</sup>|
|Zestawy jednostek|-Usuń zestaw jednostek|-Dodaj typ pochodny<br />-Zmień typ podstawowy<br />— Dodać zestaw jednostek|
|Dostosowywanie źródła|-Zmienić mapowanie właściwości jednostki||

 <sup>1</sup> to może zależeć od jak ściśle aplikacja kliencka opiera się na odbieranie określonego kodu błędu.

 <sup>2</sup> można ustawić <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość `true` klienta zignorować nowe właściwości wysyłane przez usługę danych, które nie są zdefiniowane na komputerze klienckim. Gdy wykonywane są operacje wstawiania, właściwości nieuwzględnionych przez klienta w żądaniu POST są ustawione wartości domyślne. W przypadku aktualizacji istniejących danych we właściwości nieznany do klienta mogą być zastępowane wartościami domyślnymi. W takim przypadku należy wysłać aktualizację jako żądaniu scalania, co jest ustawieniem domyślnym. Aby uzyskać więcej informacji, zobacz [zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Jak kontrolować wersję usługi danych
 Gdy jest to wymagane, nowa wersja usługi danych jest definiowany przez tworzenie nowego wystąpienia usługi przy użyciu modelu danych lub kontrakt zaktualizowany. Ta nowa usługa jest następnie udostępniany przy użyciu nowego identyfikatora URI punktu końcowego, które odróżnia go od poprzedniej wersji. Na przykład:

-   Stara wersja: `http://services.odata.org/Northwind/v1/Northwind.svc/`

-   Nowa wersja: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Podczas uaktualniania usługi danych, klienci muszą również zostać zaktualizowane na podstawie nowych metadanych usługi danych i używać nowego katalogu głównego identyfikatora URI. Jeśli to możliwe, należy zachować poprzednią wersję usługi danych do obsługi klientów, które nie zostały jeszcze uaktualnione do nowej wersji. Gdy nie są już potrzebne, można usunąć starszych wersji usługi danych. Należy rozważyć, utrzymywanie identyfikatora URI w pliku konfiguracji zewnętrzny punkt końcowy usługi danych.

## <a name="odata-protocol-versions"></a>Wersje protokołu OData
 Jak są wydawane nowe wersje OData, aplikacje klienckie mogą nie używać tę samą wersję protokołu OData, która jest obsługiwana przez usługę danych. Starsza aplikacja kliencka może uzyskać dostęp do usługi danych, która obsługuje nowszą wersję protokołu OData. Aplikacja kliencka może również używany w nowszej wersji biblioteki klienta usługi danych WCF, która obsługuje nowszą wersję protokołu OData niż usługi danych, który jest dostępny.

 Pomoc techniczną świadczoną przez OData do obsługi takich scenariuszy versioning korzysta z usług danych WCF. Dostępna jest również Obsługa generowania i tworzenie klas usługi danych klienta, kiedy klient używa innej wersji OData niż dane przy użyciu metadanych modelu danych usługi używa. Aby uzyskać więcej informacji, zobacz [OData: przechowywanie wersji protokołu](https://go.microsoft.com/fwlink/?LinkId=186071).

### <a name="version-negotiation"></a>Negocjowanie wersji
 Usługi danych można skonfigurować tak, aby zdefiniować najwyższa wersja protokołu OData, który będzie używany przez usługę, niezależnie od wersji zażądane przez klienta. Można to zrobić, określając <xref:System.Data.Services.Common.DataServiceProtocolVersion> wartość <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> właściwość <xref:System.Data.Services.DataServiceBehavior> używane przez usługę danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

 Gdy aplikacja używa biblioteki klienta usługi danych WCF dostęp do usługi danych, bibliotek automatycznie ustawić tych nagłówków do prawidłowych wartości w zależności od wersji OData i funkcje, które są używane w aplikacji. Domyślnie usługi danych WCF używa Najniższa wersja protokołu, który obsługuje żądanej operacji.

 W poniższej tabeli przedstawiono wersje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] i [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] który zapewnia obsługę usług danych WCF dla określonych wersji protokołu OData.

|Wersja protokołu OData|Obsługa wprowadzone w systemie...|
|-----------------------------------------------------------------------------------|----------------------------|
|Wersja 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Z dodatkiem Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] w wersji 3|
|W wersji 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Aktualizacja [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] z dodatkiem SP1. Możesz pobrać i zainstalować aktualizację z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] w wersji 4|
|w wersji 3|— Można pobrać i zainstalować to wersja wstępna, która obsługuje OData w wersji 3 z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Wersje metadanych
 Domyślnie usługi danych WCF używa wersji 1.1 CSDL do reprezentowania modelu danych. Jest to zawsze w przypadku modeli danych, które są oparte na dostawcy odbicia lub dostawcy usług danych niestandardowych. Jednakże, jeśli model danych jest zdefiniowana za pomocą [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], wersja CSDL, zwracany jest taka sama jak wersja używanego przez [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. Wersja CSDL jest określana przez przestrzeń nazw [elementu schematu](https://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). Aby uzyskać więcej informacji, zobacz specyfikację [ \[MC CSDL\]: koncepcyjny formatu pliku definicji schematu](https://go.microsoft.com/fwlink/?LinkId=159072).

 `DataServices` Elementów zwróconych metadanych zawiera także `DataServiceVersion` atrybut, który ma taką samą wartość jak `DataServiceVersion` nagłówka w komunikacie odpowiedzi. Aplikacje klienckie, takie jak **Dodaj odwołanie do usługi** okno dialogowe w programie Visual Studio, dzięki tym informacjom można wygenerować klas usługi danych klienta, które działają prawidłowo z wersją usługi danych WCF hostującego usługę danych. Aby uzyskać więcej informacji, zobacz [OData: przechowywanie wersji protokołu](https://go.microsoft.com/fwlink/?LinkId=186071).

## <a name="see-also"></a>Zobacz też

- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
