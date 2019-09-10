---
title: Przechowywanie wersji usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f2007e5c2fa638d64c5c1e0d6879e12c7bcc901d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854103"
---
# <a name="data-service-versioning-wcf-data-services"></a>Przechowywanie wersji usługi danych (Usługi danych programu WCF)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Umożliwia tworzenie usług danych, dzięki czemu klienci mogą uzyskiwać dostęp do danych jako zasoby przy użyciu identyfikatorów URI opartych na modelu danych. Protokół OData obsługuje również definicje operacji usługi. Po wstępnym wdrożeniu i potencjalnie kilka razy w okresie istnienia tych usług mogą być konieczne zmiany w przypadku różnych powodów, takich jak zmiana potrzeb firmy, wymagania dotyczące technologii informatycznych lub Rozwiązywanie innych problemów. Po wprowadzeniu zmian w istniejącej usłudze danych należy wziąć pod uwagę, czy należy zdefiniować nową wersję usługi danych i jak najlepiej zminimalizować wpływ istniejących aplikacji klienckich. Ten temat zawiera wskazówki dotyczące tego, kiedy i jak utworzyć nową wersję usługi danych. Opisano w nim również, w jaki sposób Usługi danych programu WCF obsługuje wymianę między klientami i usługami danych, które obsługują różne wersje protokołu OData.

## <a name="versioning-a-wcf-data-service"></a>Przechowywanie wersji usługi danych programu WCF
 Po wdrożeniu usługi danych i wykorzystaniu danych, zmiany w usłudze danych mogą powodować problemy ze zgodnością z istniejącymi aplikacjami klienckimi. Jednak ze względu na to, że zmiany są często wymagane przez ogólne potrzeby biznesowe usługi, należy wziąć pod uwagę, kiedy i jak utworzyć nową wersję usługi danych z minimalnym wpływem na aplikacje klienckie.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Zmiany modelu danych, które zalecają nową wersję usługi danych
 Biorąc pod uwagę, czy publikować nową wersję usługi danych, ważne jest, aby zrozumieć, w jaki sposób różne rodzaje zmian mogą mieć wpływ na aplikacje klienckie. Zmiany w usłudze danych, które mogą wymagać utworzenia nowej wersji usługi danych, można podzielić na następujące dwie kategorie:

- Zmiany w kontrakcie usługi, w tym aktualizacje dotyczące operacji usługi, zmiany dostępności zestawów jednostek (źródła danych), zmiany wersji i inne zmiany zachowań usługi.

- Zmiany w umowie dotyczącej danych, w tym zmiany w modelu danych, formatach kanałów informacyjnych lub dostosowaniach kanału informacyjnego.

 W poniższej tabeli przedstawiono szczegóły dotyczące rodzaju zmian, które należy wziąć pod uwagę przy publikowaniu nowej wersji usługi danych:

