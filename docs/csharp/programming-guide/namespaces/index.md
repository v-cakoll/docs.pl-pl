---
title: Przestrzenie nazw — C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 3e05e18225b198e9e34b4b96717cc813dab836c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710111"
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)

Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby. Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw. `using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../language-reference/keywords/using-directive.md).  
  
Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania. Użyj [przestrzeni nazw](../../language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Nazwa przestrzeni nazw musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Przegląd przestrzeni nazw  

Przestrzenie nazw mają następujące właściwości:  
  
- Ich organizowanie kodu dużych projektów.  
- Są rozdzielane przy użyciu `.` operatora.  
- `using` Dyrektywy eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.  
- `global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do platformy .NET <xref:System> przestrzeni nazw.  

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie przestrzeni nazw](using-namespaces.md)
- [Instrukcje: Użycie globalnych aliasów Namespace](how-to-use-the-global-namespace-alias.md)
- [Instrukcje: Użyj mojej Namespace](how-to-use-the-my-namespace.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Słowa kluczowe przestrzeni nazw](../../language-reference/keywords/namespace-keywords.md)
- [using, dyrektywa](../../language-reference/keywords/using-directive.md)
- [:: operator](../../language-reference/operators/namespace-alias-qualifer.md)
- [. operator](../../language-reference/operators/member-access-operator.md)
