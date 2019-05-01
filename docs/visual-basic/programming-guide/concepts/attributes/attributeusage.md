---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 1841171f2f3fc26ba9244c72c69960b765d39807
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789119"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="128e2-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128e2-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="128e2-103">Określa, jak używać klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="128e2-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="128e2-104">`AttributeUsage` jest atrybutem, którego może odnosić się do definicji atrybutów niestandardowych do kontrolowania, jak można zastosować nowy atrybut.</span><span class="sxs-lookup"><span data-stu-id="128e2-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="128e2-105">Po zastosowaniu jawnie, domyślne ustawienia wyglądała następująco:</span><span class="sxs-lookup"><span data-stu-id="128e2-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="128e2-106">W tym przykładzie `NewAttribute` klasy mogą być stosowane do dowolnej jednostki kodu atrybutu można, ale mogą być stosowane tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="128e2-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="128e2-107">Jest dziedziczone przez klasy pochodne, gdy jest stosowany do klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="128e2-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="128e2-108">`AllowMultiple` i `Inherited` argumenty są opcjonalne, dlatego ten kod działa tak samo:</span><span class="sxs-lookup"><span data-stu-id="128e2-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="128e2-109">Pierwszy `AttributeUsage` argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="128e2-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="128e2-110">Wiele typów docelowej mogą być połączone razem z operatora OR, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="128e2-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="128e2-111">Jeśli `AllowMultiple` argument ma wartość `true`, a następnie wynikowy atrybut można stosować więcej niż jeden raz na pojedynczej jednostce, np. to:</span><span class="sxs-lookup"><span data-stu-id="128e2-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 <span data-ttu-id="128e2-112">W tym przypadku `MultiUseAttr` mogą być stosowane wielokrotnie, ponieważ `AllowMultiple` ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="128e2-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="128e2-113">Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="128e2-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="128e2-114">Jeśli `Inherited` ustawiono `false`, a następnie ten atrybut nie jest dziedziczone przez klasy, które są uzyskiwane z klasą, która jest przypisana.</span><span class="sxs-lookup"><span data-stu-id="128e2-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="128e2-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="128e2-115">For example:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 <span data-ttu-id="128e2-116">W tym przypadku `Attr1` nie ma zastosowania do `DClass` za pomocą dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="128e2-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="128e2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="128e2-117">Remarks</span></span>  
 <span data-ttu-id="128e2-118">`AttributeUsage` Atrybut jest atrybutem jednorazowy — nie można zastosować w więcej niż jeden raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="128e2-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="128e2-119">`AttributeUsage` jest aliasem <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="128e2-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="128e2-120">Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="128e2-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="128e2-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="128e2-121">Example</span></span>  
 <span data-ttu-id="128e2-122">Poniższy przykład ilustruje efekt `Inherited` i `AllowMultiple` argumenty `AttributeUsage` atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="128e2-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a><span data-ttu-id="128e2-123">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="128e2-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="128e2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="128e2-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="128e2-125">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="128e2-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="128e2-126">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="128e2-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="128e2-127">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128e2-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="128e2-128">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128e2-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="128e2-129">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128e2-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="128e2-130">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128e2-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
