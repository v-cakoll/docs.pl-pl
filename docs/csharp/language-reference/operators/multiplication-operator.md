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
ms.openlocfilehash: 24ac4a99c48f1e8204b821bfbf5f7fbc0a2b2f1d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237353"
---
# <a name="-operator-c-reference"></a>* — Operator (odwołanie w C#)
Operator mnożenia (`*`) oblicza iloczyn argumentów. Wszystkie typy liczbowe zostały wstępnie zdefiniowane operatorów mnożenia.  

`*` Służy również jako operator wyłuskania, która umożliwia odczytywanie i zapisywanie do wskaźnika.
  
## <a name="remarks"></a>Uwagi  
 `*` Operator służy także do deklarowania typów wskaźnika i celu wyłuskania wskaźników. Ten operator należy używać tylko w kontekstach niebezpieczne wskazywane przez użycie [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe która wymaga [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.  Operator wyłuskania jest również nazywany operatora pośredniego.  
  
 Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `*` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
