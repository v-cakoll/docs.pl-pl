---
title: "namespace (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a>namespace (odwołanie w C#)
`namespace` — Słowo kluczowe służy do deklarowania zakresu, który zawiera zestaw obiektów pokrewnych. Przestrzeń nazw można użyć do organizowania elementów kodu i tworzenia unikatowych typów.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Uwagi  
 W przypadku przestrzeni nazw można zadeklarować co najmniej jeden z następujących typów:  
  
-   innej przestrzeni nazw  
  
-   [klasy](../../../csharp/language-reference/keywords/class.md)  
  
-   [Interfejs](../../../csharp/language-reference/keywords/interface.md)  
  
-   [— Struktura](../../../csharp/language-reference/keywords/struct.md)  
  
-   [wyliczenia](../../../csharp/language-reference/keywords/enum.md)  
  
-   [Delegowanie](../../../csharp/language-reference/keywords/delegate.md)  
  
 Czy jawnie zadeklarować przestrzeni nazw w pliku źródłowym C#, kompilator dodaje domyślnej przestrzeni nazw. Ta nienazwanej przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku. Wszelkie identyfikator w globalnej przestrzeni nazw jest dostępny do użytku w nazwanych przestrzeni nazw.  
  
 Przestrzenie nazw niejawnie mają dostęp publiczny i nie jest to można modyfikować. Omówienie modyfikatorów dostępu można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Jest możliwe określenie przestrzeni nazw w deklaracjach dwóch lub więcej. Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wywołania metody statycznej w zagnieżdżonych przestrzeni nazw.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Aby uzyskać więcej informacji  
 Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:  
  
-   [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Używanie usługi przestrzenie nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Porady: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [za pomocą](../../../csharp/language-reference/keywords/using.md)
