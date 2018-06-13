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
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647764"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="c1a34-102">Skuteczne stosowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1a34-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="c1a34-103">Niezadeklarowany zmiennych i zmiennych zadeklarowanych bez typu danych są przypisane `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="c1a34-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="c1a34-104">To ułatwia szybkie pisania programów, ale może to spowodować ich do wykonania wolniej.</span><span class="sxs-lookup"><span data-stu-id="c1a34-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="c1a34-105">Silne wpisywanie</span><span class="sxs-lookup"><span data-stu-id="c1a34-105">Strong Typing</span></span>  
 <span data-ttu-id="c1a34-106">Określenie typów danych dla wszystkich zmiennych nosi nazwę *silne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="c1a34-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="c1a34-107">Przy użyciu silne wpisywanie ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="c1a34-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="c1a34-108">Umożliwia obsługę funkcji IntelliSense dla zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c1a34-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="c1a34-109">Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich jako typu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1a34-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="c1a34-110">Trwa zaletą Sprawdzanie typu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c1a34-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="c1a34-111">To połowy instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="c1a34-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="c1a34-112">Przechwytuje również wywołania metod, w obiektach, które nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c1a34-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="c1a34-113">Wynikiem szybsze wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="c1a34-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="c1a34-114">Najbardziej efektywne typy danych</span><span class="sxs-lookup"><span data-stu-id="c1a34-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="c1a34-115">Zmienne, które nigdy nie zawierają ułamków typy całkowite danych są bardziej wydajne niż nonintegral typów.</span><span class="sxs-lookup"><span data-stu-id="c1a34-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="c1a34-116">W języku Visual Basic `Integer` i `UInteger` są najbardziej efektywny typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="c1a34-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="c1a34-117">Liczb ułamkowych `Double` jest najbardziej wydajnym typu danych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowych w podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="c1a34-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="c1a34-118">Jednak operacje przy użyciu `Double` nie są tak szybko, jak w przypadku typów całkowitych, takich jak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="c1a34-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="c1a34-119">Określanie typu danych</span><span class="sxs-lookup"><span data-stu-id="c1a34-119">Specifying Data Type</span></span>  
 <span data-ttu-id="c1a34-120">Użyj [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) Aby zadeklarować zmienną określonego typu.</span><span class="sxs-lookup"><span data-stu-id="c1a34-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="c1a34-121">Można jednocześnie określić jego poziom dostępu za pomocą [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe, jak w Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="c1a34-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="c1a34-122">Konwersja znaków</span><span class="sxs-lookup"><span data-stu-id="c1a34-122">Character Conversion</span></span>  
 <span data-ttu-id="c1a34-123">`AscW` i `ChrW` funkcje działają w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1a34-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="c1a34-124">Powinny być używane w preference do `Asc` i `Chr`, które muszą tłumaczyć do i z Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1a34-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a34-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1a34-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="c1a34-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c1a34-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="c1a34-127">Typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="c1a34-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="c1a34-128">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="c1a34-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="c1a34-129">Korzystanie z funkcji IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c1a34-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
