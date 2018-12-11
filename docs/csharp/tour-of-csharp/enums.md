---
title: C#Typy wyliczeniowe — Przewodnik po przykładzie C# języka
description: Dowiedz się więcej na temat typów wyliczeń, odrębny o nazwie stałych wC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: d55462f0360b6896c398d581918a9c17a87583be
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126657"
---
# <a name="enums"></a><span data-ttu-id="ff105-103">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ff105-103">Enums</span></span>

<span data-ttu-id="ff105-104">***Typu wyliczeniowego*** jest typem wartości odrębnych z szeregu nazwanych stałych.</span><span class="sxs-lookup"><span data-stu-id="ff105-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="ff105-105">Należy zdefiniować typy wyliczeniowe, gdy trzeba zdefiniować typ, który może mieć zestaw wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="ff105-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="ff105-106">Używają jednego z typów całkowitych wartości jako swojego podstawowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="ff105-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="ff105-107">Zapewniają one znaczenia semantycznego dyskretnych wartości.</span><span class="sxs-lookup"><span data-stu-id="ff105-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="ff105-108">Poniższy przykład deklaruje i wykorzystuje `enum` typu o nazwie `Color` z trzech wartości stałych, `Red`, `Green`, i `Blue`.</span><span class="sxs-lookup"><span data-stu-id="ff105-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="ff105-109">Każdy `enum` typ ma odpowiedni typ całkowity, o nazwie ***typ bazowy*** z `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="ff105-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="ff105-110">`enum` Typ, który jawnie deklaruj typu podstawowego jest podstawowym typem `int`.</span><span class="sxs-lookup"><span data-stu-id="ff105-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="ff105-111">`enum` Typu formatu przechowywania i zakres możliwych wartości są określane przez jej typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="ff105-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="ff105-112">Zbiór wartości, które `enum` typu można wykonać na nie jest ograniczone przez jego `enum` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ff105-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="ff105-113">W szczególności wszelkich wartości elementu bazowego typu `enum` mogą być rzutowane na `enum` typu i jest prawidłową wartością distinct tego `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="ff105-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="ff105-114">Poniższy przykład deklaruje `enum` typu o nazwie `Alignment` z podstawowym typem `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="ff105-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="ff105-115">Jak pokazano w poprzednim przykładzie `enum` deklaracji składowej może zawierać wyrażenie stałe, które określa wartość elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ff105-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="ff105-116">Stała wartość dla każdego `enum` elementu członkowskiego musi należeć do zakresu podstawowym typem `enum`.</span><span class="sxs-lookup"><span data-stu-id="ff105-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="ff105-117">Podczas `enum` deklaracji składowej bez określenia wartości, element członkowski jest podana wartość zero (jeśli jest pierwszym elementem w `enum` typu) lub wartość poprzedniego formie tekstu `enum` elementu członkowskiego, plus jeden.</span><span class="sxs-lookup"><span data-stu-id="ff105-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="ff105-118">`Enum` wartości mogą być przekonwertowane do całkowitej wartości i odwrotnie przy użyciu typu rzutowania.</span><span class="sxs-lookup"><span data-stu-id="ff105-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="ff105-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ff105-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="ff105-120">Wartość domyślna dowolnej `enum` typ jest wartością typu całkowitego konwertowane na wartość zero `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="ff105-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="ff105-121">W przypadkach, gdy zmienne są automatycznie inicjowane na wartość domyślną, jest to wartość do zmiennych `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="ff105-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="ff105-122">Aby wartość domyślną `enum` typ były łatwo dostępne, literał `0` niejawnie konwertuje do dowolnego `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="ff105-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="ff105-123">W związku z tym że jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="ff105-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
><span data-ttu-id="ff105-124">[Poprzednie](interfaces.md)
>[dalej](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="ff105-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>