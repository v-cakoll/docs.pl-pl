---
title: '#Błąd (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-c-reference"></a><span data-ttu-id="57ed3-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="57ed3-102">#error (C# Reference)</span></span>
<span data-ttu-id="57ed3-103">`#error` Umożliwia generowanie błędu z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="57ed3-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="57ed3-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="57ed3-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="57ed3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57ed3-105">Remarks</span></span>  
 <span data-ttu-id="57ed3-106">Typowym zastosowaniem `#error` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="57ed3-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="57ed3-107">Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="57ed3-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ed3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="57ed3-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57ed3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57ed3-109">See Also</span></span>  
 [<span data-ttu-id="57ed3-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="57ed3-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="57ed3-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="57ed3-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="57ed3-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="57ed3-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
