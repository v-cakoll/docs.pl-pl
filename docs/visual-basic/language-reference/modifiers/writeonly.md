---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="888fd-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="888fd-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="888fd-103">Określa, że właściwości mogą być zapisane, ale nie do odczytu.</span><span class="sxs-lookup"><span data-stu-id="888fd-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="888fd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="888fd-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="888fd-105">Reguły</span><span class="sxs-lookup"><span data-stu-id="888fd-105">Rules</span></span>  
 <span data-ttu-id="888fd-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="888fd-106">**Declaration Context.**</span></span> <span data-ttu-id="888fd-107">Można użyć `WriteOnly` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="888fd-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="888fd-108">Oznacza to, że w kontekście deklaracji `WriteOnly` właściwość musi być klasą, strukturą lub modułu i nie może być plik źródłowy, przestrzeni nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="888fd-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="888fd-109">Można zadeklarować właściwości jako `WriteOnly`, ale nie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="888fd-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="888fd-110">Kiedy należy używać WriteOnly</span><span class="sxs-lookup"><span data-stu-id="888fd-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="888fd-111">Czasami ma odbierającą kod, aby można było ustawić wartość, ale nie odnajdzie co to jest.</span><span class="sxs-lookup"><span data-stu-id="888fd-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="888fd-112">Na przykład poufnych danych, takich jak numer rejestracji społecznościowych lub hasło, musi być chronione przed dostępem przez każdego składnika, który nie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="888fd-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="888fd-113">W takich przypadkach można użyć `WriteOnly` właściwości można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="888fd-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="888fd-114">Po zdefiniowaniu i użyj `WriteOnly` właściwość, należy wziąć pod uwagę następujące dodatkowe środki zabezpieczające:</span><span class="sxs-lookup"><span data-stu-id="888fd-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="888fd-115">**Zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="888fd-115">**Overriding.**</span></span> <span data-ttu-id="888fd-116">Jeśli właściwość jest elementem członkowskim klasy, zezwolenie na domyślnie [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), a nie deklaruj `Overridable` lub `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="888fd-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="888fd-117">Zapobiega to wprowadzania niepożądanych dostępu za pomocą zastąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="888fd-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="888fd-118">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="888fd-118">**Access Level.**</span></span> <span data-ttu-id="888fd-119">Właściwości poufne dane są przechowywane w jedną lub więcej zmiennych, zadeklarować je [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) tak, aby żadnego innego kodu można uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="888fd-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="888fd-120">**Szyfrowanie.**</span><span class="sxs-lookup"><span data-stu-id="888fd-120">**Encryption.**</span></span> <span data-ttu-id="888fd-121">Przechowywane są wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="888fd-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="888fd-122">Jeśli złośliwy kod w jakiś sposób uzyska dostęp do tego obszaru pamięci, jest trudniej należy użyć danych.</span><span class="sxs-lookup"><span data-stu-id="888fd-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="888fd-123">Szyfrowanie jest również przydatne, jeśli jest konieczne do serializowania danych poufnych.</span><span class="sxs-lookup"><span data-stu-id="888fd-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="888fd-124">**Resetowanie.**</span><span class="sxs-lookup"><span data-stu-id="888fd-124">**Resetting.**</span></span> <span data-ttu-id="888fd-125">Klasy, struktury lub modułu definiowania właściwość zostało zakończone, zresetowanie poufne dane do wartości domyślnych lub inne wartości znaczenia.</span><span class="sxs-lookup"><span data-stu-id="888fd-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="888fd-126">Daje to dodatkowej ochrony, gdy ten obszar pamięci zostanie zwolniona ogólne dostępu.</span><span class="sxs-lookup"><span data-stu-id="888fd-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="888fd-127">**Trwałość.**</span><span class="sxs-lookup"><span data-stu-id="888fd-127">**Persistence.**</span></span> <span data-ttu-id="888fd-128">Nie są zachowywane poufnych danych, na przykład na dysku, jeśli można go uniknąć.</span><span class="sxs-lookup"><span data-stu-id="888fd-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="888fd-129">Ponadto nie zapisuj żadnych poufnych danych do Schowka.</span><span class="sxs-lookup"><span data-stu-id="888fd-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="888fd-130">`WriteOnly` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="888fd-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="888fd-131">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="888fd-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="888fd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="888fd-132">See Also</span></span>  
 [<span data-ttu-id="888fd-133">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="888fd-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="888fd-134">Prywatne</span><span class="sxs-lookup"><span data-stu-id="888fd-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="888fd-135">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="888fd-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
