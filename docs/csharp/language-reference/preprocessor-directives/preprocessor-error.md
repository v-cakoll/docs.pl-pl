---
title: '#błąd — C# odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: f18dbd007e80397b815256231a1d56e5ca50010e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608556"
---
# <a name="error-c-reference"></a><span data-ttu-id="265e6-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="265e6-102">#error (C# Reference)</span></span>
<span data-ttu-id="265e6-103">`#error`umożliwia wygenerowanie [CS1029](../compiler-messages/cs1029.md) błędu zdefiniowanego przez użytkownika z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="265e6-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="265e6-104">Przykład:</span><span class="sxs-lookup"><span data-stu-id="265e6-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="265e6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="265e6-105">Remarks</span></span>  
 <span data-ttu-id="265e6-106">Typowym zastosowaniem `#error` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="265e6-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="265e6-107">Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="265e6-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="265e6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="265e6-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="265e6-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="265e6-109">See also</span></span>

- [<span data-ttu-id="265e6-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="265e6-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="265e6-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="265e6-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="265e6-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="265e6-112">C# Preprocessor Directives</span></span>](./index.md)
