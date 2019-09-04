---
title: 'Instrukcje: Znajdź element podrzędny (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: bf0eac1e6d3a5c1c80269cb5bf3502ca51a4a6b0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253879"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź element podrzędny (XPath-LINQ to XML) (C#)
W tym temacie porównano oś elementu podrzędnego XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z <xref:System.Xml.Linq.XContainer.Element%2A> metodą.  
  
 Wyrażenie XPath ma `DeliveryNotes`wartość.  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie elementu `DeliveryNotes`podrzędnego.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  