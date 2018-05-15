---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: ae162c310511db160806501af895276a4a4bba5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="536c3-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536c3-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="536c3-103">Określa sposób użycia klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="536c3-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="536c3-104">`AttributeUsage` jest atrybut, który może odnosić się do definicji atrybutu niestandardowego do kontrolowania, jak można zastosować nowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="536c3-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="536c3-105">Po zastosowaniu jawnie, domyślne ustawienia następującą postać:</span><span class="sxs-lookup"><span data-stu-id="536c3-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="536c3-106">W tym przykładzie `NewAttribute` klasa może być stosowane do dowolnej jednostki kodu atrybutu można, ale mogą być stosowane tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="536c3-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="536c3-107">Zostało ono odziedziczone przez klas pochodnych po zastosowaniu do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="536c3-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="536c3-108">`AllowMultiple` i `Inherited` argumenty są opcjonalne, dlatego ten kod działa tak samo:</span><span class="sxs-lookup"><span data-stu-id="536c3-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="536c3-109">Pierwszy `AttributeUsage` argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="536c3-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="536c3-110">Wiele typów docelowy może odnosić się wraz z operatora OR w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="536c3-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="536c3-111">Jeśli `AllowMultiple` argument ma wartość `true`, następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="536c3-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="536c3-112">W takim przypadku `MultiUseAttr` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="536c3-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="536c3-113">Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="536c3-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="536c3-114">Jeśli `Inherited` ma ustawioną wartość `false`, a następnie ten atrybut nie jest dziedziczone przez klasy, które są pochodnymi klasy, która ma atrybut.</span><span class="sxs-lookup"><span data-stu-id="536c3-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="536c3-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="536c3-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="536c3-116">W takim przypadku `Attr1` nie ma zastosowania do `DClass` za pośrednictwem dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="536c3-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="536c3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="536c3-117">Remarks</span></span>  
 <span data-ttu-id="536c3-118">`AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="536c3-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="536c3-119">`AttributeUsage` alias jest <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="536c3-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="536c3-120">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="536c3-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="536c3-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="536c3-121">Example</span></span>  
 <span data-ttu-id="536c3-122">Poniższy przykład ilustruje efekt `Inherited` i `AllowMultiple` argumenty `AttributeUsage` atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="536c3-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="536c3-123">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="536c3-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="536c3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="536c3-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="536c3-125">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="536c3-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="536c3-126">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="536c3-126">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="536c3-127">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536c3-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="536c3-128">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536c3-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="536c3-129">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536c3-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="536c3-130">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536c3-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
