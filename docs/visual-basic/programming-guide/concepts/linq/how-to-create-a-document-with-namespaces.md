---
title: 'Instrukcje: tworzenie dokumentu z przestrzeniami nazw (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: a440c9d810798eb5ebd025a336cbb17fface23b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414637"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="7e65c-102">Instrukcje: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e65c-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7e65c-103">W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeniami nazw w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7e65c-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="7e65c-104">W przypadku używania literałów XML w Visual Basic użytkownicy mogą definiować jedną globalną domyślną przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7e65c-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="7e65c-105">Ta przestrzeń nazw jest domyślną przestrzenią nazw dla literałów XML i właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="7e65c-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="7e65c-106">Domyślną przestrzeń nazw XML można zdefiniować na poziomie projektu lub na poziomie pliku.</span><span class="sxs-lookup"><span data-stu-id="7e65c-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="7e65c-107">Jeśli jest zdefiniowany na poziomie pliku, zastępuje domyślny obszar nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="7e65c-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="7e65c-108">Można również zdefiniować inne przestrzenie nazw i określić prefiksy przestrzeni nazw dla tych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="7e65c-109">Można zdefiniować zarówno domyślne przestrzenie nazw, jak i przestrzenie nazw z prefiksem za pomocą `Imports` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7e65c-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="7e65c-110">Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="7e65c-110">For more information, see [Introduction to XML Literals in Visual Basic](introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="7e65c-111">Należy zauważyć, że domyślna przestrzeń nazw XML dotyczy tylko elementów i nie do atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7e65c-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="7e65c-112">Atrybuty są domyślnie zawsze w obszarze brak przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="7e65c-113">Można jednak użyć prefiksu przestrzeni nazw, aby umieścić atrybut w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e65c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e65c-114">Example</span></span>  
 <span data-ttu-id="7e65c-115">Ten przykład tworzy dokument zawierający przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="7e65c-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7e65c-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="7e65c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e65c-117">Example</span></span>  
 <span data-ttu-id="7e65c-118">W tym przykładzie tworzony jest dokument zawierający dwie przestrzenie nazw, z których jedna jest domyślną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="7e65c-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7e65c-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="7e65c-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e65c-120">Example</span></span>  
 <span data-ttu-id="7e65c-121">Poniższy przykład tworzy dokument zawierający wiele przestrzeni nazw, zarówno z prefiksami przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="7e65c-122">Podczas serializowania drzewa XML program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z wymaganiami, aby każdy element był w wyznaczeniu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7e65c-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="7e65c-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7e65c-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e65c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e65c-124">See also</span></span>

- [<span data-ttu-id="7e65c-125">Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e65c-125">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
