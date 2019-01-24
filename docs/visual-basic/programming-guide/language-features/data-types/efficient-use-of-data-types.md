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
ms.openlocfilehash: e0cb67b4b26bf59b074bf5964f253c007fdbe719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736172"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="bd948-102">Skuteczne stosowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd948-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="bd948-103">Niezadeklarowany zmienne i zmienne zadeklarowane bez typu danych są przypisywane `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="bd948-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="bd948-104">To ułatwia szybkie pisanie programów, ale może to spowodować ich pracę wolniej.</span><span class="sxs-lookup"><span data-stu-id="bd948-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="bd948-105">Silne wpisywanie</span><span class="sxs-lookup"><span data-stu-id="bd948-105">Strong Typing</span></span>  
 <span data-ttu-id="bd948-106">Określenie typów danych dla wszystkich zmiennych jest znany jako *silne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="bd948-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="bd948-107">Za pomocą silne wpisywanie ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="bd948-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="bd948-108">Umożliwia obsługę funkcji IntelliSense dla zmiennych.</span><span class="sxs-lookup"><span data-stu-id="bd948-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="bd948-109">Dzięki temu można zobaczyć ich właściwości i inne elementy członkowskie podczas wpisywania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bd948-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="bd948-110">Wykorzystuje ona sprawdzania typu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="bd948-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="bd948-111">To połowy instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="bd948-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="bd948-112">Przechwytuje także wywołania metod, na obiektach, które nie obsługują je.</span><span class="sxs-lookup"><span data-stu-id="bd948-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="bd948-113">Powoduje ona szybsze wykonywanie Twojego kodu.</span><span class="sxs-lookup"><span data-stu-id="bd948-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="bd948-114">Najbardziej wydajne typy danych</span><span class="sxs-lookup"><span data-stu-id="bd948-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="bd948-115">W przypadku zmiennych, które nigdy nie zawierają ułamki typy całkowite danych są bardziej wydajne niż nonintegral typów.</span><span class="sxs-lookup"><span data-stu-id="bd948-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="bd948-116">W języku Visual Basic `Integer` i `UInteger` są najbardziej efektywny sposób typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="bd948-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="bd948-117">W przypadku liczb ułamkowych `Double` jest najbardziej efektywny sposób typ danych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowej w podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="bd948-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="bd948-118">Jednak operacje `Double` nie są tak szybko, podobnie jak w przypadku typów całkowitych, takie jak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="bd948-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="bd948-119">Określanie typu danych</span><span class="sxs-lookup"><span data-stu-id="bd948-119">Specifying Data Type</span></span>  
 <span data-ttu-id="bd948-120">Użyj [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) Aby zadeklarować zmienną określonego typu.</span><span class="sxs-lookup"><span data-stu-id="bd948-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="bd948-121">Można jednocześnie określić jego poziom dostępu za pomocą [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe, jak Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="bd948-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="bd948-122">Konwersja znaków</span><span class="sxs-lookup"><span data-stu-id="bd948-122">Character Conversion</span></span>  
 <span data-ttu-id="bd948-123">`AscW` i `ChrW` funkcje działają w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd948-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="bd948-124">Powinny być używane w preference do `Asc` i `Chr`, który musi przetłumaczyć do i z Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd948-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd948-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd948-125">See also</span></span>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="bd948-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="bd948-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="bd948-127">Typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="bd948-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="bd948-128">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="bd948-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="bd948-129">Korzystanie z funkcji IntelliSense</span><span class="sxs-lookup"><span data-stu-id="bd948-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
