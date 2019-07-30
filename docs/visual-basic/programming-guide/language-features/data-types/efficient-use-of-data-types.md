---
title: Skuteczne stosowanie typów danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631105"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="80a00-102">Skuteczne stosowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80a00-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="80a00-103">Niezadeklarowane zmienne i zmienne zadeklarowane bez typu danych są przypisywane do `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="80a00-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="80a00-104">Ułatwia to szybkie pisanie programów, ale może spowodować spowolnienie ich wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80a00-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="80a00-105">Silne wpisywanie</span><span class="sxs-lookup"><span data-stu-id="80a00-105">Strong Typing</span></span>
 <span data-ttu-id="80a00-106">Określanie typów danych dla wszystkich zmiennych jest znane jako *silne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="80a00-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="80a00-107">Używanie silnego wpisywania ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="80a00-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="80a00-108">Umożliwia obsługę technologii IntelliSense dla zmiennych.</span><span class="sxs-lookup"><span data-stu-id="80a00-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="80a00-109">Dzięki temu można zobaczyć swoje właściwości i innych członków podczas wpisywania kodu.</span><span class="sxs-lookup"><span data-stu-id="80a00-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="80a00-110">Wykorzystuje ona sprawdzanie typów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="80a00-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="80a00-111">Ta instrukcja przechwytuje instrukcje, które mogą zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienie.</span><span class="sxs-lookup"><span data-stu-id="80a00-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="80a00-112">Przechwytuje również wywołania metod na obiektach, które ich nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="80a00-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="80a00-113">Skutkuje to przyspieszeniem wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="80a00-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="80a00-114">Najbardziej wydajne typy danych</span><span class="sxs-lookup"><span data-stu-id="80a00-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="80a00-115">W przypadku zmiennych, które nigdy nie zawierają ułamków, typy danych całkowitych są bardziej wydajne niż typy niecałkowite.</span><span class="sxs-lookup"><span data-stu-id="80a00-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="80a00-116">W Visual Basic `Integer` i `UInteger` to najbardziej wydajne typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="80a00-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="80a00-117">W przypadku liczb `Double` ułamkowych jest najbardziej wydajnym typem danych, ponieważ procesory na bieżących platformach wykonują operacje zmiennoprzecinkowe w podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="80a00-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="80a00-118">Jednak operacje z `Double` nie są tak szybkie jak w przypadku typów całkowitych, takich `Integer`jak.</span><span class="sxs-lookup"><span data-stu-id="80a00-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="80a00-119">Określanie typu danych</span><span class="sxs-lookup"><span data-stu-id="80a00-119">Specifying Data Type</span></span>
 <span data-ttu-id="80a00-120">Użyj [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) , aby zadeklarować zmienną określonego typu.</span><span class="sxs-lookup"><span data-stu-id="80a00-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="80a00-121">Możesz jednocześnie określić swój poziom dostępu przy użyciu słowa kluczowego [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)lub [Private](../../../../visual-basic/language-reference/modifiers/private.md) , jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="80a00-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="80a00-122">Konwersja znaków</span><span class="sxs-lookup"><span data-stu-id="80a00-122">Character Conversion</span></span>
 <span data-ttu-id="80a00-123">Funkcje `AscW` i`ChrW` działają w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="80a00-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="80a00-124">Należy używać ich z preferencjami do `Asc` i `Chr`, które muszą przełożyć na i z wartości Unicode.</span><span class="sxs-lookup"><span data-stu-id="80a00-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="80a00-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80a00-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="80a00-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="80a00-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="80a00-127">Typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="80a00-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="80a00-128">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="80a00-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="80a00-129">Korzystanie z funkcji IntelliSense</span><span class="sxs-lookup"><span data-stu-id="80a00-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
