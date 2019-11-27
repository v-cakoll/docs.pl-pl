---
title: Tworzenie atrybutów niestandardowych
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 773a3e8e974f37a1554892dd3441c115681c5bae
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350143"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="ee1e7-102">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1e7-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="ee1e7-103">Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute>, co umożliwia szybkie i łatwe identyfikowanie definicji atrybutów w metadanych.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="ee1e7-104">Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="ee1e7-105">Można zdefiniować niestandardową klasę atrybutów `Author`:</span><span class="sxs-lookup"><span data-stu-id="ee1e7-105">You might define a custom `Author` attribute class:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

<span data-ttu-id="ee1e7-106">Nazwa klasy jest nazwą atrybutu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="ee1e7-107">Jest ona pochodną `System.Attribute`, więc jest klasą atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="ee1e7-108">Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="ee1e7-109">W tym przykładzie `name` jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="ee1e7-110">Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="ee1e7-111">W tym przypadku `version` jest jedynym parametrem nazwanym.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="ee1e7-112">Zwróć uwagę na użycie atrybutu `AttributeUsage`, aby atrybut `Author` był prawidłowy tylko w deklaracjach klasy i `Structure`.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="ee1e7-113">Tego nowego atrybutu można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee1e7-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="ee1e7-114">`AttributeUsage` ma nazwany parametr `AllowMultiple`, za pomocą którego można utworzyć atrybut niestandardowy pojedynczy lub Multiuse.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="ee1e7-115">W poniższym przykładzie kodu tworzony jest atrybut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="ee1e7-116">W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="ee1e7-117">Jeśli Klasa atrybutu zawiera właściwość, ta właściwość musi mieć wartość Read-Write.</span><span class="sxs-lookup"><span data-stu-id="ee1e7-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee1e7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee1e7-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="ee1e7-119">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee1e7-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="ee1e7-120">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="ee1e7-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="ee1e7-121">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1e7-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="ee1e7-122">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1e7-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="ee1e7-123">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1e7-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="ee1e7-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1e7-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
