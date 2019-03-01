---
title: 'Instrukcje: Definiowanie stałych wC#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: cf57589df2eb375f34d175939a7f685a4abf59a2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975423"
---
# <a name="how-to-define-constants-in-c"></a>Instrukcje: Definiowanie stałych w C\#
Stałe są pola, których wartości są ustawione na czas kompilacji i nie można go zmienić. Użyj stałych zapewnienie nazw opisowych, zamiast literałów numerycznych ("numery magic") dla specjalnych wartości.  
  
> [!NOTE]
>  W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora, nie może służyć do definiowania stałych w taki sposób, który jest zazwyczaj używany w językach C i C++.  
  
 Do definiowania wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego. Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Aby określić stałe całkowite inne niż, jednym z podejść jest aby je pogrupować w jednej klasie statycznej o nazwie `Constants`. Wymaga to czy wszystkie odwołania do stałych być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 Użycie kwalifikatora Nazwa klasy pomaga upewnić się, że Ty i inni korzystającymi z stała zna jest stała i nie może być modyfikowany.  
  
## <a name="see-also"></a>Zobacz także

- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
