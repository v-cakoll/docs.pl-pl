---
title: 'Porady: uzyskiwanie dostępu do argumentów wiersza poleceń za pomocą instrukcji foreach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 2f1723efd4056539e12605bc1a4229f94bc9e055
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332510"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="5e974-102">Porady: uzyskiwanie dostępu do argumentów wiersza poleceń za pomocą instrukcji foreach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5e974-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="5e974-103">Innym sposobem Iterowanie po tablicy jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5e974-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="5e974-104">`foreach` Instrukcja może być używana do wykonywania iteracji tablica, Klasa kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5e974-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e974-105">Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="5e974-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e974-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e974-106">Example</span></span>  
 <span data-ttu-id="5e974-107">W tym przykładzie pokazano, jak wydrukować argumenty wiersza polecenia przy użyciu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5e974-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5e974-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e974-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="5e974-109">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="5e974-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="5e974-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5e974-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e974-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="5e974-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="5e974-112">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5e974-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="5e974-113">Instrukcje: wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5e974-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="5e974-114">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="5e974-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
