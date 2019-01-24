---
title: 'Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 00dfc4e14c38357deb3efc4a32fd00a97f6010b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609933"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="e7a89-102">Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7a89-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="e7a89-103">Aby napisać zapytanie na języku XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="e7a89-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="e7a89-104">W języku Visual Basic najbardziej typowym podejściem jest zdefiniowanie globalnej przestrzeni nazw, a następnie użyj literały XML i właściwości XML, które używają globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7a89-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="e7a89-105">Można określić domyślnej globalnej przestrzeni nazw, w którym to przypadku elementy w literałach XML będzie się w przestrzeni nazw, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e7a89-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="e7a89-106">Alternatywnie można zdefiniować globalnej przestrzeni nazw z prefiksem, a następnie użyć prefiksu zgodnie z potrzebami w literałach XML i właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="e7a89-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="e7a89-107">Podobnie jak w przypadku innych form XML atrybuty są zawsze w żadnej przestrzeni nazw, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e7a89-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="e7a89-108">Pierwszy zestaw przykładów w tym temacie przedstawiono sposób tworzenia drzewa XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7a89-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="e7a89-109">Drugi zestaw przedstawia sposób tworzenia drzewa XML w przestrzeni nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="e7a89-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a89-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7a89-110">Example</span></span>  
 <span data-ttu-id="e7a89-111">Poniższy przykład tworzy drzewa XML, który znajduje się w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7a89-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="e7a89-112">Pobiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="e7a89-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e7a89-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e7a89-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="e7a89-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7a89-114">Example</span></span>  
 <span data-ttu-id="e7a89-115">W języku Visual Basic, Pisanie zapytań w drzewie XML, który używa przestrzeni nazw z prefiksem bardzo różni się od zapytania drzewa XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7a89-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="e7a89-116">Zazwyczaj używają `Imports` instrukcję, aby zaimportować obszar nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="e7a89-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="e7a89-117">Następnie należy użyć prefiksu w nazwach elementów i atrybutów podczas konstruowania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="e7a89-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="e7a89-118">Możesz także użyć prefiksu, podczas wykonywania zapytania drzewa XML przy użyciu właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="e7a89-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="e7a89-119">Poniższy przykład tworzy drzewa XML, który znajduje się w przestrzeni nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="e7a89-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="e7a89-120">Pobiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="e7a89-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e7a89-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e7a89-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7a89-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7a89-122">See also</span></span>
- [<span data-ttu-id="e7a89-123">Praca z przestrzeniami nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7a89-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
