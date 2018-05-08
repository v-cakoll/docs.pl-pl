---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw silnie są używane w na dwa sposoby programowania w języku C#. Najpierw .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` jest przestrzenią nazw i `Console` jest klasą w tej przestrzeni nazw. `using` Można można użyć słowa kluczowego, dzięki czemu Pełna nazwa nie jest wymagane, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../../csharp/language-reference/keywords/using-directive.md).  
  
 Po drugie deklarowanie własnych przestrzeni nazw ułatwia kontrolowanie zakresu nazw klasy i metody w większych projektów programowania. Użyj [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) słowo kluczowe, aby zadeklarować przestrzeni nazw, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Omówienie przestrzenie nazw  
 Przestrzenie nazw ma następujące właściwości:  
  
-   Ich organizowanie kodu dużych projektów.  
  
-   Są rozdzielane przy użyciu `.` operatora.  
  
-   `using directive` Eliminuje konieczność Określ nazwę obszaru nazw dla każdej klasy.  
  
-   `global` Przestrzeni nazw jest przestrzenią nazw "root": `global::System` zawsze odwołuje się do przestrzeni nazw .NET Framework `System`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Zobacz następujące tematy, aby uzyskać więcej informacji o przestrzeni nazw:  
  
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
