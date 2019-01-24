---
title: Podsumowanie procesu wnioskowania schematu zestawu danych
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1eb12fd9c983bc0013b5dc528e0b3389250bdbe2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527656"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Podsumowanie procesu wnioskowania schematu zestawu danych
Procesu wnioskowania najpierw określi, z dokumentu XML, które elementy zostanie wywnioskowany, jako tabele. Z pozostałych pliku XML procesu wnioskowania Określa kolumny dla tych tabel. W przypadku zagnieżdżonych tabel generuje procesu wnioskowania zagnieżdżonych <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiektów.  
  
 Poniżej przedstawiono krótkie podsumowanie reguły wnioskowania:  
  
-   Elementy, które mają atrybuty są wnioskowane jako tabele.  
  
-   Elementy, które mają elementy podrzędne są wnioskowane jako tabele.  
  
-   Elementy, które powtarzają się wywnioskować jako pojedynczą tabelę.  
  
-   Jeśli element dokumentu lub katalogu głównego, ma żadnych atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, jest wnioskowany jako <xref:System.Data.DataSet>. W przeciwnym razie element dokumentu jest wnioskowany w postaci tabeli.  
  
-   Atrybuty są wnioskowane jako kolumny.  
  
-   Elementów, które mają nie atrybutów lub elementów podrzędnych i nie powtórzyć, są wnioskowane jako kolumny.  
  
-   Dla elementów, które są wnioskowane jako zagnieżdżoną tabelę w obrębie innych elementów, które również są wnioskowane jako tabele, zagnieżdżoną **DataRelation** utworzeniu między dwiema tabelami. Nowy, podstawowej kolumny klucza o nazwie **TableName_Id** jest dodawane do obu tabel i używana przez **DataRelation**. A **ForeignKeyConstraint** jest tworzony między dwiema tabelami, za pomocą **TableName_Id** kolumny.  
  
-   Dla elementów, które są wnioskowane jako tabele i który zawiera tekst, ale mieć żadnych elementów podrzędnych, nową kolumnę o nazwie **TableName_Text** jest tworzona dla poszczególnych elementów tekstu. Jeśli element jest wnioskowany w postaci tabeli i zawiera tekst, ale ma również elementy podrzędne, tekst zostanie zignorowany.  
  
## <a name="see-also"></a>Zobacz także
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
