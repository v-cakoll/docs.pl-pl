---
title: Przechowywanie wersji usługi danych (usługi danych WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121528"
---
# <a name="data-service-versioning-wcf-data-services"></a>Przechowywanie wersji usługi danych (usługi danych WCF)
Open Data Protocol (OData) umożliwia tworzenie usług danych, dzięki czemu klienci mogą uzyskiwać dostęp do danych jako zasobów przy użyciu identyfikatorów URI opartych na modelu danych. OData obsługuje również definicję operacji usługi. Po pierwszym wdrożeniu i potencjalnie kilka razy w okresie ich istnienia te usługi danych mogą wymagać zmiany z różnych powodów, takich jak zmieniające się potrzeby biznesowe, wymagania dotyczące technologii informatycznych lub w celu rozwiązania innych problemów. Podczas wprowadzania zmian w istniejącej usłudze danych należy rozważyć, czy zdefiniować nową wersję usługi danych i jak najlepiej zminimalizować wpływ na istniejące aplikacje klienckie. Ten temat zawiera wskazówki dotyczące tego, kiedy i jak utworzyć nową wersję usługi danych. Opisano w nim również, jak usługi WCF Data Services obsługują wymianę między klientami i usługami danych obsługującymi różne wersje protokołu OData.

## <a name="versioning-a-wcf-data-service"></a>Przechowywanie wersji usługi danych WCF
 Po wdrożeniu usługi danych i zużywaniu danych zmiany w usłudze danych mogą powodować problemy ze zgodnością z istniejącymi aplikacjami klienckimi. Jednak ponieważ zmiany są często wymagane przez ogólne potrzeby biznesowe usługi, należy wziąć pod uwagę, kiedy i jak utworzyć nową wersję usługi danych z najmniejszym wpływem na aplikacje klienckie.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Zmiany modelu danych, które zalecają nową wersję usługi danych
 Rozważając, czy opublikować nową wersję usługi danych, ważne jest, aby zrozumieć, jak różne rodzaje zmian mogą wpływać na aplikacje klienckie. Zmiany w usłudze danych, które mogą wymagać utworzenia nowej wersji usługi danych, można podzielić na następujące dwie kategorie:

- Zmiany w umowie serwisowej — które obejmują aktualizacje operacji serwisowych, zmiany w dostępności zestawów jednostek (kanałów informacyjnych), zmiany wersji i inne zmiany zachowań usług.

- Zmiany w umowie na dane — które obejmują zmiany w modelu danych, formatach danych lub dostosowaniach danych.

 Poniższa tabela zawiera szczegółowe informacje o tym, jakie rodzaje zmian należy rozważyć opublikowanie nowej wersji usługi danych:

|Typ zmiany|Wymaga nowej wersji|Nowa wersja nie jest potrzebna|
|--------------------|----------------------------|----------------------------|
|Operacje serwisowe|- Dodaj nowy parametr<br />- Zmiana typu zwrotu<br />- Usuń działanie serwisowe|- Usuń istniejący parametr<br />- Dodaj nową operację serwisową|
|Zachowania usług|- Wyłącz prośby o liczbę<br />- Wyłącz obsługę projekcji<br />- Zwiększenie wymaganej wersji usługi danych|- Włącz żądania zliczania<br />- Włącz obsługę projekcji<br />- Zmniejsz wymaganą wersję usługi danych|
|Uprawnienia zestawu jednostek|- Ogranicz uprawnienia zestawu jednostek<br />- Zmiana kodu odpowiedzi (nowa wartość pierwszej cyfry) <sup>1</sup>|- Rozluźnij uprawnienia zestawu jednostek<br />- Zmień kod odpowiedzi (ta sama wartość pierwszej cyfry)|
|Właściwości encji|- Usuń istniejącą właściwość lub relację<br />- Dodaj właściwość nienastępnącą do null<br />- Zmiana istniejącej właściwości|- Dodaj nullable właściwości<sup>2</sup>|
|zestawy jednostek|- Usuń zestaw jednostek|- Dodaj typ pochodny<br />- Zmiana typu bazowego<br />- Dodaj zestaw jednostek|
|Dostosowywanie kanału informacyjnego|- Zmiana mapowania właściwości jednostki||

 <sup>1</sup> Może to zależeć od tego, jak ściśle aplikacja kliencka opiera się na otrzymaniu określonego kodu błędu.

 <sup>2</sup> Można ustawić <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość, aby `true` klient zignorował wszystkie nowe właściwości wysyłane przez usługę danych, które nie są zdefiniowane na kliencie. Jednak po wstawieniu właściwości nie uwzględnione przez klienta w żądaniu POST są ustawione na ich wartości domyślne. W przypadku aktualizacji wszystkie istniejące dane we właściwości nieznanej klientowi mogą zostać zastąpione wartościami domyślnymi. W takim przypadku należy wysłać aktualizację jako żądanie KORESPONDENCJI SERYJNEJ, które jest wartością domyślną. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Jak wersję usługi danych
 W razie potrzeby nowa wersja usługi danych jest definiowana przez utworzenie nowego wystąpienia usługi ze zaktualizowaną umową serwisową lub modelem danych. Ta nowa usługa jest następnie udostępniane przy użyciu nowego punktu końcowego identyfikatoraURI, który odróżnia go od poprzedniej wersji. Przykład:

- Stara wersja:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nowa wersja:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Podczas uaktualniania usługi danych klienci będą musieli również być aktualizowani na podstawie nowych metadanych usługi danych i używać nowego głównego identyfikatora URI. Jeśli to możliwe, należy zachować poprzednią wersję usługi danych do obsługi klientów, które nie zostały jeszcze uaktualnione do korzystania z nowej wersji. Starsze wersje usługi danych można usunąć, gdy nie są już potrzebne. Należy rozważyć utrzymanie identyfikatora URI punktu końcowego usługi danych w pliku konfiguracji zewnętrznej.

## <a name="odata-protocol-versions"></a>Wersje protokołu OData
 W miarę zwalniania nowych wersji OData aplikacje klienckie mogą nie używać tej samej wersji protokołu OData, która jest obsługiwana przez usługę danych. Starsza aplikacja kliencka może uzyskać dostęp do usługi danych, która obsługuje nowszą wersję OData. Aplikacja kliencka może również używać nowszej wersji biblioteki klienta usług danych WCF, która obsługuje nowszą wersję OData niż usługa danych, która jest uzyskiwany.

 WCF Data Services wykorzystuje wsparcie świadczone przez OData do obsługi takich scenariuszy przechowywania wersji. Istnieje również obsługa generowania i używania metadanych modelu danych do tworzenia klas usług danych klienta, gdy klient używa innej wersji OData niż używa usługa danych. Aby uzyskać więcej informacji, zobacz sekcję Przechowywanie wersji protokołu w artykule [OData: Overview.](https://www.odata.org/documentation/odata-version-2-0/overview/)

### <a name="version-negotiation"></a>Negocjacja wersji
 Usługę danych można skonfigurować do definiowania najwyższej wersji protokołu OData, który będzie używany przez usługę, niezależnie od wersji żądanej przez klienta. Można to zrobić, określając <xref:System.Data.Services.Common.DataServiceProtocolVersion> wartość <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> właściwości <xref:System.Data.Services.DataServiceBehavior> używanej przez usługę danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

 Gdy aplikacja używa bibliotek klienta WCF Data Services do uzyskiwania dostępu do usługi danych, biblioteki automatycznie ustawiają te nagłówki na poprawne wartości, w zależności od wersji OData i funkcji, które są używane w aplikacji. Domyślnie WCF Data Services używa najniższej wersji protokołu, który obsługuje żądaną operację.

 W poniższej tabeli opisano wersje programu .NET Framework i silverlight, które zawierają obsługę usług WCF Data Services dla określonych wersji protokołu OData.

|Wersja protokołu OData|Wsparcie wprowadzone w...|
|-----------------------------------------------------------------------------------|----------------------------|
|Wersja 1|- .NET Framework 3.5 Z dodatkiem Service Pack 1 (SP1)<br />- Silverlight w wersji 3|
|Wersja 2|- .NET Framework 4<br />- Silverlight w wersji 4|

### <a name="metadata-versions"></a>Wersje metadanych
 Domyślnie WCF Data Services używa wersji 1.1 CSDL do reprezentowania modelu danych. Jest to zawsze w przypadku modeli danych, które są oparte na dostawcy odbicia lub dostawcy usług danych niestandardowych. Jednak gdy model danych jest zdefiniowany przy użyciu entity framework, wersja CSDL zwrócił jest taka sama jak wersja, która jest używana przez Entity Framework. Wersja CSDL jest określana przez obszar nazw [elementu Schemat (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)

 Element `DataServices` zwróconych metadanych zawiera `DataServiceVersion` również atrybut, który jest `DataServiceVersion` taką samą wartością jak nagłówek w komunikacie odpowiedzi. Aplikacje klienckie, takie jak okno dialogowe **Dodawanie odwołania do usługi** w programie Visual Studio, używają tych informacji do generowania klas usług danych klienta, które działają poprawnie z wersją usług danych WCF obsługujących usługę danych. Aby uzyskać więcej informacji, zobacz sekcję Przechowywanie wersji protokołu w artykule [OData: Overview.](https://www.odata.org/documentation/odata-version-2-0/overview/)

## <a name="see-also"></a>Zobacz też

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
