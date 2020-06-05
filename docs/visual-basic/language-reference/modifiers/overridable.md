---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392122"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="82602-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82602-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="82602-103">Określa, że właściwość lub procedura może być zastąpiona przez właściwość lub procedurę o identycznej nazwie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="82602-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82602-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82602-104">Remarks</span></span>  
 <span data-ttu-id="82602-105">`Overridable`Modyfikator zezwala na przesłanianie właściwości lub metody w klasie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="82602-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="82602-106">Modyfikator [NotOverridable](notoverridable.md) uniemożliwia przesłanianie właściwości lub metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="82602-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="82602-107">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="82602-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="82602-108">Jeśli `Overridable` modyfikator or `NotOverridable` nie jest określony, ustawienie domyślne zależy od tego, czy właściwość lub metoda przesłania właściwość lub metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="82602-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="82602-109">Jeśli właściwość lub metoda przesłania właściwość lub metodę klasy bazowej, ustawienie domyślne to `Overridable` ; w przeciwnym razie jest `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="82602-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="82602-110">Można wykonać cień lub przesłonięcie, aby ponownie zdefiniować Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="82602-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="82602-111">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="82602-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="82602-112">Element, który może być przesłonięty, jest czasami nazywany elementem *wirtualnym* .</span><span class="sxs-lookup"><span data-stu-id="82602-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="82602-113">Jeśli może być zastąpiony, ale nie musi być, jest również czasami nazywane *konkretnym* elementem.</span><span class="sxs-lookup"><span data-stu-id="82602-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="82602-114">Można użyć `Overridable` tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="82602-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="82602-115">Połączone Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="82602-115">Combined Modifiers</span></span>  
 <span data-ttu-id="82602-116">Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.</span><span class="sxs-lookup"><span data-stu-id="82602-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="82602-117">Nie można określić `Overridable` razem z `MustOverride` , `NotOverridable` , lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="82602-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="82602-118">Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` się z `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="82602-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="82602-119">Użycie</span><span class="sxs-lookup"><span data-stu-id="82602-119">Usage</span></span>  
 <span data-ttu-id="82602-120">`Overridable`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="82602-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="82602-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="82602-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="82602-122">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="82602-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="82602-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="82602-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="82602-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82602-124">See also</span></span>

- [<span data-ttu-id="82602-125">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="82602-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="82602-126">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="82602-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="82602-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="82602-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="82602-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="82602-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="82602-129">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="82602-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="82602-130">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="82602-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="82602-131">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82602-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
