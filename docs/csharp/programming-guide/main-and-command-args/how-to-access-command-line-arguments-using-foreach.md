---
title: "Porady: uzyskiwanie dostępu do argumentów wiersza poleceń za pomocą instrukcji foreach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="ac628-102">Porady: uzyskiwanie dostępu do argumentów wiersza poleceń za pomocą instrukcji foreach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ac628-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="ac628-103">Innym sposobem Iterowanie po tablicy jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac628-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="ac628-104">`foreach` Instrukcja może być używana do wykonywania iteracji tablica, Klasa kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ac628-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac628-105">Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="ac628-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac628-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac628-106">Example</span></span>  
 <span data-ttu-id="ac628-107">W tym przykładzie pokazano, jak wydrukować argumenty wiersza polecenia przy użyciu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="ac628-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ac628-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac628-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="ac628-109">Za pomocą wiersza polecenia z csc.exe</span><span class="sxs-lookup"><span data-stu-id="ac628-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="ac628-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ac628-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ac628-111">Instrukcja foreach w</span><span class="sxs-lookup"><span data-stu-id="ac628-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="ac628-112">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ac628-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="ac628-113">Porady: wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ac628-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="ac628-114">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="ac628-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