|Typ zmiany|Wymaga nowej wersji|Nowa wersja nie jest wymagana|
|--------------------|----------------------------|----------------------------|
|Operacje usługi|-Dodaj nowy parametr<br />-Zmień zwracany typ<br />-Usuń operację usługi|-Usuń istniejący parametr<br />-Dodaj nową operację usługi|
|Zachowania usługi|-Disable żądania Count<br />-Wyłącz obsługę projekcji<br />-Zwiększ wymaganą wersję usługi danych|-Włącz żądania Count<br />-Włącz obsługę projekcji<br />-Zmniejsz wymaganą wersję usługi danych|
|Uprawnienia do zestawu jednostek|-Ograniczanie uprawnień zestawu jednostek<br />-Zmiana kodu odpowiedzi (Nowa pierwsza wartość cyfry) <sup>1</sup>|-Złagodzenie uprawnień do ustawiania jednostek<br />-Zmiana kodu odpowiedzi (ta sama wartość pierwszej cyfry)|
|Właściwości jednostki|-Usuń istniejącą właściwość lub relację<br />-Dodaj właściwość niedopuszczające wartości null<br />-Zmiana istniejącej właściwości|-Dodaj właściwość null<sup>2</sup>|
|Zestawy jednostek|-Usuń zestaw jednostek|-Dodaj typ pochodny<br />-Zmień typ podstawowy<br />-Dodaj zestaw jednostek|
|Dostosowanie kanału informacyjnego|-Zmień mapowanie właściwości Entity-Property||

 <sup>1</sup> może zależeć od tego, jak ścisła aplikacja kliencka korzysta z uzyskiwania określonego kodu błędu.

 <sup>2</sup> można ustawić <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> Właściwość `true` na, aby klient ignorował wszystkie nowe właściwości wysyłane przez usługę danych, które nie są zdefiniowane na kliencie. Jednak po wykonaniu operacji wstawiania właściwości nieuwzględnione przez klienta w żądaniu POST są ustawiane na wartości domyślne. W przypadku aktualizacji wszystkie istniejące dane we właściwości nieznanej dla klienta mogą zostać zastąpione wartościami domyślnymi. W takim przypadku należy wysłać aktualizację jako żądanie scalania, co jest ustawieniem domyślnym. Aby uzyskać więcej informacji, zobacz [zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Jak uzyskać wersję usługi danych
 W razie potrzeby Nowa wersja usługi danych jest definiowana przez utworzenie nowego wystąpienia usługi z zaktualizowanym kontraktem usługi lub modelem danych. Ta nowa usługa zostanie udostępniona przy użyciu nowego punktu końcowego URI, który odróżnia go od poprzedniej wersji. Przykład:

- Stara wersja:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nowa wersja:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Podczas uaktualniania usługi danych należy zaktualizować klientów na podstawie nowych metadanych usługi danych i użyć nowego głównego identyfikatora URI. Jeśli to możliwe, należy zachować poprzednią wersję usługi danych, aby obsługiwała klientów, którzy nie zostali jeszcze uaktualnioni do korzystania z nowej wersji. Starsze wersje usługi danych mogą być usuwane, gdy nie są już potrzebne. Należy rozważyć utrzymywanie identyfikatora URI punktu końcowego usługi danych w zewnętrznym pliku konfiguracji.

## <a name="odata-protocol-versions"></a>Wersje protokołu OData
 Po udostępnieniu nowych wersji usługi OData aplikacje klienckie mogą nie używać tej samej wersji protokołu OData obsługiwanej przez usługę danych. Starsza aplikacja kliencka może uzyskać dostęp do usługi danych, która obsługuje nowszą wersję protokołu OData. Aplikacja kliencka może również korzystać z nowszej wersji biblioteki klienta Usługi danych programu WCF, która obsługuje nowszą wersję protokołu OData niż usługa danych, do której uzyskuje się dostęp.

 Usługi danych programu WCF wykorzystuje pomoc techniczną dostępną przez usługi OData do obsługi takich scenariuszy przechowywania wersji. Obsługiwane jest również generowanie metadanych modelu danych i używanie ich do tworzenia klas usługi danych klienta, gdy klient korzysta z innej wersji protokołu OData niż używana przez usługę danych. Aby uzyskać więcej informacji, [zobacz OData: Przechowywanie wersji](https://go.microsoft.com/fwlink/?LinkId=186071)protokołu.

### <a name="version-negotiation"></a>Negocjowanie wersji
 Usługę danych można skonfigurować w celu zdefiniowania najwyższej wersji protokołu OData, który będzie używany przez usługę, niezależnie od wersji żądanej przez klienta. Można to zrobić, określając <xref:System.Data.Services.Common.DataServiceProtocolVersion> wartość <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> właściwości <xref:System.Data.Services.DataServiceBehavior> używanej przez usługę danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

 Gdy aplikacja korzysta z Usługi danych programu WCFch bibliotek klienckich w celu uzyskania dostępu do usługi danych, biblioteki automatycznie ustawiają te nagłówki na prawidłowe wartości, w zależności od wersji protokołu OData i funkcji używanych w aplikacji. Domyślnie Usługi danych programu WCF używa najniższej wersji protokołu, która obsługuje żądaną operację.

 W poniższej tabeli przedstawiono listę wersji .NET Framework i Silverlight, które obejmują Usługi danych programu WCF obsługę określonych wersji protokołu OData.

|Wersja protokołu OData|Obsługa wprowadzona w...|
|-----------------------------------------------------------------------------------|----------------------------|
|Wersja 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Dodatek Service Pack 1 (SP1)<br />— Silverlight w wersji 3|
|Wersja 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />— Aktualizacja [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] programu SP1. Aktualizację można pobrać i zainstalować z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkId=158125).<br />— Silverlight w wersji 4|
|Wersja 3|— Możesz pobrać i zainstalować wersję wstępną, która obsługuje protokół OData w wersji 3 z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Wersje metadanych
 Domyślnie program Usługi danych programu WCF reprezentuje model danych przy użyciu wersji 1,1 CSDL. Jest to zawsze przypadek dla modeli danych opartych na dostawcy odbicia lub niestandardowym dostawcy usługi danych. Jeśli jednak model danych jest zdefiniowany przy użyciu Entity Framework, zwracana wersja usługi CSDL jest taka sama jak wersja używana przez Entity Framework. Wersja CSDL jest określana na podstawie przestrzeni nazw [elementu schematu (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 Element zwracanych metadanych również `DataServiceVersion` zawiera atrybut, który ma taką samą wartość jak `DataServiceVersion` nagłówek w komunikacie odpowiedzi. `DataServices` Aplikacje klienckie, takie jak okno dialogowe **Dodaj odwołanie do usługi** w programie Visual Studio, wykorzystują te informacje w celu wygenerowania klas usługi danych klienta, które działają poprawnie z wersją usługi danych programu WCF, która obsługuje usługę danych. Aby uzyskać więcej informacji, [zobacz OData: Przechowywanie wersji](https://go.microsoft.com/fwlink/?LinkId=186071)protokołu.

## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
