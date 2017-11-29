---
title: Podsumowanie procesu wnioskowania schematu zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15469e917129db7668df17f22fb71b166993d4fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Podsumowanie procesu wnioskowania schematu zestawu danych
Proces wnioskowania najpierw określi, z dokumentu XML, elementy, które będzie można wywnioskować jako tabele. Z pozostałych pliku XML proces wnioskowania określa kolumn dla tych tabel. Zagnieżdżone tabele procesu wnioskowania generuje zagnieżdżonych <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiektów.  
  
 Poniżej znajduje się krótki opis reguły wnioskowania:  
  
-   Elementów, które mają atrybuty są wywnioskować jako tabele.  
  
-   Elementów, które mają elementy podrzędne są wywnioskować jako tabele.  
  
-   Elementy powtarzające się wywnioskować jako pojedynczej tabeli.  
  
-   Jeśli element dokumentu lub kluczu głównym ma żadnych atrybutów, a nie elementy podrzędne, które będzie można wywnioskować jako kolumny, jest wywnioskowany jako <xref:System.Data.DataSet>. W przeciwnym razie element dokumentu jest wywnioskowany jako tabelę.  
  
-   Atrybuty są wywnioskować jako kolumny.  
  
-   Elementy, które mają żadnych atrybutów ani elementów podrzędnych i nie powtarzaj, są wywnioskować jako kolumny.  
  
-   Dla elementów, które są wywnioskować jako tabele zagnieżdżone w obrębie innych elementów, które są również wywnioskować jak tabele, zagnieżdżoną **DataRelation** jest tworzona między dwiema tabelami. Nowy, podstawowej kolumny klucza o nazwie **TableName_Id** jest dodawane do obu tabel i używana przez **DataRelation**. A **ForeignKeyConstraint** jest tworzona między dwiema tabelami przy użyciu **TableName_Id** kolumny.  
  
-   Dla elementów, które są wywnioskować jako tabele i który zawiera tekst, ale mieć żadnych elementów podrzędnych, nową kolumnę o nazwie **TableName_Text** jest tworzony dla poszczególnych elementów tekstu. Jeśli element jest wywnioskowany jako tabelę i tekstu, ale ma także elementy podrzędne, tekst jest ignorowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Za pomocą języka XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
