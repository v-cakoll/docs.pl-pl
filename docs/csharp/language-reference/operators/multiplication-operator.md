---
title: '* Operator - C# odwołania'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333736"
---
# <a name="-operator-c-reference"></a>* — operator (C# odwołania)

Operator mnożenia (`*`) oblicza iloczyn argumentów. Wszystkie typy liczbowe zostały wstępnie zdefiniowane operatorów mnożenia.

`*` Służy również jako operator wyłuskania, która umożliwia odczytywanie i zapisywanie do wskaźnika.

## <a name="remarks"></a>Uwagi

`*` Operator służy także do deklarowania typów wskaźnika i celu wyłuskania wskaźników. Ten operator należy używać tylko w kontekstach niebezpieczne wskazywane przez użycie [niebezpieczne](../keywords/unsafe.md) — słowo kluczowe która wymaga [/ unsafe](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.  Operator wyłuskania jest również nazywany operatora pośredniego.

Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `*` — operator (zobacz [operator](../keywords/operator.md)). Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.

## <a name="example"></a>Przykład

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
- [Operatory języka C#](index.md)