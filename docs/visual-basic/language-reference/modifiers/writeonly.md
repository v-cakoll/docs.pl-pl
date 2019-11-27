---
title: WriteOnly
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
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344190"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="425cc-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="425cc-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="425cc-103">Określa, że właściwość może być zapisywana, ale nie do odczytu.</span><span class="sxs-lookup"><span data-stu-id="425cc-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="425cc-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="425cc-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="425cc-105">Reguły</span><span class="sxs-lookup"><span data-stu-id="425cc-105">Rules</span></span>  
 <span data-ttu-id="425cc-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="425cc-106">**Declaration Context.**</span></span> <span data-ttu-id="425cc-107">`WriteOnly` można używać tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="425cc-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="425cc-108">Oznacza to, że kontekst deklaracji właściwości `WriteOnly` musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="425cc-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="425cc-109">Można zadeklarować właściwość jako `WriteOnly`, ale nie dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="425cc-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="425cc-110">Kiedy używać WriteOnly</span><span class="sxs-lookup"><span data-stu-id="425cc-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="425cc-111">Czasami kod zużywający ma mieć możliwość ustawienia wartości, ale nie Odkryj, co to jest.</span><span class="sxs-lookup"><span data-stu-id="425cc-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="425cc-112">Na przykład dane poufne, takie jak numer rejestracji społecznościowej lub hasło, muszą być chronione przed dostępem przez dowolny składnik, który go nie ustawił.</span><span class="sxs-lookup"><span data-stu-id="425cc-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="425cc-113">W takich przypadkach można użyć właściwości `WriteOnly`, aby ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="425cc-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="425cc-114">Podczas definiowania i używania właściwości `WriteOnly` należy wziąć pod uwagę następujące dodatkowe środki ochronne:</span><span class="sxs-lookup"><span data-stu-id="425cc-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="425cc-115">**Zastępuje.**</span><span class="sxs-lookup"><span data-stu-id="425cc-115">**Overriding.**</span></span> <span data-ttu-id="425cc-116">Jeśli właściwość jest członkiem klasy, zezwól jej na wartość domyślną [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)i nie deklaruj jej `Overridable` ani `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="425cc-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="425cc-117">Zapobiega to niepożądanemu dostępowi klasy pochodnej przez przesłonięcie.</span><span class="sxs-lookup"><span data-stu-id="425cc-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="425cc-118">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="425cc-118">**Access Level.**</span></span> <span data-ttu-id="425cc-119">Jeśli przechowujesz poufne dane właściwości w co najmniej jednej zmiennej, zadeklaruj je jako [prywatne](../../../visual-basic/language-reference/modifiers/private.md) , aby żaden inny kod nie mógł uzyskać do nich dostępu.</span><span class="sxs-lookup"><span data-stu-id="425cc-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="425cc-120">**Szyfrowania.**</span><span class="sxs-lookup"><span data-stu-id="425cc-120">**Encryption.**</span></span> <span data-ttu-id="425cc-121">Przechowuj wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="425cc-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="425cc-122">Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, trudno jest wykorzystać dane.</span><span class="sxs-lookup"><span data-stu-id="425cc-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="425cc-123">Szyfrowanie jest również przydatne, jeśli jest konieczne do serializacji poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="425cc-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="425cc-124">**Resetowanie.**</span><span class="sxs-lookup"><span data-stu-id="425cc-124">**Resetting.**</span></span> <span data-ttu-id="425cc-125">Gdy Klasa, struktura lub moduł definiujący właściwość jest przerywana, zresetuj dane poufne do wartości domyślnych lub innych wartości bez znaczenia.</span><span class="sxs-lookup"><span data-stu-id="425cc-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="425cc-126">Zapewnia to dodatkową ochronę, gdy ten obszar pamięci jest bezpłatny do uzyskania dostępu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="425cc-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="425cc-127">**Trwałość.**</span><span class="sxs-lookup"><span data-stu-id="425cc-127">**Persistence.**</span></span> <span data-ttu-id="425cc-128">Nie Utrwalaj poufnych danych, na przykład na dysku, jeśli można je uniknąć.</span><span class="sxs-lookup"><span data-stu-id="425cc-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="425cc-129">Ponadto nie należy zapisywać poufnych danych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="425cc-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="425cc-130">Modyfikator `WriteOnly` może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="425cc-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="425cc-131">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="425cc-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="425cc-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="425cc-132">See also</span></span>

- [<span data-ttu-id="425cc-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="425cc-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="425cc-134">Private</span><span class="sxs-lookup"><span data-stu-id="425cc-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="425cc-135">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="425cc-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
