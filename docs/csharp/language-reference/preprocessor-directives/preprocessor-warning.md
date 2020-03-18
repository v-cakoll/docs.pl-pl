---
title: '#ostrzeżenie — odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715067"
---
# <a name="warning-c-reference"></a>#warning (odwołanie w C#)
`#warning`umożliwia wygenerowanie ostrzeżenia kompilatora poziomu [1 CS1030](../../misc/cs1030.md) z określonej lokalizacji w kodzie. Przykład:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi
 Powszechne stosowanie `#warning` jest w dyrektywie warunkowej. Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika z [#error](./preprocessor-error.md).  
  
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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
