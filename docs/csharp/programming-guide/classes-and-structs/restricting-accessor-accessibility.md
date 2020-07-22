---
title: Ograniczanie dostępności metody dostępu — Przewodnik programowania w języku C#
description: Metody dostępu get i set właściwości w języku C# mają ten sam poziom widoczności lub dostępu domyślnie, jak właściwość, do której należą. Można ograniczyć dostęp.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 18fd1d58dc6125b5180118b2e0d3edc885a4b971
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863971"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="60a01-104">Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="60a01-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="60a01-105">Fragmenty [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) właściwości lub indeksatora są nazywane metodyą *dostępu*.</span><span class="sxs-lookup"><span data-stu-id="60a01-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="60a01-106">Domyślnie te metody dostępu mają ten sam poziom widoczności lub dostępu do właściwości lub indeksatora, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="60a01-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="60a01-107">Aby uzyskać więcej informacji, zobacz [poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="60a01-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="60a01-108">Jednak czasami warto ograniczyć dostęp do jednego z tych metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="60a01-109">Zazwyczaj obejmuje to ograniczenie dostępności `set` metody dostępu, zachowując `get` publicznie dostępną metodę dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="60a01-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="60a01-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="60a01-111">W tym przykładzie właściwość o nazwie `Name` definiuje `get` a i `set` akcesor.</span><span class="sxs-lookup"><span data-stu-id="60a01-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="60a01-112">`get`Metoda dostępu odbiera poziom dostępności samej właściwości, `public` w tym przypadku, gdy `set` metoda dostępu jest jawnie ograniczona przez zastosowanie modyfikatora dostępu [chronionego](../../language-reference/keywords/protected.md) do samej metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="60a01-113">Ograniczenia dotyczące modyfikatorów dostępu w przypadku metod dostępu</span><span class="sxs-lookup"><span data-stu-id="60a01-113">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="60a01-114">Używanie modyfikatorów metody dostępu we właściwościach lub indeksatorach podlega następujących warunkom:</span><span class="sxs-lookup"><span data-stu-id="60a01-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="60a01-115">Nie można używać modyfikatorów metody dostępu dla interfejsu lub jawnej implementacji elementu członkowskiego [interfejsu](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60a01-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="60a01-116">Modyfikatory metody dostępu można używać tylko wtedy, gdy właściwość lub indeksator ma zarówno metody `set` dostępu, jak i `get` .</span><span class="sxs-lookup"><span data-stu-id="60a01-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="60a01-117">W takim przypadku modyfikator jest dozwolony tylko dla jednego z dwóch metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="60a01-118">Jeśli właściwość lub indeksator ma modyfikator [przesłonięcia](../../language-reference/keywords/override.md) , modyfikator metody dostępu musi być zgodny z akcesorem przesłoniętej metody dostępu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="60a01-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="60a01-119">Poziom dostępności na metodzie dostępu musi być bardziej restrykcyjny niż poziom dostępności właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="60a01-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="60a01-120">Modyfikatory dostępu podczas zastępowania metod dostępu</span><span class="sxs-lookup"><span data-stu-id="60a01-120">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="60a01-121">Podczas przesłonięcia właściwości lub indeksatora zastępowane metody dostępu muszą być dostępne dla zastępujący kod.</span><span class="sxs-lookup"><span data-stu-id="60a01-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="60a01-122">Ponadto dostępność właściwości/indeksatora i jego metod dostępu musi być zgodna z odpowiadającą jej przesłoniętą właściwością/indeksatorem oraz jej metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="60a01-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="60a01-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="60a01-124">Implementowanie interfejsów</span><span class="sxs-lookup"><span data-stu-id="60a01-124">Implementing Interfaces</span></span>  
 <span data-ttu-id="60a01-125">W przypadku użycia metody dostępu do zaimplementowania interfejsu metoda dostępu może nie mieć modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="60a01-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="60a01-126">Jednak w przypadku zaimplementowania interfejsu przy użyciu jednej metody dostępu, takiej jak `get` , inna metoda dostępu może mieć Modyfikator dostęp, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="60a01-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="60a01-127">Domena dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="60a01-127">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="60a01-128">Jeśli używasz modyfikatora dostępu do akcesora, [domena dostępności](../../language-reference/keywords/accessibility-domain.md) metody dostępu jest określana przez ten modyfikator.</span><span class="sxs-lookup"><span data-stu-id="60a01-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="60a01-129">Jeśli nie używasz modyfikatora dostępu do akcesora, domena dostępności metody dostępu jest określana na podstawie poziomu dostępności właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="60a01-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60a01-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="60a01-130">Example</span></span>  
 <span data-ttu-id="60a01-131">Poniższy przykład zawiera trzy klasy, `BaseClass` , `DerivedClass` , i `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="60a01-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="60a01-132">Istnieją dwie właściwości w `BaseClass` `Name` i `Id` dla obu klas.</span><span class="sxs-lookup"><span data-stu-id="60a01-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="60a01-133">W przykładzie pokazano, jak Właściwość `Id` włączona `DerivedClass` może być ukryta przez właściwość `Id` w `BaseClass` przypadku używania ograniczonego modyfikatora dostępu, takiego jak [Protected](../../language-reference/keywords/protected.md) lub [Private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="60a01-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="60a01-134">W związku z tym podczas przypisywania wartości do tej właściwości `BaseClass` zamiast niej wywoływana jest właściwość klasy.</span><span class="sxs-lookup"><span data-stu-id="60a01-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="60a01-135">Zastąpienie modyfikatora dostępu [publicznego](../../language-reference/keywords/public.md) spowoduje udostępnienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="60a01-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="60a01-136">W przykładzie pokazano również, że restrykcyjny modyfikator dostępu, taki jak `private` lub `protected` , w `set` metodzie dostępu `Name` właściwości w programie `DerivedClass` uniemożliwia dostęp do akcesora i generuje błąd podczas przypisywania do niego.</span><span class="sxs-lookup"><span data-stu-id="60a01-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="60a01-137">Komentarze</span><span class="sxs-lookup"><span data-stu-id="60a01-137">Comments</span></span>  
 <span data-ttu-id="60a01-138">Zwróć uwagę, że w przypadku zastąpienia deklaracji `new private string Id` przez, otrzymujesz `new public string Id` dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="60a01-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="60a01-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60a01-139">See also</span></span>

- [<span data-ttu-id="60a01-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="60a01-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="60a01-141">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60a01-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="60a01-142">Indexers (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="60a01-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="60a01-143">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="60a01-143">Access Modifiers</span></span>](./access-modifiers.md)
