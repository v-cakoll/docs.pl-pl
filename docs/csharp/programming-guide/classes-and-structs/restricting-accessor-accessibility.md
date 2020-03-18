---
title: Ograniczanie ułatwień dostępu — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: a332fef814f0c81914eb7b8c308de68f719fbaac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714694"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="d82ee-102">Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d82ee-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="d82ee-103">[Get](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) części właściwości lub indeksatora są nazywane *akcesorów*.</span><span class="sxs-lookup"><span data-stu-id="d82ee-103">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="d82ee-104">Domyślnie te akcesory mają taką samą widoczność lub poziom dostępu właściwości lub indeksatora, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="d82ee-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="d82ee-105">Aby uzyskać więcej informacji, zobacz [poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d82ee-105">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="d82ee-106">Jednak czasami warto ograniczyć dostęp do jednego z tych akcesorów.</span><span class="sxs-lookup"><span data-stu-id="d82ee-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="d82ee-107">Zazwyczaj wiąże się to z ograniczeniem dostępności `set` akcesora, przy jednoczesnym zachowaniu `get` akcesor publicznie dostępne.</span><span class="sxs-lookup"><span data-stu-id="d82ee-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="d82ee-108">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d82ee-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="d82ee-109">W tym przykładzie właściwość `Name` o `get` nazwie `set` definiuje a i akcesor.</span><span class="sxs-lookup"><span data-stu-id="d82ee-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="d82ee-110">Akcesor `get` odbiera poziom ułatwień `public` dostępu samej właściwości, w tym przypadku, podczas gdy `set` akcesor jest jawnie ograniczony przez zastosowanie modyfikatora dostępu [chronionego](../../language-reference/keywords/protected.md) do samego akcesora.</span><span class="sxs-lookup"><span data-stu-id="d82ee-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="d82ee-111">Ograniczenia dotyczące modyfikatorów dostępu w programach akcesorów</span><span class="sxs-lookup"><span data-stu-id="d82ee-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="d82ee-112">Korzystanie modyfikatorów akcesora na właściwości lub indeksatorów podlega następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="d82ee-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="d82ee-113">Nie można użyć modyfikatorów akcesora w interfejsie lub implementacji elementu członkowskiego [interfejsu](../../language-reference/keywords/interface.md) jawnego.</span><span class="sxs-lookup"><span data-stu-id="d82ee-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="d82ee-114">Modyfikatory akcesora można używać tylko `set` `get` wtedy, gdy właściwość lub indeksator ma zarówno i akcesorów.</span><span class="sxs-lookup"><span data-stu-id="d82ee-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="d82ee-115">W takim przypadku modyfikator jest dozwolone tylko na jednym z dwóch akcesorów.</span><span class="sxs-lookup"><span data-stu-id="d82ee-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="d82ee-116">Jeśli właściwość lub indeksator ma modyfikator [zastępowania,](../../language-reference/keywords/override.md) modyfikator akcesormusi odpowiadać akcesor akcesor, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="d82ee-116">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="d82ee-117">Poziom ułatwień dostępu na akcesor musi być bardziej restrykcyjne niż poziom ułatwień dostępu na właściwości lub indeksatora się.</span><span class="sxs-lookup"><span data-stu-id="d82ee-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="d82ee-118">Modyfikatory dostępu na zalegające akcesory</span><span class="sxs-lookup"><span data-stu-id="d82ee-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="d82ee-119">Po zastąpieniu właściwości lub indeksatora, zastąpione akcesory muszą być dostępne dla kodu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d82ee-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="d82ee-120">Ponadto dostępność zarówno właściwości/indeksatora i jego akcesorów musi odpowiadać odpowiedniej właściwości zastąpione/indeksator i jego akcesorów.</span><span class="sxs-lookup"><span data-stu-id="d82ee-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="d82ee-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d82ee-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="d82ee-122">Implementowanie interfejsów</span><span class="sxs-lookup"><span data-stu-id="d82ee-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="d82ee-123">Korzystając z akcesora do zaimplementowania interfejsu, akcesor może nie mieć modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="d82ee-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="d82ee-124">Jednak jeśli zaimplementujesz interfejs przy użyciu `get`jednego akcesora, takich jak , inny akcesor może mieć modyfikator dostępu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d82ee-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="d82ee-125">Domena ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="d82ee-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="d82ee-126">Jeśli używasz modyfikatora dostępu na akcesor, [domena ułatwień dostępu](../../language-reference/keywords/accessibility-domain.md) jest określana przez ten modyfikator.</span><span class="sxs-lookup"><span data-stu-id="d82ee-126">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="d82ee-127">Jeśli nie używasz modyfikatora dostępu w akcesorze, domena ułatwień dostępu jest określana przez poziom ułatwień dostępu właściwości lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="d82ee-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82ee-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d82ee-128">Example</span></span>  
 <span data-ttu-id="d82ee-129">Poniższy przykład zawiera trzy `BaseClass` `DerivedClass`klasy, `MainClass`, , i .</span><span class="sxs-lookup"><span data-stu-id="d82ee-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="d82ee-130">Istnieją dwie właściwości na `BaseClass` `Name` , `Id` i na obu klasach.</span><span class="sxs-lookup"><span data-stu-id="d82ee-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="d82ee-131">W przykładzie pokazano, `Id` `DerivedClass` jak właściwość na `Id` mogą `BaseClass` być ukryte przez właściwość podczas korzystania z modyfikatora dostępu restrykcyjnego, takich jak [chronione](../../language-reference/keywords/protected.md) lub [prywatne](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="d82ee-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="d82ee-132">W związku z tym po przypisaniu `BaseClass` wartości do tej właściwości, właściwość na klasy jest wywoływana zamiast.</span><span class="sxs-lookup"><span data-stu-id="d82ee-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="d82ee-133">Zastąpienie modyfikatora dostępu [publicznie](../../language-reference/keywords/public.md) spowoduje, że właściwość będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="d82ee-133">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="d82ee-134">W przykładzie pokazano również, że modyfikator dostępu `set` ograniczającego, `Name` takich `DerivedClass` jak `private` lub `protected`, na akcesor właściwości w uniemożliwia dostęp do akcesora i generuje błąd po przypisaniu do niego.</span><span class="sxs-lookup"><span data-stu-id="d82ee-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="d82ee-135">Komentarze</span><span class="sxs-lookup"><span data-stu-id="d82ee-135">Comments</span></span>  
 <span data-ttu-id="d82ee-136">Należy zauważyć, że `new private string Id` jeśli `new public string Id`zastąpisz deklarację przez , otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d82ee-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="d82ee-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d82ee-137">See also</span></span>

- [<span data-ttu-id="d82ee-138">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d82ee-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d82ee-139">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d82ee-139">Properties</span></span>](./properties.md)
- <span data-ttu-id="d82ee-140">[Indexers](../indexers/index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="d82ee-140">[Indexers](../indexers/index.md)</span></span>
- [<span data-ttu-id="d82ee-141">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="d82ee-141">Access Modifiers</span></span>](./access-modifiers.md)
