---
title: '#pragma warning C# -Reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712471"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (odwołanie w C#)
Dyrektywa `#pragma warning` służy do włączania i wyłączania określonych ostrzeżeń.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametry  
 `warning-list`  
 Rozdzielana przecinkami lista numerów ostrzeżeń. Prefiks „CS” jest opcjonalny.  
  
 Jeżeli numery ostrzeżeń nie są wymienione, `disable` wyłącza wszystkie ostrzeżenia, a `restore` włącza wszystkie ostrzeżenia.  
  
> [!NOTE]
> Aby znaleźć numery ostrzeżeń w programie Visual Studio, należy skompilować projekt, a następnie znaleźć numery ostrzeżeń w oknie **Dane wyjściowe**.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
- [Błędy kompilatora C#](../compiler-messages/index.md)
