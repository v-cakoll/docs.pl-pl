---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
  - Astoria
  - 'WCF Data Services, getting started'
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
---

# <a name="wcf-data-services-45"></a>Usługi danych WCF 4.5

Usługi danych WCF (wcześniej znane jako "Architektury ADO.NET Data Services") jest składnikiem programu .NET Framework, która umożliwia tworzenie usług, które używają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do prezentowania i wykorzystywania danych w Internecie lub intranecie przy użyciu semantyki [ (REST) Representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919). OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI. Dane są dostępne i zmieniać przy użyciu standardowych poleceń HTTP elementu GET, PUT, POST i DELETE. OData używa konwencji Relacja jednostki [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) aby uwidocznić zasoby jako zestawów jednostek, które są powiązane przez skojarzenia.

Usługi danych WCF korzysta z protokołu OData do adresowania i aktualizowania zasobów. W ten sposób uzyskujesz dostęp do tych usług, za pomocą dowolnego klienta, który obsługuje OData. OData pozwala na żądanie i zapisywania danych do zasobów przy użyciu dobrze znanych transferu formatów: Atom, zestaw standardów wymianę i aktualizowanie danych w formacie XML i JavaScript Object Notation (JSON), formatem wymiany danych tekstowych, często używane w aplikacjach w technologii AJAX.

Usługi danych WCF można ujawnić dane, które pochodzą z różnych źródeł, jako źródła OData. Narzędzia programu Visual Studio ułatwiają tworzenie usługi OData przy użyciu modelu danych ADO.NET Entity Framework. Można również utworzyć źródła danych OData na podstawie wspólnej klasy środowiska uruchomieniowego (języka wspólnego CLR) języka i nawet z późnym wiązaniem lub bez danych.

Usługi danych WCF zawiera również zestaw bibliotek klienta dla głównej aplikacji klienta programu .NET Framework i inny wpis specjalnie dla aplikacji opartych na technologii Silverlight. Tych bibliotek klienckich zapewnia model programowania oparty na obiekt, gdy uzyskujesz dostęp do źródła danych ze środowisk, takich jak .NET Framework lub Silverlight jako technologii OData.

## <a name="where-should-i-start"></a>Gdzie mam zacząć?

W zależności od zainteresowaniach należy rozważyć wprowadzenie do usługi danych WCF w jeden z następujących tematów.

Chcę, aby przejść bezpośrednio...

- [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

- [Szybki start Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Szybki start Silverlight dla systemu Windows Phone rozwoju](https://go.microsoft.com/fwlink/?LinkID=214535)

Po prostu Pokaż kodu...

- [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [Instrukcje: Powiąż dane z programu Windows Presentation Foundation elementów](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

Chcę dowiedzieć się więcej o OData...

- [Oficjalny dokument: Wprowadzenie do protokołu OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Otwórz witrynę sieci Web protokołu danych](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData: Często zadawane pytania](https://go.microsoft.com/fwlink/?LinkId=185867)

Chcę obejrzeć niektóre filmy wideo...

- [Przewodnik dla początkujących do usługi danych WCF](https://go.microsoft.com/fwlink/?LinkId=220864)

- [Filmy dla deweloperów usługi danych WCF](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData: Witryny sieci Web deweloperów](https://go.microsoft.com/fwlink/?LinkId=185866)

Chcę wyświetlić przykłady end-to-end...

- [Usługi WCF Data Services — przykłady dokumentacji w galerii przykładów MSDN](https://go.microsoft.com/fwlink/?LinkID=220865)

- [Inne usługi WCF Data Services — przykłady w galerii przykładów MSDN](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Jak można je zintegrować z programem Visual Studio?

- [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

- [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md)

- [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

Co można zrobić z nim?

- [Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

- [Oficjalny dokument: Wprowadzenie do protokołu OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Scenariusze aplikacji](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

Chcę użyć Silverlight...

- [Szybki start Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Wprowadzenie do programu Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366)

Chcę użyć LINQ...

- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

- [Zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

Mi nadal potrzebne pewne dodatkowe informacje...

- [Blog zespołu usług danych WCF](https://go.microsoft.com/fwlink/?LinkID=150511)

- [Zasoby](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

- [Centrum deweloperów usług danych WCF](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Otwórz witrynę sieci Web protokołu danych](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>W tej sekcji

[Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

Zawiera omówienie funkcji i funkcji dostępnych w usługach danych programu WCF.

[What's New in usługi danych WCF 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

W tym artykule opisano nowe funkcje w usługach danych programu WCF i obsługę nowych funkcji OData.

[Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

Zawiera opis sposobu prezentowania i wykorzystywania źródeł danych usługi OData przy użyciu usługi danych WCF.

[Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

W tym artykule opisano sposób tworzenia i konfigurowania usługi danych, która udostępnia źródłami danych OData.

[Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

W tym artykule opisano, jak używać tych źródeł od aplikacji klienckiej .NET Framework za pomocą biblioteki klienta.

## <a name="see-also"></a>Zobacz także

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
