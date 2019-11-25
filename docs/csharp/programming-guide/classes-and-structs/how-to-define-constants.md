---
title: Jak definiować stałe wC#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 6681b1987ec9b5bce40b3abffb9b7d11d4a82bcc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970958"
---
# <a name="how-to-define-constants-in-c"></a>Jak definiować stałe w języku C\#
Stałe są polami, których wartości są ustawiane w czasie kompilacji i nigdy nie mogą być zmieniane. Użyj stałych, aby podać znaczące nazwy zamiast literałów liczbowych ("liczby magiczne") dla specjalnych wartości.  
  
> [!NOTE]
> W C# dyrektywie preprocesora [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nie można używać do definiowania stałych w sposób, który jest zazwyczaj używany w C i C++.  
  
 Aby zdefiniować stałe wartości typów całkowitych (`int`, `byte`itd.), użyj typu wyliczeniowego. Aby uzyskać więcej informacji, zobacz [Wyliczenie](../../language-reference/keywords/enum.md).  
  
 Aby zdefiniować niecałkowite stałe, jedno podejście polega na pogrupowania ich w pojedynczej klasie statycznej o nazwie `Constants`. To wymaga, aby wszystkie odwołania do stałych były poprzedzone nazwą klasy, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Użycie kwalifikatora nazwy klasy pomaga upewnić się, że i inne osoby, które używają stałej, wiedzą, że jest stała i nie mogą być modyfikowane.  
  
## <a name="see-also"></a>Zobacz także

- [Klasy i struktury](./index.md)
