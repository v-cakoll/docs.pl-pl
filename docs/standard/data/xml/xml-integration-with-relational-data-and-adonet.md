---
title: Integracja XML z danymi relacyjnymi i ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d86c590f2d5fe6bc970c2f8ac6de43d3e8485650
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183148"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integracja XML z danymi relacyjnymi i ADO.NET
**XmlDataDocument** klasa jest klasy pochodnej **XmlDocument**i zawiera dane XML. Zaletą **XmlDataDocument** jest zapewnianie Most między danymi relacyjne i hierarchiczne. Jest **XmlDocument** może być powiązana z **DataSet** i obie klasy można synchronizować zmiany wprowadzone do danych znajdujących się w dwóch klas. **XmlDocument** , jest powiązany z **DataSet** umożliwia XML w celu integracji z danymi relacyjnymi i jest konieczne dane reprezentowane jako obu XML lub w formacie relacyjnym. Obie opcje, a nie być ograniczone do pojedynczego reprezentację danych.  
  
 Korzyści dostępnych danych w dwóch widoków są:  
  
-   Ze strukturą części dokumentu XML może być mapowane do zestawu danych, można efektywnie przechowywane, indeksowane i przeszukiwane.  
  
-   Przekształcenia, weryfikacji i nawigacji może odbywać się wydajnie za pomocą modelu kursor nad dane XML, które są przechowywane w relationally. Czasami można to zrobić w bardziej efektywnie względem relacyjnej struktury niż Jeśli kod XML jest przechowywany w **XmlDocument** modelu.  
  
-   **DataSet** można przechowywać fragment kodu XML. Oznacza to, że używasz **XPath** lub **XslTransform** do przechowywania do **zestawu danych** tylko tych elementów i atrybutów zainteresowania. Z tego miejsca zmian na mniejsze, przefiltrowane podzbiór danych, ze zmianami propagowanie danych większe w **XmlDataDocument**.  
  
 Można również uruchomić transformacji danych, który został załadowany do **DataSet** z programu SQL Server. Innym rozwiązaniem jest powiązanie WinForm zarządzanych styl klas .NET Framework i formanty formularza sieci Web **DataSet** , została wypełniona ze strumienia wejściowego XML.  
  
 Oprócz obsługi **XslTransform**, **XmlDataDocument** udostępnia dane relacyjne do **XPath** zapytania i sprawdzania poprawności.  Po prostu wszystkich usług XML są dostępne za pośrednictwem w relacyjnej bazie danych i obiektów relacyjnych, takich jak powiązania kontrolki, generowanie kodu i tak dalej, są dostępne za pośrednictwem ze strukturą projekcji XML bez naruszania wierności XML.  
  
 Ponieważ **XmlDataDocument** jest dziedziczony z **XmlDocument**, zapewnia implementacja modelu DOM. W3C Fakt, **XmlDataDocument** jest skojarzony, a następnie przechowuje podzbiór danych w obrębie, **zestawu danych** nie ograniczenia lub zmienić jego użycie jako **XmlDocument** w dowolny sposób. Kod napisany z **XmlDocument** działa niezmienione względem **XmlDataDocument**. **DataSet** zapewnia relacyjny widok tych samych danych, definiując tabele, kolumny, relacje i ograniczenia i jest do przechowywania danych użytkownika autonomicznych, w pamięci.  
  
 Na poniższej ilustracji przedstawiono różne skojarzenia, dane XML ma z **DataSet** i **XmlDataDocument**.  
  
 ![Zestaw danych XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 Na ilustracji przedstawiono, że dane XML mogą być ładowane bezpośrednio do **DataSet**, co umożliwia bezpośrednią manipulację za pomocą XML w relacyjnej sposób. Lub, w pliku XML mogą być ładowane do klasy pochodnej modelu DOM, który jest **XmlDataDocument**, a następnie załadować i zsynchronizowane z usługą **zestawu danych**. Ponieważ **DataSet** i **XmlDataDocument** są synchronizowane dla jednego zestawu danych, zmiany wprowadzone do danych w jednym magazynie są odzwierciedlane w innym magazynie.  
  
 **XmlDataDocument** dziedziczy wszystkie funkcje edycji i nawigacji z **XmlDocument**. Istnieją momenty, korzystając z **XmlDataDocument** i jego odziedziczonych funkcji i zsynchronizowane z **zestawu danych**, jest bardziej odpowiednia opcja niż ładowania XML bezpośrednio w **zestawudanych**. W poniższej tabeli przedstawiono elementy wziąć pod uwagę podczas wybierania metody ładowania **zestawu danych**.  
  
|Kiedy należy załadować XML bezpośrednio do zestawu danych|Kiedy należy zsynchronizować elementem XmlDataDocument z zestawu danych|  
|----------------------------------------------|-----------------------------------------------------------|  
|Zapytania dotyczące danych w **DataSet** mogą pozwalać na łatwiejsze przy użyciu języka SQL niż XPath.|Zapytania XPath potrzebnych danych w **zestawu danych**.|  
|Zachowywanie kolejności ze źródła XML — element nie jest krytyczny.|Ważne jest zachowanie kolejności ze źródła XML element.|  
|Odstępy między elementami i formatowanie nie musi zostać zachowane ze źródła XML.|Biały znak i formatowania zachowania ze źródła XML ma krytyczne znaczenie.|  
  
 Jeśli podczas ładowania i pisanie XML bezpośrednio do i z **DataSet** zaspokaja Twoje potrzeby, zobacz [Ładowanie elementu DataSet z pliku XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [Zapisywanie zestawu danych jako danych XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Jeśli podczas ładowania **zestawu danych** z **XmlDataDocument** zaspokaja Twoje potrzeby, zobacz [synchronizowanie Datasetwith dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
