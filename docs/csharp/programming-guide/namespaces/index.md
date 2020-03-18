---
title: Przestrzenie nazw — przewodnik programowania C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937616"
---
# <a name="namespaces-c-programming-guide"></a>Przestrzenie nazw (Przewodnik programowania w języku C#)

Przestrzenie nazw są intensywnie używane w programowaniu języka C# na dwa sposoby. Po pierwsze. .NET używa przestrzeni nazw do organizowania wielu klas w następujący sposób:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>jest obszarem <xref:System.Console> nazw i jest klasą w tym obszarze nazw. Słowa `using` kluczowego można użyć, aby pełna nazwa nie była wymagana, jak w poniższym przykładzie:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Aby uzyskać więcej informacji, zobacz [dyrektywę stosującą](../../language-reference/keywords/using-directive.md).

Po drugie deklarowanie własnych przestrzeni nazw może pomóc kontrolować zakres nazw klas i metod w większych projektach programowania. Użyj słowa kluczowego [obszaru nazw,](../../language-reference/keywords/namespace.md) aby zadeklarować obszar nazw, jak w poniższym przykładzie:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Nazwa obszaru nazw musi być prawidłową [nazwą identyfikatora C#.](../inside-a-program/identifier-names.md)

## <a name="namespaces-overview"></a>Omówienie przestrzeni nazw

Przestrzenie nazw mają następujące właściwości:

- Organizują duże projekty kodu.
- Są one rozdzielane `.` za pomocą operatora.
- Dyrektywa `using` zażegna wymóg, aby określić nazwę obszaru nazw dla każdej klasy.
- Obszar `global` nazw jest "root" obszar `global::System` nazw: zawsze odnoszą <xref:System> się do obszaru nazw .NET.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Przestrzenie nazw](~/_csharplang/spec/namespaces.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Używanie przestrzeni nazw](using-namespaces.md)
- [Korzystanie z przestrzeni nazw typu My](how-to-use-the-my-namespace.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [using, dyrektywa](../../language-reference/keywords/using-directive.md)
- [:: Operator](../../language-reference/operators/namespace-alias-qualifier.md)
