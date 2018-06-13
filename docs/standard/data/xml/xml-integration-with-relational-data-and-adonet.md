---
title: Integracja XML z danych relacyjnych i ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e9bdb9b88d51e5435609bbab8bbe21a985505a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575704"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integracja XML z danych relacyjnych i ADO.NET
**Dokumentu XmlDataDocument** klasy jest klasy pochodnej z **XmlDocument**i zawiera dane XML. Zaletą **dokumentu XmlDataDocument** jest mostka między danych relacyjnych i hierarchicznych. Jest **XmlDocument** może być powiązana z **DataSet** i obie klasy można synchronizować zmiany wprowadzone w danych znajdujących się w dwóch klas. **XmlDocument** który jest powiązany **DataSet** umożliwia XML do integracji z danych relacyjnych i nie trzeba mieć dane reprezentowane jako albo XML lub w formacie relacyjnym. Możesz wykonać obie czynności i nie można ograniczyć do pojedynczego reprezentację danych.  
  
 Są dostępne w dwóch widoków danych korzyści:  
  
-   Strukturalnych części dokumentu XML może być mapowane do zestawu danych i można wydajnie przechowywane, indeksowane i przeszukiwane.  
  
-   Przekształcenia, weryfikacji i nawigacji można efektywnie za pośrednictwem modelu kursora relationally przechowywanych danych XML. Czasami mogą to robić wydajniej przed relacyjne struktury niż Jeśli XML znajduje się w **XmlDocument** modelu.  
  
-   **DataSet** może przechowywać fragment kodu XML. Oznacza to, że używasz **XPath** lub **XslTransform** do przechowywania do **DataSet** tylko te elementy i atrybuty zainteresowań. Z tego miejsca, zmian na mniejsze, filtrowane podzestaw danych ze zmianami propagowanie większych danych w **dokumentu XmlDataDocument**.  
  
 Można również uruchomić transformacji nad danymi, które zostało załadowane do **DataSet** z programu SQL Server. Innym rozwiązaniem jest powiązać kontrolce zarządzanych stylu klasy .NET Framework i formanty formularza sieci Web **DataSet** że wypełniono ze strumienia wejściowego XML.  
  
 Oprócz obsługi **XslTransform**, **dokumentu XmlDataDocument** przedstawia dane relacyjne **XPath** zapytania i sprawdzania poprawności.  Zasadniczo wszystkie usługi XML są dostępne za pośrednictwem danych relacyjnych i relacyjne urządzeń, takich jak powiązanie formantu, codegen i tak dalej, są dostępne za pośrednictwem strukturalnych projekcji XML bez naruszania wierności XML.  
  
 Ponieważ **dokumentu XmlDataDocument** jest odziedziczone **XmlDocument**, zapewnia implementacji modelu DOM. W3C Fakt który **dokumentu XmlDataDocument** jest skojarzony z i przechowuje podzbiór danych w ramach, **zestawu danych** nie ograniczenia lub alter jako **XmlDocument** w dowolny sposób. Kod napisany za użycie **XmlDocument** works niezmienione względem **dokumentu XmlDataDocument**. **DataSet** zapewnia relacyjny widok tych samych danych, definiując tabele, kolumny, relacji i ograniczeń i magazyn danych użytkownika autonomicznych, w pamięci.  
  
 Na poniższej ilustracji przedstawiono różne skojarzenia, że dane XML mają z **DataSet** i **dokumentu XmlDataDocument**.  
  
 ![Zestaw danych XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 Na ilustracji pokazano, że dane XML mogą być ładowane bezpośrednio do **DataSet**, co pozwala w sposób relacyjne bezpośredniej XML. Lub XML mogą zostać załadowane do modelu DOM, który jest klasa pochodna **dokumentu XmlDataDocument**, a następnie ładowania i synchronizacji z **zestawu danych**. Ponieważ **DataSet** i **dokumentu XmlDataDocument** są synchronizowane przez jeden zestaw danych, zmiany wprowadzone w danych w jednym magazynie zostaną odzwierciedlone w innym magazynie.  
  
 **Dokumentu XmlDataDocument** dziedziczy wszystkie funkcje edycji i nawigacyjne z **XmlDocument**. Czasami przy użyciu **dokumentu XmlDataDocument** i jego funkcje dziedziczone, synchronizowane z **DataSet**, jest bardziej odpowiednia opcja niż ładowania XML bezpośrednio do **zestawudanych**. W poniższej tabeli przedstawiono elementy wziąć pod uwagę w przypadku wybrania metody załadować **zestawu danych**.  
  
|Podczas ładowania XML bezpośrednio do zestawu danych|Podczas synchronizowania dokumentu XmlDataDocument z zestawu danych|  
|----------------------------------------------|-----------------------------------------------------------|  
|Zapytania o dane w **DataSet** są łatwiejsze przy użyciu programu SQL niż XPath.|Kwerendy XPath potrzebnych danych w **zestawu danych**.|  
|Zachowanie elementu kolejności w źródle XML nie są ważne.|Bardzo ważne jest zachowanie elementu kolejności w źródle XML.|  
|Biały znak między elementami i formatowanie nie trzeba być zachowane w źródle XML.|Bardzo ważne jest białe i zachowywania formatowania w źródle XML.|  
  
 Czy ładowanie i zapisywania XML bezpośrednio do i z **DataSet** adresy potrzeb, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [Zapisywanie zestawu danych jako dane XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 W przypadku **DataSet** z **dokumentu XmlDataDocument** dotyczy Twoich potrzeb dotyczących zobacz [synchronizowanie Datasetwith dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
