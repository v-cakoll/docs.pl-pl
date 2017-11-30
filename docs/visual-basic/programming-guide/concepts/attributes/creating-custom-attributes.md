---
title: "Tworzenie atrybutów niestandardowych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="261ed-102">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261ed-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="261ed-103">Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która jest pochodną bezpośrednio lub pośrednio <xref:System.Attribute>, która sprawia, że identyfikacji definicje atrybutów w metadanych szybkie i łatwe.</span><span class="sxs-lookup"><span data-stu-id="261ed-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="261ed-104">Załóżmy, że chcesz typów tagu o nazwie programisty autorze typu.</span><span class="sxs-lookup"><span data-stu-id="261ed-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="261ed-105">Możesz zdefiniować niestandardowy `Author` klasy atrybutu:</span><span class="sxs-lookup"><span data-stu-id="261ed-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="261ed-106">Nazwa klasy jest nazwa atrybutu `Author`.</span><span class="sxs-lookup"><span data-stu-id="261ed-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="261ed-107">Jest pochodną `System.Attribute`, co klasa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="261ed-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="261ed-108">Konstruktor parametry są parametry pozycyjne atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="261ed-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="261ed-109">W tym przykładzie `name` jest parametrów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="261ed-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="261ed-110">Parametry są nazwane właściwości lub pola publiczne odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="261ed-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="261ed-111">W takim przypadku `version` tylko nosi nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="261ed-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="261ed-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut jest prawidłowy tylko w klasie i `Structure` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="261ed-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="261ed-113">Ten nowy atrybut można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="261ed-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="261ed-114">`AttributeUsage`Nazwany parametr `AllowMultiple`, z której można utworzyć atrybutu niestandardowego, jednorazowych lub multiuse.</span><span class="sxs-lookup"><span data-stu-id="261ed-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="261ed-115">W poniższym przykładzie jest tworzony multiuse atrybutu.</span><span class="sxs-lookup"><span data-stu-id="261ed-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="261ed-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="261ed-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="261ed-117">Jeśli atrybut klasy zawiera właściwości, tej właściwości musi być do odczytu / zapisu.</span><span class="sxs-lookup"><span data-stu-id="261ed-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261ed-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="261ed-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="261ed-119">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="261ed-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="261ed-120">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="261ed-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="261ed-121">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261ed-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="261ed-122">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261ed-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="261ed-123">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261ed-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="261ed-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="261ed-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
