---
title: "* Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 64c32def0935f4347f9aaccc2865b9cd33dd8a70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>* — Operator (odwołanie w C#)
Operator mnożenia (`*`), który oblicza iloczyn argumentów.  Ponadto dereference operator, który umożliwia odczytywanie i zapisywanie do wskaźnika.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory mnożenia.  
  
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
