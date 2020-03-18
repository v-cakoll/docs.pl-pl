---
title: '#ostrzeżenie pragma - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712471"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (odwołanie w C#)
`#pragma warning`można włączyć lub wyłączyć niektóre ostrzeżenia.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametry  
 `warning-list`  
 Lista numerów ostrzegawczych rozdzielonych przecinkami. Prefiks "CS" jest opcjonalny.  
  
 Jeśli nie określono żadnych `disable` numerów ostrzegawczych, `restore` wyłącza wszystkie ostrzeżenia i włącza wszystkie ostrzeżenia.  
  
> [!NOTE]
> Aby znaleźć numery ostrzeżeń w programie Visual Studio, skompiluj projekt, a następnie poszukaj numerów ostrzeżeń w oknie **Dane wyjściowe.**  
  
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

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
- [Błędy kompilatora Języka C#](../compiler-messages/index.md)
