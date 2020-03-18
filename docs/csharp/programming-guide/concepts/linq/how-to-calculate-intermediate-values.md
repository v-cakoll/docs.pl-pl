---
title: Jak obliczyć wartości pośrednie (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141450"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Jak obliczyć wartości pośrednie (C#)
W tym przykładzie pokazano, jak obliczyć wartości pośrednie, które mogą być używane do sortowania, filtrowania i wybierania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Let` klauzuli.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Dane numeryczne (LINQ do XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Dane liczbowe w obszarze nazw](./sample-xml-file-numerical-data-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
