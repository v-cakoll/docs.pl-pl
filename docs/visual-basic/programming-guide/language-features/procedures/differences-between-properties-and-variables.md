---
title: "Różnice pomiędzy właściwościami i zmiennymi w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="65756-102">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65756-102">Differences Between Properties and Variables in Visual Basic</span></span>
<span data-ttu-id="65756-103">Zmienne i właściwości reprezentują wartości, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="65756-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="65756-104">Istnieją różnice w pamięci masowej i implementacji.</span><span class="sxs-lookup"><span data-stu-id="65756-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="65756-105">Zmienne</span><span class="sxs-lookup"><span data-stu-id="65756-105">Variables</span></span>  
 <span data-ttu-id="65756-106">A *zmiennej* odpowiada bezpośrednio do lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="65756-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="65756-107">Należy zdefiniować zmienną z instrukcją jednej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="65756-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="65756-108">Może być zmienną *zmiennej lokalnej*, zdefiniowane wewnątrz procedury i jest dostępny tylko w ramach tej procedury, lub można ją *zmiennej członkowskiej*, zdefiniowane w module, klasy lub struktury, ale nie znajduje się w dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="65756-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="65756-109">Zmiennej członkowskiej jest również nazywany *pola*.</span><span class="sxs-lookup"><span data-stu-id="65756-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="65756-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-110">Properties</span></span>  
 <span data-ttu-id="65756-111">A *właściwości* jest elementem dane zdefiniowane dla modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="65756-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="65756-112">Definiuje właściwości z bloku kodu między `Property` i `End Property` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="65756-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="65756-113">Blok kodu zawiera `Get` procedury `Set` procedury lub oba.</span><span class="sxs-lookup"><span data-stu-id="65756-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="65756-114">Te procedury są nazywane *procedury właściwości* lub *metod dostępu do właściwości*.</span><span class="sxs-lookup"><span data-stu-id="65756-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="65756-115">Oprócz pobierania lub przechowywania wartość właściwości, one również wykonywać akcje niestandardowe, takie jak aktualizowanie licznika dostępu.</span><span class="sxs-lookup"><span data-stu-id="65756-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="65756-116">Różnice</span><span class="sxs-lookup"><span data-stu-id="65756-116">Differences</span></span>  
 <span data-ttu-id="65756-117">W poniższej tabeli przedstawiono kilka istotnych różnic między zmiennych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="65756-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="65756-118">Punktu różnicy</span><span class="sxs-lookup"><span data-stu-id="65756-118">Point of difference</span></span>|<span data-ttu-id="65756-119">Zmienna</span><span class="sxs-lookup"><span data-stu-id="65756-119">Variable</span></span>|<span data-ttu-id="65756-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="65756-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="65756-121">Deklaracja</span><span class="sxs-lookup"><span data-stu-id="65756-121">Declaration</span></span>|<span data-ttu-id="65756-122">Pojedyncza deklaracja — instrukcja</span><span class="sxs-lookup"><span data-stu-id="65756-122">Single declaration statement</span></span>|<span data-ttu-id="65756-123">Seria instrukcje w bloku kodu</span><span class="sxs-lookup"><span data-stu-id="65756-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="65756-124">Implementacja</span><span class="sxs-lookup"><span data-stu-id="65756-124">Implementation</span></span>|<span data-ttu-id="65756-125">Pojedyncze magazynu</span><span class="sxs-lookup"><span data-stu-id="65756-125">Single storage location</span></span>|<span data-ttu-id="65756-126">Kod wykonywalny (procedury właściwości)</span><span class="sxs-lookup"><span data-stu-id="65756-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="65756-127">Magazyn</span><span class="sxs-lookup"><span data-stu-id="65756-127">Storage</span></span>|<span data-ttu-id="65756-128">Bezpośrednio związane z wartość zmiennej</span><span class="sxs-lookup"><span data-stu-id="65756-128">Directly associated with variable's value</span></span>|<span data-ttu-id="65756-129">Zwykle ma pamięci wewnętrznej nie jest dostępny poza klasę lub moduł zawierający właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="65756-130">Wartość właściwości może lub nie istnieje jako element przechowywanych <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="65756-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="65756-131">Kod wykonywalny</span><span class="sxs-lookup"><span data-stu-id="65756-131">Executable code</span></span>|<span data-ttu-id="65756-132">Brak</span><span class="sxs-lookup"><span data-stu-id="65756-132">None</span></span>|<span data-ttu-id="65756-133">Musi mieć co najmniej jednej procedury</span><span class="sxs-lookup"><span data-stu-id="65756-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="65756-134">Odczyt i zapis</span><span class="sxs-lookup"><span data-stu-id="65756-134">Read and write access</span></span>|<span data-ttu-id="65756-135">Odczyt i zapis czy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65756-135">Read/write or read-only</span></span>|<span data-ttu-id="65756-136">Odczyt/zapis, tylko do odczytu lub w trybie tylko do zapisu</span><span class="sxs-lookup"><span data-stu-id="65756-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="65756-137">Akcje niestandardowe (oprócz akceptowanie lub zwracania wartości)</span><span class="sxs-lookup"><span data-stu-id="65756-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="65756-138">Nie jest możliwe</span><span class="sxs-lookup"><span data-stu-id="65756-138">Not possible</span></span>|<span data-ttu-id="65756-139">Można wykonać w ramach ustawiania i pobierania wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="65756-140"><sup>1</sup> w przeciwieństwie do zmiennej, wartość właściwości nie może odpowiadać bezpośrednio do pojedynczego elementu magazynu.</span><span class="sxs-lookup"><span data-stu-id="65756-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="65756-141">Magazyn może zostać podzielony na fragmenty dla wygody lub zabezpieczeń, lub wartość mogą być przechowywane w postaci zaszyfrowanej.</span><span class="sxs-lookup"><span data-stu-id="65756-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="65756-142">W takich przypadkach `Get` procedury czy złożyć części lub odszyfrować przechowywana wartość i `Set` procedury czy szyfrowania nowej wartości lub podziel go na składników magazynu.</span><span class="sxs-lookup"><span data-stu-id="65756-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="65756-143">Wartości właściwości mogą być efemeryczne, takich jak porę dnia, w którym to przypadku `Get` procedury będzie obliczać go na bieżąco zawsze dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="65756-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65756-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65756-144">See Also</span></span>  
 [<span data-ttu-id="65756-145">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="65756-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="65756-146">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="65756-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="65756-147">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="65756-147">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="65756-148">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="65756-148">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="65756-149">Porady: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="65756-150">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="65756-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="65756-151">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="65756-152">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65756-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="65756-153">Porady: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="65756-154">Porady: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="65756-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
