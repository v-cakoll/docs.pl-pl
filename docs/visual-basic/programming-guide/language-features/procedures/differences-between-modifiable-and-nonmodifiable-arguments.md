---
title: Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 733f92cc2cdaa6e923c57649774ceb64de172c18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403346"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="b6fb4-102">Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6fb4-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="b6fb4-103">Po wywołaniu procedury zwykle przekazywany jest jeden lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="b6fb4-104">Każdy argument odpowiada bazowemu elementowi programistycznemu.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="b6fb4-105">Zarówno elementy bazowe, jak i same argumenty mogą być modyfikowalne lub niemodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="b6fb4-106">Modyfikowalne i niemodyfikowalne elementy</span><span class="sxs-lookup"><span data-stu-id="b6fb4-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="b6fb4-107">Elementem programistycznym może być *element modyfikowalny*, który może mieć zmienioną wartość, lub *niemodyfikowalny element*, który ma ustaloną wartość po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="b6fb4-108">W poniższej tabeli wymieniono elementy programistyczne modyfikowane i niemodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="b6fb4-109">Modyfikowalne elementy</span><span class="sxs-lookup"><span data-stu-id="b6fb4-109">Modifiable elements</span></span>|<span data-ttu-id="b6fb4-110">Elementy niemodyfikowalne</span><span class="sxs-lookup"><span data-stu-id="b6fb4-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="b6fb4-111">Zmienne lokalne (zadeklarowane wewnątrz procedur), w tym zmienne obiektów, z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6fb4-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="b6fb4-112">Zmienne tylko do odczytu, pola i właściwości</span><span class="sxs-lookup"><span data-stu-id="b6fb4-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="b6fb4-113">Pola (zmienne składowe modułów, klas i struktur), z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6fb4-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="b6fb4-114">Stałe i literały</span><span class="sxs-lookup"><span data-stu-id="b6fb4-114">Constants and literals</span></span>|  
|<span data-ttu-id="b6fb4-115">Właściwości, z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6fb4-115">Properties, except for read-only</span></span>|<span data-ttu-id="b6fb4-116">Elementy członkowskie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b6fb4-116">Enumeration members</span></span>|  
|<span data-ttu-id="b6fb4-117">Elementy tablicy</span><span class="sxs-lookup"><span data-stu-id="b6fb4-117">Array elements</span></span>|<span data-ttu-id="b6fb4-118">Wyrażenia (nawet jeśli ich elementy są modyfikowane)</span><span class="sxs-lookup"><span data-stu-id="b6fb4-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="b6fb4-119">Modyfikowalne i niemodyfikowalne argumenty</span><span class="sxs-lookup"><span data-stu-id="b6fb4-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="b6fb4-120">*Modyfikowalny argument* to jeden z modyfikowalnym elementem bazowym.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="b6fb4-121">Kod wywołujący może przechowywać nową wartość w dowolnym momencie, a w przypadku przekazania argumentu [ByRef](../../../language-reference/modifiers/byref.md)kod w procedurze może także zmodyfikować podstawowy element w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="b6fb4-122">*Argument niemodyfikowalny* ma niemodyfikowalny element podstawowy lub został przekazaną wartość [ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="b6fb4-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="b6fb4-123">Procedura nie może zmodyfikować podstawowego elementu w kodzie wywołującym, nawet jeśli jest to element modyfikowalny.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="b6fb4-124">Jeśli jest to niemodyfikowalny element, sam kod wywołujący nie może go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="b6fb4-125">Wywołana procedura może zmodyfikować swoją lokalną kopię niemodyfikowalnego argumentu, ale ta modyfikacja nie ma wpływu na element podstawowy w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="b6fb4-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6fb4-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6fb4-126">See also</span></span>

- [<span data-ttu-id="b6fb4-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="b6fb4-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b6fb4-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="b6fb4-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b6fb4-129">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="b6fb4-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="b6fb4-130">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="b6fb4-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b6fb4-131">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="b6fb4-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="b6fb4-132">Instrukcje: zmiana wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="b6fb4-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="b6fb4-133">Instrukcje: ochrona argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="b6fb4-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="b6fb4-134">Instrukcje: wymuszanie przekazywania argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="b6fb4-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="b6fb4-135">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="b6fb4-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="b6fb4-136">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="b6fb4-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
