---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 1ce152b84f17a35982a75f54b5418623ba39210f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975232"
---
# <a name="wcf-data-services-45"></a>Usługi danych WCF 4.5

Usługi danych programu WCF (dawniej znany jako "ADO.NET Data Services") jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki [przenoszenia stanu (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI. Dostęp do danych jest uzyskiwany i zmieniany przy użyciu standardowych czasowników HTTP GET, PUT, POST i DELETE. Usługa OData używa Konwencji relacji jednostek [Entity Data Model](../adonet/entity-data-model.md) , aby udostępnić zasoby jako zestawy jednostek, które są powiązane ze skojarzeniami.

Usługi danych programu WCF używa protokołu OData do adresowania i aktualizacji zasobów. W ten sposób można uzyskać dostęp do tych usług z dowolnego klienta, który obsługuje protokół OData. Usługa OData umożliwia żądanie i zapisanie danych w zasobach przy użyciu dobrze znanych formatów transferu: Atom, zestaw standardów do wymiany i aktualizowania danych jako XML, a JavaScript Object Notation (JSON), format wymiany danych oparty na tekście, który jest szeroko używany w technologii AJAX zastosowania.

Usługi danych programu WCF mogą uwidaczniać dane pochodzące z różnych źródeł jako źródła danych OData. Narzędzia programu Visual Studio ułatwiają tworzenie usługi opartej na protokole OData przy użyciu modelu danych ADO.NET Entity Framework. Można również tworzyć źródła danych OData oparte na klasach środowiska uruchomieniowego języka wspólnego (CLR), a nawet z danymi z późnym wiązaniem lub bez typu.

Usługi danych programu WCF obejmuje również zestaw bibliotek klienckich, jeden dla ogólnych .NET Framework aplikacji klienckich, a drugi przeznaczony dla aplikacji opartych na technologii Silverlight. Te biblioteki klienckie zapewniają model programowania oparty na obiektach, gdy uzyskujesz dostęp do źródła danych OData ze środowisk, takich jak .NET Framework i Silverlight.

## <a name="where-should-i-start"></a>Gdzie należy zacząć?

W zależności od zainteresowań należy rozważyć wprowadzenie do Usługi danych programu WCF w jednym z poniższych tematów.

Chcę przeskoczyć do prawej strony...

- [Szybki start](quickstart-wcf-data-services.md)

- [Wprowadzenie](getting-started-with-wcf-data-services.md)

- [Silverlight — Szybki Start](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Samouczek szybki start dla programu Windows Phone Development](https://go.microsoft.com/fwlink/?LinkID=214535)

Pokaż mi tylko jakiś kod...

- [Szybki start](quickstart-wcf-data-services.md)

- [Instrukcje: Wykonywanie zapytań usługi danych](how-to-execute-data-service-queries-wcf-data-services.md)

- [Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)

Chcę dowiedzieć się więcej o usłudze OData...

- [Oficjalny dokument: wprowadzenie do usługi OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Otwórz witrynę sieci Web protokołu Data Protocol](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData: często zadawane pytania](https://go.microsoft.com/fwlink/?LinkId=185867)

Chcę obejrzeć kilka filmów wideo...

- [Przewodnik dla początkujących Usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkId=220864)

- [Film wideo dla deweloperów Usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData: Witryna sieci Web programistów](https://go.microsoft.com/fwlink/?LinkId=185866)

Chcę zobaczyć kompleksowe przykłady...

- [Przykłady dokumentacji Usługi danych programu WCF w galerii przykładów MSDN](https://go.microsoft.com/fwlink/?LinkID=220865)

- [Inne przykłady Usługi danych programu WCF w galerii przykładów MSDN](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Jak integruje się z programem Visual Studio?

- [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)

- [Tworzenie usługi danych](creating-the-data-service.md)

- [Dostawca programu Entity Framework](entity-framework-provider-wcf-data-services.md)

Co mogę zrobić z nim?

- [Omówienie](wcf-data-services-overview.md)

- [Oficjalny dokument: wprowadzenie do usługi OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Scenariusze aplikacji](application-scenarios-wcf-data-services.md)

Chcę użyć programu Silverlight...

- [Silverlight — Szybki Start](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Usługi danych programu WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Wprowadzenie z technologią Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366)

Chcę użyć LINQ...

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)

- [Zagadnienia dotyczące LINQ](linq-considerations-wcf-data-services.md)

- [Instrukcje: Wykonywanie zapytań usługi danych](how-to-execute-data-service-queries-wcf-data-services.md)

Nadal potrzebuję więcej informacji...

- [Blog zespołu Usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkID=150511)

- [Zasoby](wcf-data-services-resources.md)

- [Centrum deweloperów Usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Otwórz witrynę sieci Web protokołu Data Protocol](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>W tej sekcji

[Omówienie](wcf-data-services-overview.md)

Zawiera przegląd funkcji dostępnych w Usługi danych programu WCF.

[Co nowego w Usługi danych programu WCF 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

Opisuje nowe funkcje w Usługi danych programu WCF i obsługę nowych funkcji OData.

[Wprowadzenie](getting-started-with-wcf-data-services.md)

Opisuje sposób udostępniania i korzystania ze źródeł danych OData przy użyciu Usługi danych programu WCF.

[Definiowanie usług danych WCF](defining-wcf-data-services.md)

Opisuje sposób tworzenia i konfigurowania usługi danych, która udostępnia źródła strumieniowego OData.

[Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)

Opisuje sposób używania bibliotek klienckich do korzystania ze źródeł danych OData z aplikacji klienckiej .NET Framework.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie stanu reprezentacji (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
