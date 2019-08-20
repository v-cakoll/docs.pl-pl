---
title: '#Ostrzeżenie- C# odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608524"
---
# <a name="warning-c-reference"></a><span data-ttu-id="78b43-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="78b43-102">#warning (C# Reference)</span></span>
<span data-ttu-id="78b43-103">`#warning`umożliwia wygenerowanie ostrzeżenia kompilatora o poziomie [CS1030](../../misc/cs1030.md) z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="78b43-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="78b43-104">Przykład:</span><span class="sxs-lookup"><span data-stu-id="78b43-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="78b43-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78b43-105">Remarks</span></span>
 <span data-ttu-id="78b43-106">Typowym zastosowaniem `#warning` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="78b43-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="78b43-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="78b43-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78b43-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="78b43-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="78b43-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78b43-109">See also</span></span>

- [<span data-ttu-id="78b43-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="78b43-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78b43-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="78b43-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78b43-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="78b43-112">C# Preprocessor Directives</span></span>](./index.md)
