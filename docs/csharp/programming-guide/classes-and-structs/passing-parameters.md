---
title: Przekazywanie parametrów — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705473"
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C#argumenty mogą być przekazywane do parametrów przez wartość lub przez odwołanie. Przekazywanie przez odwołanie umożliwia elementy członkowskie funkcji, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartość parametrów i mieć tę zmianę utrzymują się w środowisku wywołującym. Aby przekazać parametr przez odwołanie z zamiarem zmiany `ref`wartości, użyj słowa `out` kluczowego lub słowa kluczowego. Aby przekazać odwołanie z zamiarem uniknięcia kopiowania, ale `in` nie zmienia wartość, należy użyć modyfikatora. Dla uproszczenia tylko `ref` słowo kluczowe jest używane w przykładach w tym temacie. Aby uzyskać więcej informacji `in` `ref`na `out`temat różnicy między , i , zobacz [w](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), i [obecnie](../../language-reference/keywords/out-parameter-modifier.md).  
  
 W poniższym przykładzie przedstawiono różnicę między parametrami wartości i odwołania.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [Przekazywanie parametrów typu wartość](./passing-value-type-parameters.md)  
  
- [Przekazywanie parametrów typu odwołanie](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Metody](./methods.md)
