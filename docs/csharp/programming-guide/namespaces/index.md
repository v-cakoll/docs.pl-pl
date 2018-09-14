---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c4011092a6c605137053b544d4b9f14cce2fdb4c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560285"
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)

Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby. Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw. `using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../language-reference/keywords/using-directive.md).  
  
Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania. Użyj [przestrzeni nazw](../../language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

Nazwa przestrzeni nazw musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Przegląd przestrzeni nazw  

Przestrzenie nazw mają następujące właściwości:  
  
- Ich organizowanie kodu dużych projektów.  
- Są rozdzielane przy użyciu `.` operatora.  
- `using directive` Eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.  
- `global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do przestrzeni nazw .NET Framework `System`.  

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Używanie przestrzeni nazw](using-namespaces.md)
- [Instrukcje: użycie globalnych aliasów przestrzeni nazw](how-to-use-the-global-namespace-alias.md)
- [Instrukcje: użycie przestrzeni nazw typu My](how-to-use-the-my-namespace.md)
- [Przewodnik programowania w języku C#](../index.md)  
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Słowa kluczowe przestrzeni nazw](../../language-reference/keywords/namespace-keywords.md)  
- [using, dyrektywa](../../language-reference/keywords/using-directive.md)  
- [::, operator](../../language-reference/operators/namespace-alias-qualifer.md)  
- [. operator](../../language-reference/operators/member-access-operator.md)
>>>>>>> Dodaj identyfikator reguły nazewnictwa
