---
title: '#Ostrzeżenie - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659959"
---
# <a name="warning-c-reference"></a>#warning (odwołanie w C#)
`#warning` Umożliwia wygenerowanie [CS1030](../../misc/cs1030.md) poziom jednego ostrzeżenia kompilatora z określonej lokalizacji w kodzie. Na przykład:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi
 Typowym zastosowaniem `#warning` jest dyrektywa warunkowa. Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
## <a name="example"></a>Przykład  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
