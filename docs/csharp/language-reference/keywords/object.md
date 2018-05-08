---
title: object (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-c-reference"></a>object (odwołanie w C#)
`object` Typu jest aliasem <xref:System.Object> w programie .NET Framework. W systemie typów ujednoliconego C#, wszystkie typy, typy referencyjne wstępnie zdefiniowanych i zdefiniowanych przez użytkownika i typów wartości, dziedziczy pośrednio ani bezpośrednio po <xref:System.Object>. Można przypisać wartości dowolnego typu do zmiennych typu `object`. Gdy zmienna typu wartości jest konwertowana na obiekt, jest określany jako *opakowany*. Gdy zmienna typu obiektu jest konwertowany na typ wartości, jest określany jako *rozpakowany*. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe pokazuje, jak zmiennych typu `object` może akceptować wartości każdego typu danych i w jaki sposób zmienne typu `object` można używać metod na <xref:System.Object> z programu .NET Framework.  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)
