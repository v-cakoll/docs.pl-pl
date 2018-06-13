---
title: '* Operator (odwołanie w C#)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275844"
---
# <a name="-operator-c-reference"></a>* — Operator (odwołanie w C#)
Operator mnożenia (`*`) oblicza iloczyn argumentów. Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory mnożenia.  

`*` Służy również jako operatora dereference, który umożliwia odczytywanie i zapisywanie do wskaźnika.
  
## <a name="remarks"></a>Uwagi  
 `*` Operator służy również do deklarować typów wskaźnikowych i usunąć odwołania do wskaźników. Ten operator jest możliwe tylko w kontekstach niebezpieczne, oznaczona za pomocą [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe i wymagający [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.  Dereference operator jest nazywana operator pośredni.  
  
 Typy definiowane przez użytkownika można przeciążać plik binarny `*` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
