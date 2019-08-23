---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963768"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="4adda-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4adda-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="4adda-103">Określa, że właściwość może być zapisywana, ale nie do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4adda-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4adda-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4adda-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4adda-105">Przepisy</span><span class="sxs-lookup"><span data-stu-id="4adda-105">Rules</span></span>  
 <span data-ttu-id="4adda-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="4adda-106">**Declaration Context.**</span></span> <span data-ttu-id="4adda-107">Można używać `WriteOnly` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="4adda-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="4adda-108">Oznacza to, że kontekst `WriteOnly` deklaracji właściwości musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="4adda-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="4adda-109">Właściwość można zadeklarować jako `WriteOnly`, ale nie zmienną.</span><span class="sxs-lookup"><span data-stu-id="4adda-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="4adda-110">Kiedy używać WriteOnly</span><span class="sxs-lookup"><span data-stu-id="4adda-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="4adda-111">Czasami kod zużywający ma mieć możliwość ustawienia wartości, ale nie Odkryj, co to jest.</span><span class="sxs-lookup"><span data-stu-id="4adda-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="4adda-112">Na przykład dane poufne, takie jak numer rejestracji społecznościowej lub hasło, muszą być chronione przed dostępem przez dowolny składnik, który go nie ustawił.</span><span class="sxs-lookup"><span data-stu-id="4adda-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="4adda-113">W takich przypadkach można użyć `WriteOnly` właściwości, aby ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="4adda-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4adda-114">Podczas definiowania i używania `WriteOnly` właściwości należy wziąć pod uwagę następujące dodatkowe środki ochronne:</span><span class="sxs-lookup"><span data-stu-id="4adda-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="4adda-115">**Zastępuje.**</span><span class="sxs-lookup"><span data-stu-id="4adda-115">**Overriding.**</span></span> <span data-ttu-id="4adda-116">Jeśli właściwość jest członkiem klasy, zezwól jej na wartość domyślną [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)i nie deklaruj `Overridable` ani. `MustOverride`</span><span class="sxs-lookup"><span data-stu-id="4adda-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="4adda-117">Zapobiega to niepożądanemu dostępowi klasy pochodnej przez przesłonięcie.</span><span class="sxs-lookup"><span data-stu-id="4adda-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="4adda-118">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="4adda-118">**Access Level.**</span></span> <span data-ttu-id="4adda-119">Jeśli przechowujesz poufne dane właściwości w co najmniej jednej zmiennej, zadeklaruj je jako [prywatne](../../../visual-basic/language-reference/modifiers/private.md) , aby żaden inny kod nie mógł uzyskać do nich dostępu.</span><span class="sxs-lookup"><span data-stu-id="4adda-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="4adda-120">**Szyfrowania.**</span><span class="sxs-lookup"><span data-stu-id="4adda-120">**Encryption.**</span></span> <span data-ttu-id="4adda-121">Przechowuj wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="4adda-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="4adda-122">Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, trudno jest wykorzystać dane.</span><span class="sxs-lookup"><span data-stu-id="4adda-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="4adda-123">Szyfrowanie jest również przydatne, jeśli jest konieczne do serializacji poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="4adda-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="4adda-124">**Resetowanie.**</span><span class="sxs-lookup"><span data-stu-id="4adda-124">**Resetting.**</span></span> <span data-ttu-id="4adda-125">Gdy Klasa, struktura lub moduł definiujący właściwość jest przerywana, zresetuj dane poufne do wartości domyślnych lub innych wartości bez znaczenia.</span><span class="sxs-lookup"><span data-stu-id="4adda-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="4adda-126">Zapewnia to dodatkową ochronę, gdy ten obszar pamięci jest bezpłatny do uzyskania dostępu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4adda-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="4adda-127">**Trwałość.**</span><span class="sxs-lookup"><span data-stu-id="4adda-127">**Persistence.**</span></span> <span data-ttu-id="4adda-128">Nie Utrwalaj poufnych danych, na przykład na dysku, jeśli można je uniknąć.</span><span class="sxs-lookup"><span data-stu-id="4adda-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="4adda-129">Ponadto nie należy zapisywać poufnych danych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="4adda-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="4adda-130">`WriteOnly` Modyfikator może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="4adda-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="4adda-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="4adda-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4adda-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4adda-132">See also</span></span>

- [<span data-ttu-id="4adda-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="4adda-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="4adda-134">Private</span><span class="sxs-lookup"><span data-stu-id="4adda-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="4adda-135">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4adda-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
