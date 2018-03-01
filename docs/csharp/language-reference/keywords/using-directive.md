---
title: "using — Dyrektywa (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 02c50b1e7a54d776985b60570c898e7d0739c44c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-directive-c-reference"></a>using — Dyrektywa (odwołanie w C#)
`using` Dyrektywy ma trzy zastosowań:  
  
-   Aby zezwolić na użycie typów w przestrzeni nazw, dzięki czemu nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Aby umożliwić dostęp do statycznych elementów członkowskich typu bez kwalifikacji dostępu o nazwie typu. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Aby uzyskać więcej informacji, zobacz [statycznych dyrektywa using](using-static.md).

-   Aby utworzyć alias dla przestrzeni nazw lub typu. Ta metoda jest wywoływana *alias dyrektywa using*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` — Słowo kluczowe jest również używany do tworzenia *instrukcje using*, który pomocy, upewnij się, że <xref:System.IDisposable> obiekty, takie jak pliki i czcionki są prawidłowo obsługiwane. Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.  
  
## <a name="using-static-type"></a>Przy użyciu typu statycznego  
 Statyczne elementy członkowskie typu dostępne bez konieczności zakwalifikować dostępu o nazwie:  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Zakres `using` dyrektywa jest ograniczona do pliku, w których występuje.  
  
 Utwórz `using` alias, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora. Prawej stronie, używając aliasu dyrektywy zawsze musi być typem pełną niezależnie od tego, użycie dyrektywy znajdujące się przed nim.  
  
 Utwórz `using` dyrektywy można używać typów w przestrzeni nazw, bez konieczności określania przestrzeni nazw. A `using` dyrektywy nie udostępnia wszystkie przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.  
  
 Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system. Zdefiniowane przez użytkownika przestrzenie nazw są nazw zdefiniowanych w kodzie. Aby uzyskać listę obszarów nazw zdefiniowanych w systemie, zobacz [Przegląd biblioteki klas programu .NET Framework](../../../standard/class-library-overview.md).  
  
 Przykłady dotyczące odwoływania się do metody w innych zestawów można znaleźć [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Przykład 1  
  
 Poniższy przykład przedstawia sposób zdefiniować i użyć `using` alias przestrzeni nazw:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Za pomocą dyrektywy alias nie może być otwartym typem ogólnym po prawej stronie. Na przykład nie można utworzyć za pomocą aliasu dla listy\<T >, ale można utworzyć listę\<int >.  
  
## <a name="example-2"></a>Przykład 2  
  
 Poniższy przykład przedstawia sposób definiowania `using` dyrektywy i `using` alias klasy:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Używanie usługi przestrzenie nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
 [Using — instrukcja](../../../csharp/language-reference/keywords/using-statement.md)
