---
title: Podsumowanie procesu wnioskowania schematu zestawu danych
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 9bcc5ce1574eed60d2ef1aa35bdafe8c6050e44c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
