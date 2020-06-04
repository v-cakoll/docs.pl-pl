---
title: 'Instrukcje: wyszukiwanie elementu o określonym elemencie podrzędnym'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405290"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="76a5a-102">Instrukcje: Znajdowanie elementu z określonym elementem podrzędnym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76a5a-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="76a5a-103">W tym temacie pokazano, jak znaleźć konkretny element, który ma element podrzędny o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="76a5a-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76a5a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="76a5a-104">Example</span></span>  
 <span data-ttu-id="76a5a-105">Przykład znajduje `Test` element, który ma `CommandLine` element podrzędny o wartości "EXAMP2. exe".</span><span class="sxs-lookup"><span data-stu-id="76a5a-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="76a5a-106">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="76a5a-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="76a5a-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="76a5a-107">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
 <span data-ttu-id="76a5a-108">Należy zauważyć, że w tym przykładzie jest stosowana [Właściwość osi elementu podrzędnego XML](../../../language-reference/xml-axis/xml-child-axis-property.md), [Właściwość osi atrybutu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)i [właściwość wartość XML](../../../language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="76a5a-108">Note that this example uses the [XML Child axis property](../../../language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76a5a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="76a5a-109">Example</span></span>  
 <span data-ttu-id="76a5a-110">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="76a5a-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="76a5a-111">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="76a5a-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="76a5a-112">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testowa w przestrzeni nazw](sample-xml-file-test-configuration-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="76a5a-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="76a5a-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="76a5a-113">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="76a5a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76a5a-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="76a5a-115">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76a5a-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="76a5a-116">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76a5a-116">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="76a5a-117">Operacje projekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76a5a-117">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
