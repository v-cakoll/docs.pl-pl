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
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829032"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="19079-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19079-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="19079-103">Określa, że właściwości mogą być zapisywane, ale nie do odczytu.</span><span class="sxs-lookup"><span data-stu-id="19079-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19079-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19079-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="19079-105">reguły</span><span class="sxs-lookup"><span data-stu-id="19079-105">Rules</span></span>  
 <span data-ttu-id="19079-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="19079-106">**Declaration Context.**</span></span> <span data-ttu-id="19079-107">Możesz użyć `WriteOnly` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="19079-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="19079-108">Oznacza to, że kontekst deklaracji `WriteOnly` właściwość musi być klasy, struktury lub modułu i nie może być plikiem źródłowym, przestrzeń nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="19079-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="19079-109">Można zadeklarować właściwości jako `WriteOnly`, ale nie zmienną.</span><span class="sxs-lookup"><span data-stu-id="19079-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="19079-110">Kiedy należy używać WriteOnly</span><span class="sxs-lookup"><span data-stu-id="19079-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="19079-111">Czasami kod konsumencki, aby można było ustawić wartość, ale nie zobaczyć, jakie go.</span><span class="sxs-lookup"><span data-stu-id="19079-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="19079-112">Na przykład dane poufne, takie jak numer rejestracji społecznościowych lub hasła, muszą być chronione przed dostępem przez dowolny składnik, który nie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="19079-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="19079-113">W takich przypadkach można użyć `WriteOnly` właściwość można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="19079-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19079-114">Podczas definiowania i stosowania `WriteOnly` właściwość, należy wziąć pod uwagę następujące dodatkowe środki zabezpieczające:</span><span class="sxs-lookup"><span data-stu-id="19079-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="19079-115">**Zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="19079-115">**Overriding.**</span></span> <span data-ttu-id="19079-116">Jeśli właściwość jest składową klasy, zezwalała na domyślnie [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), a nie deklaruj `Overridable` lub `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="19079-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="19079-117">Uniemożliwia to wprowadzanie niepożądany dostęp za pomocą zastąpienia przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="19079-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="19079-118">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="19079-118">**Access Level.**</span></span> <span data-ttu-id="19079-119">Jeśli przytrzymasz właściwości poufnych danych w jednej lub więcej zmiennych je zadeklarować [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) tak, aby żadnego innego kodu można uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="19079-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="19079-120">**Encryption.**</span><span class="sxs-lookup"><span data-stu-id="19079-120">**Encryption.**</span></span> <span data-ttu-id="19079-121">Store wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="19079-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="19079-122">Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, jest trudniejsze użyć danych.</span><span class="sxs-lookup"><span data-stu-id="19079-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="19079-123">Szyfrowanie jest również przydatne, jeśli to konieczne do serializowania danych poufnych.</span><span class="sxs-lookup"><span data-stu-id="19079-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="19079-124">**Resetowanie.**</span><span class="sxs-lookup"><span data-stu-id="19079-124">**Resetting.**</span></span> <span data-ttu-id="19079-125">Klasy, struktury lub modułu definiowania właściwość zostanie przerwany, zresetowanie danych poufnych do wartości domyślnych lub inne wartości bez znaczenia.</span><span class="sxs-lookup"><span data-stu-id="19079-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="19079-126">Zapewnia dodatkową ochronę, gdy ten obszar pamięci jest zwalniana dla ogólnego dostępu.</span><span class="sxs-lookup"><span data-stu-id="19079-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="19079-127">**Trwałość.**</span><span class="sxs-lookup"><span data-stu-id="19079-127">**Persistence.**</span></span> <span data-ttu-id="19079-128">Nie są zachowywane poufnych danych, na przykład na dysku, jeśli można go uniknąć.</span><span class="sxs-lookup"><span data-stu-id="19079-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="19079-129">Ponadto nie wpisuj poufnych danych do Schowka.</span><span class="sxs-lookup"><span data-stu-id="19079-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="19079-130">`WriteOnly` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="19079-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="19079-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="19079-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="19079-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19079-132">See also</span></span>

- [<span data-ttu-id="19079-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="19079-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="19079-134">Private</span><span class="sxs-lookup"><span data-stu-id="19079-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="19079-135">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="19079-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
