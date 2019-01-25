---
title: 'Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5dfddb0faf77e40397eafd70955e233a9a320163
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635822"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="a6d72-102">Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a6d72-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="a6d72-103">Iterowanie po tablicy na innym sposobem jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6d72-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="a6d72-104">`foreach` Instrukcja może być używana do iteracji przez tablicę, klasy kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a6d72-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6d72-105">Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="a6d72-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6d72-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6d72-106">Example</span></span>  
 <span data-ttu-id="a6d72-107">W tym przykładzie pokazano, jak wydrukować argumentów wiersza polecenia za pomocą `foreach`.</span><span class="sxs-lookup"><span data-stu-id="a6d72-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a6d72-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6d72-108">See also</span></span>

- <xref:System.Array>
- <xref:System.Collections>
- [<span data-ttu-id="a6d72-109">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="a6d72-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="a6d72-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a6d72-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a6d72-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="a6d72-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="a6d72-112">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a6d72-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="a6d72-113">Instrukcje: Wyświetlanie argumentów wiersza poleceń</span><span class="sxs-lookup"><span data-stu-id="a6d72-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="a6d72-114">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="a6d72-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
