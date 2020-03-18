---
title: '#error - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173409"
---
# <a name="error-c-reference"></a>#error (odwołanie w C#)
`#error`umożliwia wygenerowanie błędu zdefiniowanego przez użytkownika w usiuł [CS1029](../compiler-messages/cs1029.md) z określonej lokalizacji w kodzie. Przykład:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi  
 Powszechne stosowanie `#error` jest w dyrektywie warunkowej.  
  
 Możliwe jest również wygenerowanie ostrzeżenia zdefiniowanego przez użytkownika za pomocą [#warning](./preprocessor-warning.md).  
  
## <a name="example"></a>Przykład  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
