---
title: klauzula let - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173591"
---
# <a name="let-clause-c-reference"></a>Klauzula Let (odwołanie w C#)

W wyrażeniu kwerendy czasami jest przydatne do przechowywania wyniku wyrażenia podrzędnego w celu użycia go w kolejnych klauzul. Można to zrobić `let` za pomocą słowa kluczowego, który tworzy nową zmienną zakresu i inicjuje go z wynikiem wyrażenia, które podajesz. Po zainicjowania z wartością zmiennej zakresu nie można użyć do przechowywania innej wartości. Jednak jeśli zmienna zakresu zawiera typ zapytań, można go zbadać.

## <a name="example"></a>Przykład

W poniższym `let` przykładzie jest używany na dwa sposoby:

1. Aby utworzyć typ wyliczany, który sam może być przeszukiwany.

2. Aby włączyć kwerendę `ToLower` do wywołania tylko `word`jeden raz na zmiennej zakresu . Bez `let`użycia , trzeba `ToLower` by wywołać w każdym `where` predykatu w klauzuli.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [LINQ w C#](../../linq/index.md)
- [Language Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Obsługa wyjątków w wyrażeniach zapytań](../../linq/handle-exceptions-in-query-expressions.md)
