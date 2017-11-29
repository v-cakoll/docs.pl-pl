---
title: "Porady: łączenie wielu ciągów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="cde82-102">Porady: łączenie wielu ciągów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cde82-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="cde82-103">*Łączenie* to proces dołączania jeden ciąg do końca ciągu innego.</span><span class="sxs-lookup"><span data-stu-id="cde82-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="cde82-104">Jeśli łączenie literałów ciągu lub ciągu stałych przy użyciu `+` operatora, kompilator tworzy pojedynczy ciąg.</span><span class="sxs-lookup"><span data-stu-id="cde82-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="cde82-105">Nie można uruchomić wystąpieniu łączenia.</span><span class="sxs-lookup"><span data-stu-id="cde82-105">No run time concatenation occurs.</span></span> <span data-ttu-id="cde82-106">Jednak zmiennych ciągu może zostać dołączona tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cde82-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="cde82-107">W takim przypadku zapoznaj się z różnych metod jego wpływu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="cde82-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde82-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cde82-108">Example</span></span>  
 <span data-ttu-id="cde82-109">Poniższy przykład pokazuje, jak podzielić ciąg literału na mniejsze ciągów w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="cde82-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="cde82-110">Te elementy zostaną połączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cde82-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="cde82-111">Nie jest uruchamiane koszt niezależnie od liczby ciągów związanych wydajności w czasie.</span><span class="sxs-lookup"><span data-stu-id="cde82-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="cde82-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cde82-112">Example</span></span>  
 <span data-ttu-id="cde82-113">Aby połączyć zmiennych ciągu można użyć `+` lub `+=` operatorów, lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cde82-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="cde82-114">`+` Operator jest łatwy w użyciu i sprawia, że dla intuicyjne kodu.</span><span class="sxs-lookup"><span data-stu-id="cde82-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="cde82-115">Nawet jeśli używasz kilka + operatory w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="cde82-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="cde82-116">Ale jeśli Powtórz tę operację wiele razy na przykład w pętli, może powodować problemy wydajności.</span><span class="sxs-lookup"><span data-stu-id="cde82-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="cde82-117">Na przykład należy uwzględnić następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cde82-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="cde82-118">W operacji łączenia ciąg kompilatora C# traktuje pusty ciąg takie same jak pusty ciąg, ale nie konwertuje wartość oryginalnego pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="cde82-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="cde82-119">Jeśli nie są łączenie wielu ciągów (na przykład w pętli), to koszt wydajności ten kod prawdopodobnie nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="cde82-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="cde82-120">Dotyczy to także <xref:System.String.Concat%2A?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cde82-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="cde82-121">Jednak gdy wydajności odgrywa ważną rolę, należy zawsze używać <xref:System.Text.StringBuilder> klasy do ciągów.</span><span class="sxs-lookup"><span data-stu-id="cde82-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="cde82-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do ciągów bez wpływu CBC `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="cde82-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cde82-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cde82-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="cde82-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cde82-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cde82-125">Ciągi</span><span class="sxs-lookup"><span data-stu-id="cde82-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
