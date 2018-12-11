---
title: '#Błąd — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: b335dfeed23d43938c66f0753590af55ac99b12a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235599"
---
# <a name="error-c-reference"></a>#error (odwołanie w C#)
`#error` Umożliwia wygenerowanie [CS1029](../compiler-messages/cs1029.md) błędach zdefiniowane przez użytkownika z określonych lokalizacji w kodzie. Na przykład:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Uwagi  
 Typowym zastosowaniem `#error` jest dyrektywa warunkowa.  
  
 Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
