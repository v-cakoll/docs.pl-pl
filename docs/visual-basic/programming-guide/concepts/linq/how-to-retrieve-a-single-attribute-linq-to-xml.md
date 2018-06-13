---
title: 'Porady: pobieranie jeden atrybut (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: e9e4dce95e9c3202b1cd2a53c186126deac0913c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642965"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="06d98-102">Porady: pobieranie jeden atrybut (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06d98-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="06d98-103">W tym temacie wyjaśniono, jak pobrać jeden atrybut elementu jest podana nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="06d98-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="06d98-104">Jest to przydatne dla wyrażeń zapytania, które chcesz znaleźć element, który ma określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="06d98-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="06d98-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metody <xref:System.Xml.Linq.XElement> klasy zwraca <xref:System.Xml.Linq.XAttribute> o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="06d98-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d98-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="06d98-106">Example</span></span>  
 <span data-ttu-id="06d98-107">W poniższym przykładzie użyto <xref:System.Xml.Linq.XElement.Attribute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06d98-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="06d98-108">W tym przykładzie znajduje wszystkie elementy podrzędne w drzewie o nazwie `Phone`, a następnie znalezienie atrybutu o nazwie `type`.</span><span class="sxs-lookup"><span data-stu-id="06d98-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="06d98-109">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="06d98-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="06d98-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="06d98-110">Example</span></span>  
 <span data-ttu-id="06d98-111">Jeśli chcesz pobrać wartość atrybutu można rzutować, podobnie jak w przypadku z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="06d98-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="06d98-112">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="06d98-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="06d98-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="06d98-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="06d98-114"> zawiera operatory jawnego rzutowania <xref:System.Xml.Linq.XAttribute> klasy do `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`i `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="06d98-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d98-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="06d98-115">Example</span></span>  
 <span data-ttu-id="06d98-116">Poniższy przykład przedstawia ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06d98-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="06d98-117">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="06d98-117">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="06d98-118">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="06d98-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="06d98-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06d98-119">See Also</span></span>  
 [<span data-ttu-id="06d98-120">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06d98-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
