---
title: 'Instrukcje: Znajdź element główny (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1fea4cc630dd708a86a0f0595ac727f8b8fa40af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593370"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź element główny (XPath-LINQ to XML) (C#)
W tym temacie pokazano, jak uzyskać element główny przy użyciu XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]i.  
  
 Wyrażenie XPath:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie elementu głównego.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
```  
Results are identical  
PurchaseOrders  
```  
