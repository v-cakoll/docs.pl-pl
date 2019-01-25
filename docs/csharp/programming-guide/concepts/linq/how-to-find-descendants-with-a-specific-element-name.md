---
title: 'Instrukcje: Wyszukiwanie elementów potomnych o określonej nazwie elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 11f13dfc61e837a923cb9709301d89ff6d2149dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530392"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="021fd-102">Instrukcje: Wyszukiwanie elementów potomnych o określonej nazwie elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="021fd-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="021fd-103">Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="021fd-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="021fd-104">Można napisać kod, aby wykonać iterację przez wszystkie elementy podrzędne, ale jest łatwiejszy w obsłudze <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="021fd-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="021fd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="021fd-105">Example</span></span>  
 <span data-ttu-id="021fd-106">Poniższy przykład pokazuje, jak można znaleźć elementy podrzędne na podstawie nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="021fd-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="021fd-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="021fd-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="021fd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="021fd-108">Example</span></span>  
 <span data-ttu-id="021fd-109">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="021fd-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="021fd-110">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="021fd-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="021fd-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="021fd-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="021fd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="021fd-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="021fd-113">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="021fd-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
