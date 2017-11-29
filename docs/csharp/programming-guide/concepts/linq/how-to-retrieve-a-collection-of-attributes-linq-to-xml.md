---
title: "Porady: pobierania kolekcję atrybutów (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 165c807735bfc73375d4ddec125786750ad08ad1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Porady: pobierania kolekcję atrybutów (LINQ do XML) (C#)
W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Ta metoda pobiera atrybuty elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do iterowania po kolekcji atrybutów elementu.  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
