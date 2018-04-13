---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw silnie są używane w na dwa sposoby programowania w języku C#. Najpierw .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System`jest przestrzenią nazw i `Console` jest klasą w tej przestrzeni nazw. `using` Można można użyć słowa kluczowego, dzięki czemu Pełna nazwa nie jest wymagane, jak w poniższym przykładzie:  
  
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
  
-   [Używanie usługi przestrzenie nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Porady: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Porady: Użyj mojej Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Using — Dyrektywa](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: — Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. Operator](../../../csharp/language-reference/operators/member-access-operator.md)
