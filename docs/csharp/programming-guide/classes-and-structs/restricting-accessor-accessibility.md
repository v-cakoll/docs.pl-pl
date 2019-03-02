---
title: Ograniczanie dostępności metody dostępu — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: c15b4939306b79f843b22dc808d88bf3d20ed555
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203707"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="7f378-102">Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7f378-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="7f378-103">[Uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustaw](../../../csharp/language-reference/keywords/set.md) noszą nazwę porcjach właściwości lub indeksatora *Akcesory*.</span><span class="sxs-lookup"><span data-stu-id="7f378-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="7f378-104">Domyślnie te metody dostępu mają ten sam poziom widoczności lub dostęp do właściwości lub indeksatora, do której należą.</span><span class="sxs-lookup"><span data-stu-id="7f378-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="7f378-105">Aby uzyskać więcej informacji, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7f378-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="7f378-106">Jednak czasami jest przydatne ograniczyć dostęp do jednej z tych metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="7f378-107">Zwykle wymaga to, ograniczenie dostępności `set` akcesor przy zachowaniu `get` publicznie dostępne metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="7f378-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f378-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="7f378-109">W tym przykładzie właściwość o nazwie `Name` definiuje `get` i `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="7f378-110">`get` Akcesor odbiera poziom ułatwień dostępu właściwości, `public` while, w tym przypadku `set` akcesor jawnie jest ograniczony przez zastosowanie [chronione](../../../csharp/language-reference/keywords/protected.md) modyfikator dostępu do Metoda dostępu sam.</span><span class="sxs-lookup"><span data-stu-id="7f378-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="7f378-111">Ograniczenia dotyczące modyfikatorów dostępu</span><span class="sxs-lookup"><span data-stu-id="7f378-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="7f378-112">Za pomocą modyfikatorów dostępu na właściwości i indeksatorów podlega tych warunków:</span><span class="sxs-lookup"><span data-stu-id="7f378-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="7f378-113">Nie można używać modyfikatorów dostępu na interfejs lub jawnie [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7f378-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="7f378-114">Modyfikatory dostępu można użyć tylko wtedy, gdy właściwość lub indeksator zarówno `set` i `get` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="7f378-115">W tym przypadku modyfikator jest dozwolona tylko na jednym z dwóch metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
-   <span data-ttu-id="7f378-116">Jeśli właściwość lub indeksator ma [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator, modyfikator dostępu muszą być zgodne dostępu przesłonięte metody dostępu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="7f378-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="7f378-117">Poziom dostępności metody dostępu musi być bardziej restrykcyjny niż poziom dostępności na właściwość lub indeksator sam.</span><span class="sxs-lookup"><span data-stu-id="7f378-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="7f378-118">Modyfikatory dostępu w przypadku przesłaniania metody dostępu</span><span class="sxs-lookup"><span data-stu-id="7f378-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="7f378-119">Gdy zastąpisz właściwość lub indeksator przesłoniętych metod dostępu muszą być dostępne dla kodu nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7f378-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="7f378-120">Ponadto dostępność właściwości/indeksatora i jego metod dostępu muszą być zgodne, odpowiedni zastąpione właściwości/indeksatora i jego metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="7f378-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f378-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="7f378-122">Implementowanie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7f378-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="7f378-123">Gdy używasz metody dostępu do zaimplementowania interfejsu akcesor nie może mieć modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="7f378-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="7f378-124">Jednak jeśli zaimplementować interfejs za pomocą jedną metodę dostępu, takich jak `get`, inne metody dostępu może mieć modyfikatora dostępu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f378-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="7f378-125">Domena dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="7f378-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="7f378-126">Użycie modyfikatora dostępu dla metody dostępu, [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md) metody dostępu jest określana przez ten modyfikator.</span><span class="sxs-lookup"><span data-stu-id="7f378-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="7f378-127">Jeśli nie użyto modyfikatora dostępu na akcesor, domena dostępności metody dostępu jest określany przez poziom ułatwień dostępu właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="7f378-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f378-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f378-128">Example</span></span>  
 <span data-ttu-id="7f378-129">Poniższy przykład zawiera trzy klasy `BaseClass`, `DerivedClass`, i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7f378-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="7f378-130">Istnieją dwie właściwości na `BaseClass`, `Name` i `Id` w obu klasach.</span><span class="sxs-lookup"><span data-stu-id="7f378-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="7f378-131">W przykładzie pokazano, jak właściwość `Id` na `DerivedClass` może być ukryta przez właściwość `Id` na `BaseClass` zastosowania modyfikatora dostępu ograniczające takich jak [chronione](../../../csharp/language-reference/keywords/protected.md) lub [ prywatne](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="7f378-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="7f378-132">W związku z tym, kiedy przypisujesz wartości tej właściwości, właściwość na `BaseClass` zamiast tego wywoływany jest klasa.</span><span class="sxs-lookup"><span data-stu-id="7f378-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="7f378-133">Modyfikator dostępu przez zastąpienie [publicznych](../../../csharp/language-reference/keywords/public.md) spowoduje, że właściwość dostępny.</span><span class="sxs-lookup"><span data-stu-id="7f378-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="7f378-134">W przykładzie pokazano również, modyfikator dostępu ograniczające, takich jak `private` lub `protected`na `set` akcesor `Name` właściwość `DerivedClass` uniemożliwia dostęp do metody dostępu i generuje błąd, po przypisaniu do go.</span><span class="sxs-lookup"><span data-stu-id="7f378-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="7f378-135">Komentarze</span><span class="sxs-lookup"><span data-stu-id="7f378-135">Comments</span></span>  
 <span data-ttu-id="7f378-136">Należy zauważyć, że jeżeli wymienisz deklaracji `new private string Id` przez `new public string Id`, otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7f378-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="7f378-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f378-137">See also</span></span>

- [<span data-ttu-id="7f378-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7f378-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7f378-139">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7f378-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="7f378-140">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="7f378-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="7f378-141">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="7f378-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
