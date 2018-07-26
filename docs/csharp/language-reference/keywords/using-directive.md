---
title: using — Dyrektywa (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960043"
---
# <a name="using-directive-c-reference"></a>using — Dyrektywa (odwołanie w C#)
`using` Dyrektywy ma trzy zastosowań:  
  
-   Aby zezwolić na używanie typów w przestrzeni nazw, tak, aby nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Aby zezwolić na dostęp do statycznych elementów członkowskich typu bez konieczności kwalifikuj dostęp do nazwą typu. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Aby uzyskać więcej informacji, zobacz [using static, dyrektywa](using-static.md).

-   Aby utworzyć alias dla przestrzeni nazw lub typu. Jest to nazywane *użycie dyrektywy alias*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` Słowo kluczowe jest również używane do tworzenia *za pomocą instrukcji*, co pomóc, upewnij się, że <xref:System.IDisposable> obiektów, takich jak pliki i czcionki są obsługiwane poprawnie. Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.  
  
## <a name="using-static-type"></a>Za pomocą typu statycznego  
 Statyczne elementy członkowskie typu dostęp bez konieczności kwalifikuj dostęp do nazwą typu:  
  
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
 Zakres `using` dyrektywa jest ograniczona do pliku, w której występuje.  
  
 Utwórz `using` aliasu, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora. Prawego boku za pomocą aliasu dyrektywy zawsze musi być w pełni kwalifikowanego typu niezależnie od tego używając dyrektyw, które pochodzą przed nią.  
  
 Utwórz `using` dyrektywy na używanie typów w przestrzeni nazw bez konieczności określania przestrzeni nazw. A `using` dyrektywy nie umożliwiają dostęp do wszelkich przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.  
  
 Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system. Zdefiniowane przez użytkownika przestrzenie nazw są przestrzenie nazw zdefiniowane w kodzie. Aby uzyskać listę nazw zdefiniowaną przez system, zobacz [Przegląd biblioteki klas programu .NET Framework](../../../standard/class-library-overview.md).  
  
 Przykłady dotyczące odwoływania się do metody w innych zestawach, zobacz [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Przykład 1  
  
 Poniższy przykład pokazuje, jak zdefiniować i zastosować `using` alias dla przestrzeni nazw:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Using — dyrektywa alias nie może mieć to otwarty typ ogólny po prawej stronie. Na przykład nie można utworzyć za pomocą aliasu dla listy\<T >, ale można utworzyć listę\<int >.  
  
## <a name="example-2"></a>Przykład 2  
  
 Poniższy przykład pokazuje jak zdefiniować `using` dyrektywy i `using` alias dla klasy:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Używanie przestrzeni nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
 [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)
