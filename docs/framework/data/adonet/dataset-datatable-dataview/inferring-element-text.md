---
title: Wnioskowanie tekstu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 3fdd110a14ddfd6065ed552171a8d76ef64e2fb5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784541"
---
# <a name="inferring-element-text"></a>Wnioskowanie tekstu elementu
Jeśli element zawiera tekst i nie ma żadnych elementów podrzędnych, które mają być wywnioskowane jako tabele (takie jak elementy z atrybutami lub powtarzalne elementy), Nowa kolumna o nazwie **TableName_Text** zostanie dodana do tabeli, która jest wywnioskowana dla elementu. Tekst zawarty w elemencie zostanie dodany do wiersza w tabeli i zapisany w nowej kolumnie. Właściwość **ColumnMapping** nowej kolumny zostanie ustawiona na wartość **MappingType. SimpleContent**.  
  
 Rozważmy na przykład następujący kod XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z dwiema kolumnami: **attr1** i **Element1_Text**. Właściwość **ColumnMapping** kolumny **attr1** zostanie ustawiona na wartość **MappingType. Attribute**. Właściwość **ColumnMapping** kolumny **Element1_Text** zostanie ustawiona na wartość **MappingType. SimpleContent**.  
  
 **Zestawu** DocumentElement  
  
 **Tabele** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|sekwencj|Organizacji1|  
  
 Jeśli element zawiera tekst, ale również zawiera elementy podrzędne, które zawierają tekst, kolumna nie zostanie dodana do tabeli w celu przechowania tekstu zawartego w elemencie. Tekst zawarty w elemencie zostanie zignorowany, podczas gdy tekst w elementach podrzędnych zostanie uwzględniony w wierszu w tabeli. Rozważmy na przykład następujący kod XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z jedną kolumną o nazwie **ChildElement1**. Tekst elementu **ChildElement1** zostanie uwzględniony w wierszu w tabeli. Drugi tekst zostanie zignorowany. Właściwość **ColumnMapping** kolumny **ChildElement1** zostanie ustawiona na wartość **MappingType. element**.  
  
 **Zestawu** DocumentElement  
  
 **Tabele** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
