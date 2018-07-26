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
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199254"
---
# <a name="object-c-reference"></a>object (odwołanie w C#)
`object` Typu jest aliasem dla <xref:System.Object> w .NET Framework. W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object>. Można przypisać wartości dowolnego typu do zmiennych typu `object`. Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*. Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe pokazuje, jak zmienne typu `object` może akceptować wartości dowolnego typu danych i w jaki sposób zmienne typu `object` można użyć metod na <xref:System.Object> z programu .NET Framework.  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)
