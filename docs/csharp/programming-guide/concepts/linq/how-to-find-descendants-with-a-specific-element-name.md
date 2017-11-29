---
title: "Porady: znajdowanie elementów podrzędnych o nazwie określonego elementu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b1cc45f07accd7ae6dcc530f0fd5a9078bce949d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="76dc5-102">Porady: znajdowanie elementów podrzędnych o nazwie określonego elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="76dc5-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="76dc5-103">Czasami chcesz znaleźć wszystkich elementów podrzędnych o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="76dc5-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="76dc5-104">Można napisać kod, aby wykonać iterację wszystkich elementów podrzędnych, ale jest łatwiejsze w <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="76dc5-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76dc5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="76dc5-105">Example</span></span>  
 <span data-ttu-id="76dc5-106">Poniższy przykład pokazuje, jak można znaleźć elementów podrzędnych na podstawie nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="76dc5-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="76dc5-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="76dc5-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="76dc5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="76dc5-108">Example</span></span>  
 <span data-ttu-id="76dc5-109">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="76dc5-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="76dc5-110">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="76dc5-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="76dc5-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="76dc5-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="76dc5-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76dc5-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="76dc5-113">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76dc5-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
