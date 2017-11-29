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
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Porady: uzyskiwanie dostępu do argumentów wiersza poleceń za pomocą instrukcji foreach (Przewodnik programowania w języku C#)
Innym sposobem Iterowanie po tablicy jest użycie [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji, jak pokazano w poniższym przykładzie. `foreach` Instrukcja może być używana do wykonywania iteracji tablica, Klasa kolekcji .NET Framework lub dowolnej klasy lub struktury, która implementuje <xref:System.Collections.IEnumerable> interfejsu.  
  
> [!NOTE]
>  Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak wydrukować argumenty wiersza polecenia przy użyciu `foreach`.  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 <xref:System.Collections>  
 [Za pomocą wiersza polecenia z csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Instrukcja foreach w](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Porady: wyświetlanie argumentów wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
