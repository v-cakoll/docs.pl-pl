---
title: 'Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5813ad573e89886ba991ca8cbcebb7232af05821
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971679"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="1b625-102">Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1b625-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="1b625-103">Iterowanie po tablicy na innym sposobem jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1b625-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="1b625-104">`foreach` Instrukcja może być używana do iteracji przez tablicę, klasy kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1b625-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b625-105">Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="1b625-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b625-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b625-106">Example</span></span>  
 <span data-ttu-id="1b625-107">W tym przykładzie pokazano, jak wydrukować argumentów wiersza polecenia za pomocą `foreach`.</span><span class="sxs-lookup"><span data-stu-id="1b625-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class2.cs#10)]  
  
 [!code-csharp[csProgGuideMain#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1b625-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b625-108">See also</span></span>

- <xref:System.Array>
- <xref:System.Collections>
- [<span data-ttu-id="1b625-109">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="1b625-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="1b625-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b625-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1b625-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="1b625-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="1b625-112">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1b625-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="1b625-113">Instrukcje: Wyświetlanie argumentów wiersza poleceń</span><span class="sxs-lookup"><span data-stu-id="1b625-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="1b625-114">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="1b625-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
