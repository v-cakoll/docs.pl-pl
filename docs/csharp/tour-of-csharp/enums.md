---
title: "C# wyliczenia — samouczek języka C#"
description: "Dowiedz się więcej o wyliczenia, odrębny o nazwie stałe języka C#"
keywords: ".NET, języka csharp"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="enums"></a><span data-ttu-id="e3dac-104">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e3dac-104">Enums</span></span>

<span data-ttu-id="e3dac-105">***Typu wyliczeniowego*** jest typem unikatowych wartości przy użyciu zestawu stałe nazwane.</span><span class="sxs-lookup"><span data-stu-id="e3dac-105">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="e3dac-106">Typy wyliczeniowe należy zdefiniować, kiedy należy zdefiniować typu, który może mieć zestaw wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="e3dac-106">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="e3dac-107">Używają jednego z typów całkowitych wartości jako ich powiązany magazyn.</span><span class="sxs-lookup"><span data-stu-id="e3dac-107">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="e3dac-108">Udostępniają one semantycznego znaczenie wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="e3dac-108">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="e3dac-109">W poniższym przykładzie deklaruje i używa `enum` typu o nazwie `Color` z trzech wartości stałej, `Red`, `Green`, i `Blue`.</span><span class="sxs-lookup"><span data-stu-id="e3dac-109">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="e3dac-110">Każdy `enum` typ ma odpowiedni typ całkowity o nazwie ***typ podstawowy*** z `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="e3dac-110">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="e3dac-111">`enum` Typu, który nie deklaruje jawnie typ podstawowy ma typ podstawowy elementu `int`.</span><span class="sxs-lookup"><span data-stu-id="e3dac-111">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="e3dac-112">`enum` Typu formatu przechowywania i zakresu możliwych wartości są określane przez jego typem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="e3dac-112">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="e3dac-113">Zbiór wartości, które `enum` typu może zająć na nie jest ograniczona przez jego `enum` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e3dac-113">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="e3dac-114">W szczególności typ wartości podstawowych `enum` mogą być rzutowane na `enum` typu i jest prawidłową wartością różne tego `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="e3dac-114">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="e3dac-115">Poniższy przykład deklaruje `enum` typu o nazwie `Alignment` z typem podstawowym typu `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="e3dac-115">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="e3dac-116">Jak pokazano w poprzednim przykładzie `enum` deklaracji elementu członkowskiego mogą zawierać wyrażenie stałe, która określa wartość elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e3dac-116">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="e3dac-117">Wartość stała dla każdego `enum` element członkowski musi być w zakresie typ podstawowy elementu `enum`.</span><span class="sxs-lookup"><span data-stu-id="e3dac-117">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="e3dac-118">Podczas `enum` deklaracji elementu członkowskiego nie jawnie określona wartość, element członkowski znajduje się wartość zero (jeśli pierwszego elementu członkowskiego w `enum` typu) lub wartość postaci tekstu poprzedniego `enum` elementu członkowskiego plus jeden.</span><span class="sxs-lookup"><span data-stu-id="e3dac-118">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="e3dac-119">`Enum`wartości mogą być przekonwertowane na całkowite wartości i na odwrót przy użyciu typu rzutowania.</span><span class="sxs-lookup"><span data-stu-id="e3dac-119">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="e3dac-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e3dac-120">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="e3dac-121">Wartość domyślna dowolnej `enum` typ jest integralną wartość zero przekonwertować `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="e3dac-121">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="e3dac-122">W przypadkach, gdy zmienne są inicjowane automatycznie wartość domyślna to wartość zmiennych `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="e3dac-122">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="e3dac-123">Aby wartość domyślną `enum` typu były łatwo dostępne, literał `0` niejawnie konwertuje wszelkie `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="e3dac-123">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="e3dac-124">W związku z tym następujące jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e3dac-124">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="e3dac-125">[Poprzednie](interfaces.md)
[dalej](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="e3dac-125">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
