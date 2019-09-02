---
title: Ograniczenia wnioskowania
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 4e0f63776162b60c9333ba47be58ea78a9b6805d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204833"
---
# <a name="inference-limitations"></a>Ograniczenia wnioskowania
Proces wywnioskowania <xref:System.Data.DataSet> schematu z XML może skutkować różnymi schematami w zależności od elementów XML w poszczególnych dokumentach. Rozważmy na przykład następujące dokumenty XML.  
  
 Document1  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 W przypadku "document1" proces wnioskowania tworzy **zestaw danych** o nazwie "DocumentElement" i tabelę o nazwie "element1", ponieważ "element1" jest elementem powtarzającym się.  
  
 **Zestawu** DocumentElement  
  
 **Tabele** Element1  
  
|Element1_Text|  
|--------------------|  
|Organizacji1|  
|Text2|  
  
 Jednak w przypadku "Document2" proces wnioskowania tworzy **zestaw danych** o nazwie "NewDataSet" i tabelę o nazwie "DocumentElement". Element "element1" jest wywnioskowany jako kolumna, ponieważ nie ma atrybutów ani elementów podrzędnych.  
  
 **Zestawu** NewDataSet  
  
 **Tabele** DocumentElement  
  
|Element1|  
|--------------|  
|Organizacji1|  
  
 Te dwa dokumenty XML mogą być przeznaczone do tworzenia tego samego schematu, ale proces wnioskowania generuje bardzo różne wyniki w zależności od elementów zawartych w każdym dokumencie.  
  
 Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, zalecamy jawnie określić schemat przy użyciu języka definicji schematu XML (XSD) lub XML-Data zredukowany (XDR) podczas ładowania **zestawu danych** z pliku XML. Aby uzyskać więcej informacji na temat jawnego określania schematu **zestawu danych** ze schematem XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
