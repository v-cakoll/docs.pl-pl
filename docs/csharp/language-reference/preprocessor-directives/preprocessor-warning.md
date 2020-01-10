---
title: '#Ostrzeżenie- C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715067"
---
# <a name="warning-c-reference"></a>#warning (odwołanie w C#)
`#warning` umożliwia wygenerowanie ostrzeżenia kompilatora o poziomie [CS1030](../../misc/cs1030.md) z określonej lokalizacji w kodzie. Na przykład:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi
 Typowym zastosowaniem `#warning` jest dyrektywa warunkowa. Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](./preprocessor-error.md).  
  
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

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
