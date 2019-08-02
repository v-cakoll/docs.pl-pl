---
title: 'Instrukcje: Znajdź elementy podrzędne z określoną nazwą elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: dbb955697e4d4b0ed5aad9c00c37e73bbd32b7b4
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709938"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="a5680-102">Instrukcje: Znajdź elementy podrzędne z określoną nazwą elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="a5680-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="a5680-103">Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a5680-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="a5680-104">Można napisać kod do iteracji przez wszystkie elementy podrzędne, ale łatwiej jest użyć <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="a5680-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5680-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5680-105">Example</span></span>  
 <span data-ttu-id="a5680-106">Poniższy przykład pokazuje, jak znaleźć elementy podrzędne na podstawie nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="a5680-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="a5680-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a5680-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="a5680-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5680-108">Example</span></span>  
 <span data-ttu-id="a5680-109">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a5680-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a5680-110">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a5680-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a5680-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a5680-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5680-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5680-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
