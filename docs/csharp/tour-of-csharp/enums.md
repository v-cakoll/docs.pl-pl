---
title: C# wyliczenia — samouczek języka C#
description: Dowiedz się więcej o wyliczenia, odrębny o nazwie stałe języka C#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 7fe2626381cb90e55842e3be17dd450eb73d5a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enums"></a><span data-ttu-id="5b430-103">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b430-103">Enums</span></span>

<span data-ttu-id="5b430-104">***Typu wyliczeniowego*** jest typem unikatowych wartości przy użyciu zestawu stałe nazwane.</span><span class="sxs-lookup"><span data-stu-id="5b430-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="5b430-105">Typy wyliczeniowe należy zdefiniować, kiedy należy zdefiniować typu, który może mieć zestaw wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="5b430-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="5b430-106">Używają jednego z typów całkowitych wartości jako ich powiązany magazyn.</span><span class="sxs-lookup"><span data-stu-id="5b430-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="5b430-107">Udostępniają one semantycznego znaczenie wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="5b430-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="5b430-108">W poniższym przykładzie deklaruje i używa `enum` typu o nazwie `Color` z trzech wartości stałej, `Red`, `Green`, i `Blue`.</span><span class="sxs-lookup"><span data-stu-id="5b430-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="5b430-109">Każdy `enum` typ ma odpowiedni typ całkowity o nazwie ***typ podstawowy*** z `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="5b430-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="5b430-110">`enum` Typu, który nie deklaruje jawnie typ podstawowy ma typ podstawowy elementu `int`.</span><span class="sxs-lookup"><span data-stu-id="5b430-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="5b430-111">`enum` Typu formatu przechowywania i zakresu możliwych wartości są określane przez jego typem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="5b430-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="5b430-112">Zbiór wartości, które `enum` typu może zająć na nie jest ograniczona przez jego `enum` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5b430-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="5b430-113">W szczególności typ wartości podstawowych `enum` mogą być rzutowane na `enum` typu i jest prawidłową wartością różne tego `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="5b430-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="5b430-114">Poniższy przykład deklaruje `enum` typu o nazwie `Alignment` z typem podstawowym typu `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="5b430-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="5b430-115">Jak pokazano w poprzednim przykładzie `enum` deklaracji elementu członkowskiego mogą zawierać wyrażenie stałe, która określa wartość elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5b430-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="5b430-116">Wartość stała dla każdego `enum` element członkowski musi być w zakresie typ podstawowy elementu `enum`.</span><span class="sxs-lookup"><span data-stu-id="5b430-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="5b430-117">Podczas `enum` deklaracji elementu członkowskiego nie jawnie określona wartość, element członkowski znajduje się wartość zero (jeśli pierwszego elementu członkowskiego w `enum` typu) lub wartość postaci tekstu poprzedniego `enum` elementu członkowskiego plus jeden.</span><span class="sxs-lookup"><span data-stu-id="5b430-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="5b430-118">`Enum` wartości mogą być przekonwertowane na całkowite wartości i na odwrót przy użyciu typu rzutowania.</span><span class="sxs-lookup"><span data-stu-id="5b430-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="5b430-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5b430-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="5b430-120">Wartość domyślna dowolnej `enum` typ jest integralną wartość zero przekonwertować `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="5b430-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="5b430-121">W przypadkach, gdy zmienne są inicjowane automatycznie wartość domyślna to wartość zmiennych `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="5b430-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="5b430-122">Aby wartość domyślną `enum` typu były łatwo dostępne, literał `0` niejawnie konwertuje wszelkie `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="5b430-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="5b430-123">W związku z tym następujące jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="5b430-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="5b430-124">[Poprzednie](interfaces.md)
[dalej](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="5b430-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
