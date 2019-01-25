---
title: Tworzenie atrybutów niestandardowych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 4bc60e20d163c6aec231152940f548fcb58442f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526356"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="64051-102">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64051-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="64051-103">Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która pochodzi bezpośrednio lub pośrednio z <xref:System.Attribute>, co sprawia, że identyfikowanie definicji atrybutów w metadanych jest łatwe i szybkie.</span><span class="sxs-lookup"><span data-stu-id="64051-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="64051-104">Załóżmy, że chcesz typy tag o nazwie programisty, który napisał typu.</span><span class="sxs-lookup"><span data-stu-id="64051-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="64051-105">Można zdefiniować niestandardowy `Author` klasy atrybutu:</span><span class="sxs-lookup"><span data-stu-id="64051-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="64051-106">Nazwa klasy jest nazwą atrybutu `Author`.</span><span class="sxs-lookup"><span data-stu-id="64051-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="64051-107">Jest pochodną `System.Attribute`, więc jest klasą atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="64051-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="64051-108">Parametry Konstruktora są parametry pozycyjne atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="64051-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="64051-109">W tym przykładzie `name` jest parametr pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="64051-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="64051-110">Właściwości lub pola publiczne odczytu / zapisu czy nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="64051-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="64051-111">W tym przypadku `version` tylko nosi nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="64051-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="64051-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby wprowadzić `Author` atrybut jest prawidłowy tylko w klasie i `Structure` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="64051-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="64051-113">Można użyć tego nowego atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="64051-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="64051-114">`AttributeUsage` został nazwany parametr `AllowMultiple`, dzięki którym możesz ustawić atrybutu niestandardowego jednorazowych lub multiuse —.</span><span class="sxs-lookup"><span data-stu-id="64051-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="64051-115">W poniższym przykładzie kodu multiuse — atrybut jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="64051-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="64051-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="64051-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="64051-117">Jeśli atrybut klasy zawiera właściwości, ta właściwość musi być odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="64051-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64051-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64051-118">See also</span></span>
- <xref:System.Reflection>
- [<span data-ttu-id="64051-119">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64051-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="64051-120">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="64051-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="64051-121">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64051-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="64051-122">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64051-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="64051-123">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64051-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="64051-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64051-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
