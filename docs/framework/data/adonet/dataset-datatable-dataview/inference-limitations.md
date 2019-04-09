---
title: Ograniczenia wnioskowania
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076246"
---
# <a name="inference-limitations"></a>Ograniczenia wnioskowania
Proces wnioskowanie <xref:System.Data.DataSet> schemat z pliku XML może spowodować różne schematy, w zależności od elementów XML w każdym dokumencie. Na przykład należy wziąć pod uwagę następujące dokumenty XML.  
  
 Dokument1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Dla "Dokument1", generuje procesu wnioskowania **DataSet** o nazwie "elementu DocumentElement" i tabeli o nazwie "Element1", ponieważ powtarzający się element "Element1".  
  
 **Zestaw danych:** Elementu DocumentElement  
  
 **Tabela:** element1  
  
|Element1_Text|  
|--------------------|  
|TEXT1|  
|Tekst2|  
  
 Jednak dla "Document2," procesu wnioskowania tworzy **DataSet** o nazwie "NewDataSet" i tabeli o nazwie "elementu DocumentElement". "Element1" jest wnioskowany jako kolumny, ponieważ zawiera ona żadnych atrybutów i nie elementy podrzędne.  
  
 **Zestaw danych:** NewDataSet  
  
 **Tabela:** Elementu DocumentElement  
  
|element1|  
|--------------|  
|TEXT1|  
  
 Tych dwóch dokumentów XML zostały przeznaczone do tworzenia ten sam schemat, ale procesu wnioskowania daje różne wyniki oparte na elementach zawartych w poszczególnych dokumentów.  
  
 Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, firma Microsoft zaleca, jawnie określ schemat przy użyciu języka definicji schematu XML (XSD) lub danych XML (XDR), podczas ładowania **DataSet** z PLIK XML. Aby uzyskać więcej informacji na temat jawne określenie **DataSet** schematu przy użyciu schematu XML, zobacz [elementu pochodnego dla zestawu danych relacyjnej struktury z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
