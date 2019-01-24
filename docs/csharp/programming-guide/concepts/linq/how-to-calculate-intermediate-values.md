---
title: 'Instrukcje: Obliczanie wartości pośrednich (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 12c8a87114859ce7b47b8206acb454cdc2838470
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604334"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Instrukcje: Obliczanie wartości pośrednich (C#)
W tym przykładzie przedstawiono sposób obliczania wartości pośrednich, które mogą być używane w sortowania, filtrowania i wybierając opcję.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Let` klauzuli.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).  
  
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
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe zapytania (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
