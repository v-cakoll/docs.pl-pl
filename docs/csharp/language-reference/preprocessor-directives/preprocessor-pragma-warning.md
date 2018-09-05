---
title: '#warning elementu pragma (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 89ff8151d55ac58a1b114f7727297704ce26b9a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557608"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (odwołanie w C#)
Dyrektywa `#pragma warning` służy do włączania i wyłączania określonych ostrzeżeń.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a>Parametry  
 `warning-list`  
 Rozdzielana przecinkami lista numerów ostrzeżeń. Prefiks „CS” jest opcjonalny.  
  
 Jeżeli numery ostrzeżeń nie są wymienione, `disable` wyłącza wszystkie ostrzeżenia, a `restore` włącza wszystkie ostrzeżenia.  
  
> [!NOTE]
>  	
Aby znaleźć numery ostrzeżeń w programie Visual Studio, należy skompilować projekt, a następnie znaleźć numery ostrzeżeń w oknie **Dane wyjściowe**.  
  
## <a name="example"></a>Przykład  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [Błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md)
