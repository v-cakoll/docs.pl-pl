---
title: 'Porady: definiowanie stałych w C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 03912a71aba883ec9127d265e6f1a2b05e1e60fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313225"
---
# <a name="how-to-define-constants-in-c"></a>Porady: definiowanie stałych w C#
Stałe są pól, których wartości są ustawione na czas kompilacji i nie można go zmienić. Stałe umożliwia uzyskanie łatwy do rozpoznania nazwy zamiast literałach numerycznych ("numery magic") dla specjalnych wartości.  
  
> [!NOTE]
>  W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora nie może służyć do definiowania stałe w taki sposób, który jest zwykle używany w C i C++.  
  
 Aby zdefiniować wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego. Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Aby zdefiniować niecałkowity stałe, jednym z podejść jest do grupowania ich w jednej klasy statycznej o nazwie `Constants`. Wymaga to czy wszystkie odwołania do stałe być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 Użycie Kwalifikator nazwy klasy pomaga, upewnij się, że użytkowników zastosować stałą rozumiesz jest stała i nie może być modyfikowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
