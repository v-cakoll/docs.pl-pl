---
title: 'Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 71e66791b41e26ea13f828ef6239a8db9a9365b0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835004"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="2c624-102">Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c624-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="2c624-103">Aby napisać zapytanie dotyczące kodu XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają prawidłową przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="2c624-104">W Visual Basic, najbardziej typowym podejściem jest zdefiniowanie globalnej przestrzeni nazw, a następnie użycie literałów XML i właściwości XML, które używają globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="2c624-105">Można zdefiniować globalną domyślną przestrzeń nazw, w której elementy case w literałach XML będą domyślnie w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="2c624-106">Alternatywnie można zdefiniować globalną przestrzeń nazw z prefiksem, a następnie użyć prefiksu zgodnie z wymaganiami w literałach XML i we właściwościach XML.</span><span class="sxs-lookup"><span data-stu-id="2c624-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="2c624-107">Podobnie jak w przypadku innych form XML, atrybuty są zawsze domyślnie w żadnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="2c624-108">Pierwszy zestaw przykładów w tym temacie przedstawia sposób tworzenia drzewa XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="2c624-109">Drugi zestaw pokazuje, jak utworzyć drzewo XML w przestrzeni nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="2c624-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c624-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c624-110">Example</span></span>  
 <span data-ttu-id="2c624-111">Poniższy przykład tworzy drzewo XML, który znajduje się w domyślnym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="2c624-112">Następnie pobiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="2c624-112">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="2c624-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2c624-113">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="2c624-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c624-114">Example</span></span>  
 <span data-ttu-id="2c624-115">W Visual Basic jednak zapisywanie zapytań w drzewie XML, który używa przestrzeni nazw z prefiksem, jest zupełnie inne niż wykonywanie zapytań względem drzewa XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2c624-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="2c624-116">Zwykle używasz instrukcji `Imports`, aby zaimportować przestrzeń nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="2c624-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="2c624-117">Następnie użyj prefiksu w nazwach elementów i atrybutów podczas konstruowania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2c624-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="2c624-118">Należy również użyć prefiksu podczas wykonywania zapytania w drzewie XML przy użyciu właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="2c624-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="2c624-119">Poniższy przykład tworzy drzewo XML, który znajduje się w przestrzeni nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="2c624-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="2c624-120">Następnie pobiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="2c624-120">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="2c624-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2c624-121">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c624-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c624-122">See also</span></span>

- [<span data-ttu-id="2c624-123">Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c624-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
