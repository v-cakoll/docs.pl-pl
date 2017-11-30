---
title: Ograniczenia wnioskowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a>Ograniczenia wnioskowania
Proces wnioskowanie <xref:System.Data.DataSet> schematu z pliku XML może spowodować schematy różne w zależności od elementów XML do każdego dokumentu. Rozważmy na przykład w następujących dokumentach XML.  
  
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
  
 Dla "Dokument1," tworzy proces wnioskowania **DataSet** o nazwie "DocumentElement" i tabeli o nazwie "Element1", ponieważ powtarzający się element "Element1".  
  
 **Zestaw danych:** DocumentElement  
  
 **Tabela:** Element1  
  
|Element1_Text|  
|--------------------|  
|Tekst1|  
|Tekst2|  
  
 Jednak dla "Document2," proces wnioskowania tworzy **DataSet** o nazwie "NewDataSet" i tabeli o nazwie "DocumentElement". "Element1" jest wywnioskowany jako kolumny, ponieważ ma ona żadnych atrybutów i elementów podrzędnych.  
  
 **Zestaw danych:** NewDataSet  
  
 **Tabela:** DocumentElement  
  
|Element1|  
|--------------|  
|Tekst1|  
  
 Te dwa dokumenty XML mogą przeznaczone do tworzenia tego samego schematu, ale proces wnioskowania daje różne wyniki, oparte na elementy zawarte w każdej dokumentu.  
  
 Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, firma Microsoft zaleca, jawnie określ schemat przy użyciu języka definicji schematu XML (XSD) lub danych XML (XDR) podczas ładowania **DataSet** z KOD XML. Aby uzyskać więcej informacji na temat jawne określenie **DataSet** schematu ze schematem XML, zobacz [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Ładowanie informacji o schemacie zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Za pomocą języka XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
