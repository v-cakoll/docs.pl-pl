---
title: 'Instrukcje: Definiowanie stałych w języku C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: a85e7728512922be38658c07314229c26b2461fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646452"
---
# <a name="how-to-define-constants-in-c"></a>Instrukcje: Definiowanie stałych w C\#
Stałe są pola, których wartości są ustawione na czas kompilacji i nie można go zmienić. Użyj stałych zapewnienie nazw opisowych, zamiast literałów numerycznych ("numery magic") dla specjalnych wartości.  
  
> [!NOTE]
>  W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora, nie może służyć do definiowania stałych w taki sposób, który jest zazwyczaj używany w językach C i C++.  
  
 Do definiowania wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego. Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Aby określić stałe całkowite inne niż, jednym z podejść jest aby je pogrupować w jednej klasie statycznej o nazwie `Constants`. Wymaga to czy wszystkie odwołania do stałych być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Użycie kwalifikatora Nazwa klasy pomaga upewnić się, że Ty i inni korzystającymi z stała zna jest stała i nie może być modyfikowany.  
  
## <a name="see-also"></a>Zobacz także

- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
