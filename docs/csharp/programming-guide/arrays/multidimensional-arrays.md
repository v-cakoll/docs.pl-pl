---
title: Tablice wielowymiarowe — Przewodnik programowania w języku C#
description: Tablice w języku C# mogą mieć więcej niż jeden wymiar. Ta przykładowa deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475011"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Tablice wielowymiarowe (Przewodnik programowania w języku C#)

Tablice mogą mieć więcej niż jeden wymiar. Na przykład następująca deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Poniższa deklaracja tworzy tablicę trzech wymiarów, 4, 2 i 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy

 Tablicę można zainicjować po deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Możesz również zainicjować tablicę bez określania rangi.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Jeśli zdecydujesz się zadeklarować zmienną tablicową bez inicjalizacji, musisz użyć `new` operatora, aby przypisać tablicę do zmiennej. Użycie `new` jest pokazane w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Poniższy przykład przypisuje wartość do określonego elementu tablicy.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Podobnie Poniższy przykład pobiera wartość określonego elementu tablicy i przypisuje go do zmiennej `elementValue` .  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Poniższy przykład kodu inicjuje elementy tablicy do wartości domyślnych (z wyjątkiem tablic nieregularnych).  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
