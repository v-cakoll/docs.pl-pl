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
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach (C# Programming Guide)
Iterowanie po tablicy na innym sposobem jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie. `foreach` Instrukcja może być używana do iteracji przez tablicę, klasy kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.  
  
> [!NOTE]
>  Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak wydrukować argumentów wiersza polecenia za pomocą `foreach`.  
  
 [!code-csharp[csProgGuideMain#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class2.cs#10)]  
  
 [!code-csharp[csProgGuideMain#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- <xref:System.Collections>
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Instrukcje: Wyświetlanie argumentów wiersza poleceń](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
