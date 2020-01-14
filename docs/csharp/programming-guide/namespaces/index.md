---
title: Przestrzenie C# nazw — Przewodnik programowania
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937616"
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)

Przestrzenie nazw są intensywnie używane w C# programowaniu na dwa sposoby. Najpierw platforma .NET używa przestrzeni nazw do organizowania jej wielu klas w następujący sposób:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System> jest przestrzenią nazw, a <xref:System.Console> jest klasą w tej przestrzeni nazw. Za pomocą słowa kluczowego `using` można użyć, aby pełna nazwa nie była wymagana, jak w poniższym przykładzie:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../language-reference/keywords/using-directive.md).

Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych. Użyj słowa kluczowego [Namespace](../../language-reference/keywords/namespace.md) , aby zadeklarować przestrzeń nazw, jak w poniższym przykładzie:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Nazwa przestrzeni nazw musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Przegląd przestrzeni nazw

Przestrzenie nazw mają następujące właściwości:

- Organizują one duże projekty kodu.
- Są one rozdzielane za pomocą operatora `.`.
- Dyrektywa `using` eliminuje konieczność określenia nazwy przestrzeni nazw dla każdej klasy.
- Przestrzeń nazw `global` jest przestrzenią nazw "root": `global::System` zawsze będzie odwoływać się do przestrzeni nazw .NET <xref:System>.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [przestrzenie nazw](~/_csharplang/spec/namespaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Używanie przestrzeni nazw](using-namespaces.md)
- [Jak używać przestrzeni nazw](how-to-use-the-my-namespace.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [using, dyrektywa](../../language-reference/keywords/using-directive.md)
- [::, operator](../../language-reference/operators/namespace-alias-qualifier.md)
