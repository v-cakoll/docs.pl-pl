---
title: 'Porady: Tworzenie dokumentu z przestrzeni nazw (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643081"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="f29a7-102">Porady: Tworzenie dokumentu z przestrzeni nazw (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f29a7-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f29a7-103">W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeni nazw w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f29a7-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="f29a7-104">Przy użyciu literałów XML w Visual Basic, użytkownicy mogą definiować jedną globalnego domyślnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="f29a7-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="f29a7-105">Ta przestrzeń nazw jest domyślny obszar nazw dla literałów XML i właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="f29a7-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="f29a7-106">Domyślna przestrzeń nazw XML można zdefiniować na poziomie projektu lub poziomie plików.</span><span class="sxs-lookup"><span data-stu-id="f29a7-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="f29a7-107">Jeśli jest zdefiniowana na poziomie plików, zastępuje on domyślnej przestrzeni nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="f29a7-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="f29a7-108">Można również zdefiniować innych przestrzeniach nazw i określić prefiksy przestrzeni nazw dla tych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="f29a7-109">Zdefiniuj zarówno domyślne obszary nazw, jak i przestrzeni nazw z prefiksem przy użyciu `Imports` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f29a7-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="f29a7-110">Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="f29a7-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="f29a7-111">Należy pamiętać, że domyślna przestrzeń nazw XML ma zastosowanie tylko do elementów, a nie do atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f29a7-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="f29a7-112">Atrybuty są domyślnie zawsze w bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="f29a7-113">Jednak można prefiks przestrzeni nazw umieść atrybut w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f29a7-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f29a7-114">Example</span></span>  
 <span data-ttu-id="f29a7-115">W tym przykładzie tworzy dokument, który zawiera przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f29a7-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f29a7-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f29a7-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="f29a7-117">Example</span></span>  
 <span data-ttu-id="f29a7-118">W tym przykładzie tworzy dokument, który zawiera dwie przestrzenie nazw, z których jeden jest domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="f29a7-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f29a7-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f29a7-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="f29a7-120">Example</span></span>  
 <span data-ttu-id="f29a7-121">Poniższy przykład tworzy dokument, który zawiera wiele obszarów nazw, zarówno z prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="f29a7-122">Podczas serializowania drzewo XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z wymaganiami, dzięki czemu każdy element znajduje się w wyznaczonym przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f29a7-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="f29a7-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f29a7-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f29a7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f29a7-124">See Also</span></span>  
 [<span data-ttu-id="f29a7-125">Praca z przestrzeni nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f29a7-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
