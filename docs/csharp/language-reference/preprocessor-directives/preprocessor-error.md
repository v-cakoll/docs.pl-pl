---
title: '#błąd — C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712523"
---
# <a name="error-c-reference"></a>#error (odwołanie w C#)
`#error` umożliwia wygenerowanie błędu zdefiniowanego przez użytkownika [CS1029](../compiler-messages/cs1029.md) z określonej lokalizacji w kodzie. Na przykład:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi  
 Typowym zastosowaniem `#error` jest dyrektywa warunkowa.  
  
 Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](./preprocessor-warning.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
