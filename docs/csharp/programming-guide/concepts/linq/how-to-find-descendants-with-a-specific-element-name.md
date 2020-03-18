---
title: Jak znaleźć elementy podrzędne o nazwie określonego elementu (C#)
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: b3200a2fdf75dbf52079a2b3d27aa1a88d313406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141083"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="e026a-102">Jak znaleźć elementy podrzędne o nazwie określonego elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="e026a-102">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="e026a-103">Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e026a-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="e026a-104">Można napisać kod do iterate przez wszystkie elementy podrzędne, <xref:System.Xml.Linq.XContainer.Descendants%2A> ale łatwiej jest użyć osi.</span><span class="sxs-lookup"><span data-stu-id="e026a-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e026a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e026a-105">Example</span></span>  
 <span data-ttu-id="e026a-106">W poniższym przykładzie pokazano, jak znaleźć elementy podrzędne na podstawie nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="e026a-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="e026a-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e026a-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="e026a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e026a-108">Example</span></span>  
 <span data-ttu-id="e026a-109">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="e026a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e026a-110">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e026a-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e026a-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e026a-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e026a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e026a-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
