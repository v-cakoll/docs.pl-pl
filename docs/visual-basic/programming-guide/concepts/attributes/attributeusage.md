---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400735"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="ce70f-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce70f-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="ce70f-103">Określa, w jaki sposób można używać klasy atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ce70f-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="ce70f-104">`AttributeUsage`jest atrybutem, który można zastosować do definicji atrybutów niestandardowych w celu kontrolowania, jak można zastosować nowy atrybut.</span><span class="sxs-lookup"><span data-stu-id="ce70f-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="ce70f-105">Ustawienia domyślne wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="ce70f-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="ce70f-106">W tym przykładzie `NewAttribute` Klasa może być stosowana do dowolnej jednostki kodu, która może być stosowana tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="ce70f-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="ce70f-107">Jest dziedziczona przez klasy pochodne w przypadku zastosowania do klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="ce70f-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="ce70f-108">`AllowMultiple`Argumenty i `Inherited` są opcjonalne, więc ten kod ma ten sam skutek:</span><span class="sxs-lookup"><span data-stu-id="ce70f-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="ce70f-109">Pierwszy `AttributeUsage` argument musi być co najmniej jednym elementem <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ce70f-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="ce70f-110">Z operatorem OR można łączyć wiele typów docelowych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="ce70f-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="ce70f-111">Jeśli `AllowMultiple` argument jest ustawiony na `true` , wówczas atrybut otrzymany można zastosować więcej niż raz do pojedynczej jednostki, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="ce70f-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="ce70f-112">W takim przypadku `MultiUseAttr` można je zastosować wielokrotnie `AllowMultiple` , ponieważ jest ustawiona na `true` .</span><span class="sxs-lookup"><span data-stu-id="ce70f-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="ce70f-113">Oba formaty wyświetlane na potrzeby stosowania wielu atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="ce70f-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="ce70f-114">Jeśli `Inherited` jest ustawiona na `false` , atrybut nie jest dziedziczony przez klasy, które pochodzą z klasy, która ma atrybut.</span><span class="sxs-lookup"><span data-stu-id="ce70f-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="ce70f-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ce70f-115">For example:</span></span>

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

<span data-ttu-id="ce70f-116">W tym przypadku `Attr1` nie ma zastosowania do `DClass` dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="ce70f-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce70f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce70f-117">Remarks</span></span>

<span data-ttu-id="ce70f-118">`AttributeUsage`Atrybut jest atrybutem o pojedynczym użyciu — nie można go zastosować więcej niż raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="ce70f-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="ce70f-119">`AttributeUsage`jest aliasem dla <xref:System.AttributeUsageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ce70f-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="ce70f-120">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="ce70f-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="ce70f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce70f-121">Example</span></span>

<span data-ttu-id="ce70f-122">Poniższy przykład ilustruje efekt `Inherited` `AllowMultiple` argumentów i do `AttributeUsage` atrybutu oraz sposób wyliczania atrybutów niestandardowych zastosowanych do klasy.</span><span class="sxs-lookup"><span data-stu-id="ce70f-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="ce70f-123">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ce70f-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="ce70f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce70f-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="ce70f-125">Przewodnik programowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce70f-125">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="ce70f-126">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce70f-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="ce70f-127">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce70f-127">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="ce70f-128">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce70f-128">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="ce70f-129">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce70f-129">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="ce70f-130">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce70f-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
