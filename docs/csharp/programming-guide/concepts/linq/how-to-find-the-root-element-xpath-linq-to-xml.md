---
title: Jak znaleźć element główny (XPath-LINQ to XML) (C#)
description: Ten przykład w języku C# porównuje wyrażenie XPath LINQ to XML, aby uzyskać element główny dla przykładowego dokumentu XML.
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105190"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Jak znaleźć element główny (XPath-LINQ to XML) (C#)
W tym temacie pokazano, jak uzyskać element główny przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Wyrażenie XPath:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie elementu głównego.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
PurchaseOrders  
```  
