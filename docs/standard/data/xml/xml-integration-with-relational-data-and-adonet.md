---
title: Integracja XML z danymi relacyjnymi i sterownikiem ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
ms.openlocfilehash: 30b788c77a2352d0d02ee772ab3f428381facd9f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155623"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integracja XML z danymi relacyjnymi i sterownikiem ADO.NET
Klasa **XmlDataDocument** jest klasą pochodną elementu **XmlDocument**i zawiera dane XML. Zaletą **XmlDataDocument** jest to, że zapewnia ona Most między danymi relacyjnymi i hierarchicznymi. Jest to **dokument XmlDocument** , który może być powiązany z **zestawem danych** , a obie klasy mogą synchronizować zmiany wprowadzone w danych znajdujących się w dwóch klasach. Element **XmlDocument** , który jest powiązany z **zestawem danych** , umożliwia integrację XML z danymi relacyjnymi, a dane nie muszą być reprezentowane jako XML lub w formacie relacyjnym. Można jednocześnie i nie ograniczyć się do pojedynczej reprezentacji danych.  
  
 Dostępne są następujące korzyści z używania danych w dwóch widokach:  
  
- Strukturalna część dokumentu XML może być mapowana na zestaw danych i wydajnie przechowywana, indeksowana i przeszukiwana.  
  
- Przekształcenia, walidacja i nawigacja mogą być efektywnie wykonywane przez model kursora nad danymi XML, które są przechowywane w sposób relacyjny. Czasami można wydajniej wykonywać przed strukturami relacyjnymi, niż gdyby kod XML jest przechowywany w modelu **XmlDocument** .  
  
- **Zestaw danych** może przechowywać część kodu XML. Oznacza to, że można użyć **XPath** lub **XslTransform** do przechowywania **danych** tylko dla tych elementów i atrybutów. W tym miejscu można wprowadzać zmiany w mniejszych, filtrowanych podzbiorach danych, przy czym zmiany są propagowane do większej ilości danych w **XmlDataDocument**.  
  
 Można również uruchomić transformację z danymi, które zostały załadowane do **zestawu danych** z SQL Server. Kolejną opcją jest powiązanie .NET Framework klas — formanty WinForm i WebForm zarządzane przez styl do **zestawu danych** , który został wypełniony ze strumienia wejściowego XML.  
  
 Oprócz obsługi **XslTransform**, **XmlDataDocument** uwidacznia dane relacyjne kwerend **XPath** i walidacji.  Zasadniczo wszystkie usługi XML są dostępne za pośrednictwem danych relacyjnych, a obiekty relacyjne, takie jak powiązania sterowania, codegen i tak dalej, są dostępne w ramach strukturalnego projekcji XML bez naruszania dokładności kodu XML.  
  
 Ponieważ **XmlDataDocument** jest Dziedziczony z **XmlDocument**, zapewnia implementację W3C dom. Fakt, że **XmlDataDocument** jest skojarzona z, i przechowuje podzestaw danych w ramach, **zestaw danych** nie ogranicza ani nie zmienia jego użycia jako **XmlDocument** w jakikolwiek sposób. Kod zapisany w celu użycia **dokumentu XmlDocument** nie jest zmieniany na **XmlDataDocument**. **Zestaw** danych udostępnia widok relacyjny tych samych danych przez Definiowanie tabel, kolumn, relacji i ograniczeń oraz jest autonomicznym magazynem danych użytkownika w pamięci.  
  
 Na poniższej ilustracji przedstawiono różne skojarzenia danych XML z **zestawem** danych i **XmlDataDocument**:
  
 ![Diagram przedstawiający różne skojarzenia z zestawem danych XML.](./media/xml-integration-with-relational-data-and-adonet/xml-integration-relational-data-adodotnet.gif)  
  
 Ilustracja pokazuje, że dane XML mogą być ładowane bezpośrednio do **zestawu danych**, co umożliwia bezpośrednie manipulowanie XML w sposób relacyjny. Lub plik XML można załadować do klasy pochodnej modelu DOM, która jest **XmlDataDocument**, a następnie załadować i zsynchronizować z **zestawem danych**. Ponieważ **zestaw danych** i **XmlDataDocument** są synchronizowane za pośrednictwem jednego zestawu danych, zmiany wprowadzone do danych w jednym sklepie są odzwierciedlane w innym magazynie.  
  
 **XmlDataDocument** dziedziczy wszystkie funkcje edycji i nawigacji z **dokumentu XmlDocument**. Istnieją przypadki, w których funkcja **XmlDataDocument** i jej Odziedziczone funkcje są synchronizowane z **zestawem danych**, jest bardziej odpowiednią opcją niż ładowanie kodu XML bezpośrednio do **zestawu danych**. W poniższej tabeli przedstawiono elementy, które należy wziąć pod uwagę podczas wybierania metody do załadowania **zestawu danych**.  
  
|Kiedy ładować XML bezpośrednio do zestawu danych|Kiedy synchronizować XmlDataDocument z zestawem danych|  
|----------------------------------------------|-----------------------------------------------------------|  
|Zapytania dotyczące danych w **zestawie danych** są łatwiejsze przy użyciu języka SQL niż XPath.|Zapytania XPath są niezbędne dla danych w **zestawie**danych.|  
|Zachowywanie kolejności elementów w źródłowym kodzie XML nie jest krytyczne.|Zachowywanie kolejności elementów w źródłowym kodzie XML jest krytyczne.|  
|Między elementami i formatowaniem nie trzeba zachować odstępu w źródłowym kodzie XML.|Białe miejsce i zachowywanie formatowania w źródłowym kodzie XML są krytyczne.|  
  
 Jeśli ładowanie i zapisywanie kodu XML bezpośrednio do i z **zestawu danych** odpowiada Twoim potrzebom, zobacz [Ładowanie zestawu danych z pliku XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [Zapisywanie zestawu danych jako danych XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Jeśli załadowanie **zestawu danych** z **XmlDataDocument** do Twoich potrzeb, zobacz [synchronizowanie zestawu danych z dokumentem XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Zobacz też

- [Używanie języka XML w elemencie DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
