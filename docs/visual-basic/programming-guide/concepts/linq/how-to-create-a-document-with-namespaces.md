---
title: 'Porady: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499929"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="5423f-102">Porady: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5423f-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5423f-103">W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeniami nazw w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5423f-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="5423f-104">Przy użyciu literałów XML w Visual Basic, użytkownicy mogą definiować jednej domyślnej globalnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5423f-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="5423f-105">Ta przestrzeń nazw jest domyślny obszar nazw dla literały XML i właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="5423f-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="5423f-106">Domyślny obszar nazw XML można definiować na poziomie projektu lub na poziomie plików.</span><span class="sxs-lookup"><span data-stu-id="5423f-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="5423f-107">Jeśli jest zdefiniowana na poziomie plików, zastępuje ona domyślny obszar nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="5423f-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="5423f-108">Można również zdefiniować inne przestrzenie nazw i określić prefiksy przestrzeni nazw dla tych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="5423f-109">Zdefiniować domyślne obszary nazw i przestrzeni nazw z prefiksem przy użyciu `Imports` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5423f-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="5423f-110">Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="5423f-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="5423f-111">Należy pamiętać, że domyślny obszar nazw XML ma zastosowanie tylko do elementów, a nie atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5423f-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="5423f-112">Atrybuty są domyślnie zawsze w żadnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="5423f-113">Jednak umożliwia prefiks przestrzeni nazw umieść atrybut w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5423f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5423f-114">Example</span></span>  
 <span data-ttu-id="5423f-115">Ten przykład tworzy dokument, który zawiera przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="5423f-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5423f-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5423f-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5423f-117">Example</span></span>  
 <span data-ttu-id="5423f-118">Ten przykład tworzy dokument, który zawiera dwie przestrzenie nazw, z których jedna jest domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="5423f-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5423f-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5423f-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5423f-120">Example</span></span>  
 <span data-ttu-id="5423f-121">Poniższy przykład tworzy dokument, który zawiera wiele przestrzeni nazw, obie z prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="5423f-122">Podczas serializacji drzewa XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z potrzebami, tak, aby każdy element jest w jej wyznaczoną przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5423f-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="5423f-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5423f-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5423f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5423f-124">See Also</span></span>  
 [<span data-ttu-id="5423f-125">Praca z przestrzeniami nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5423f-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
