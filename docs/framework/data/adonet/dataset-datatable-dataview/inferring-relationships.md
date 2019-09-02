---
title: Wnioskowanie relacji
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204770"
---
# <a name="inferring-relationships"></a>Wnioskowanie relacji
Jeśli element, który jest wywnioskowany jako tabela, ma element podrzędny, który jest również wywnioskowany jako tabela, <xref:System.Data.DataRelation> zostanie utworzony między dwiema tabelami. Nowa kolumna o nazwie **ParentTableName_Id** zostanie dodana do tabeli utworzonej dla elementu nadrzędnego, a tabela utworzona dla elementu podrzędnego. Właściwość **ColumnMapping** tej kolumny tożsamości zostanie ustawiona na wartość MappingType **. Hidden**. Kolumna będzie przerastać klucz podstawowy dla tabeli nadrzędnej i będzie używana dla **relacji** między tymi dwiema tabelami. Typem danych kolumny dodanej tożsamości będzie **System. Int32**, w przeciwieństwie do typu danych wszystkich innych wywnioskowanych kolumn, które jest **System. String**. Element <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** również zostanie utworzony przy użyciu nowej kolumny w tabeli nadrzędnej i podrzędnej.  
  
 Rozważmy na przykład następujący kod XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces wnioskowania spowoduje utworzenie dwóch tabel: **Element1** i **ChildElement1**.  
  
 Tabela **element1** będzie zawierać dwie kolumny: **Element1_Id** i **ChildElement2**. Właściwość **ColumnMapping** kolumny **Element1_Id** zostanie ustawiona na wartość **MappingType. Hidden**. Właściwość **ColumnMapping** kolumny **ChildElement2** zostanie ustawiona na wartość **MappingType. element**. Kolumna **Element1_Id** zostanie ustawiona jako klucz podstawowy tabeli **element1** .  
  
 Tabela **ChildElement1** będzie miała trzy kolumny: **attr1**, **attr2** i **Element1_Id**. Właściwość **ColumnMapping** dla kolumn **attr1** i **Attr2** zostanie ustawiona na wartość MappingType **. Attribute**. Właściwość **ColumnMapping** kolumny **Element1_Id** zostanie ustawiona na wartość **MappingType. Hidden**.  
  
 **Relacje** i **element ForeignKeyConstraint** zostaną utworzone przy użyciu kolumn **Element1_Id** z obu tabel.  
  
 **Zestawu** DocumentElement  
  
 **Tabele** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Tabele** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|sekwencj|wartość2|0|  
  
 **DataRelation** Element1_ChildElement1  
  
 **Element nadrzędny:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **Elementy podrzędne:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Zagnieżdża** Prawda  
  
 **Element ForeignKeyConstraint** Element1_ChildElement1  
  
 **Kolumna** Element1_Id  
  
 **Element nadrzędny:** Element1  
  
 **Elementy podrzędne:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:** Brak  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Zagnieżdżanie elementów DataRelation](nesting-datarelations.md)
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
