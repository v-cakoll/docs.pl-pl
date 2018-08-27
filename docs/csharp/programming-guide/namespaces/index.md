---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934876"
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby. Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw. `using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../../csharp/language-reference/keywords/using-directive.md).  
  
 Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania. Użyj [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Przegląd przestrzeni nazw  
 Przestrzenie nazw mają następujące właściwości:  
  
-   Ich organizowanie kodu dużych projektów.  
  
-   Są rozdzielane przy użyciu `.` operatora.  
  
-   `using directive` Eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.  
  
-   `global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do przestrzeni nazw .NET Framework `System`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Zobacz następujące tematy, aby uzyskać więcej informacji na temat przestrzenie nazw:  
  
-   [Używanie przestrzeni nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Instrukcje: użycie globalnych aliasów przestrzeni nazw](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Instrukcje: użycie przestrzeni nazw typu My](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using, dyrektywa](../../../csharp/language-reference/keywords/using-directive.md)  
 [::, operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. operator](../../../csharp/language-reference/operators/member-access-operator.md)
