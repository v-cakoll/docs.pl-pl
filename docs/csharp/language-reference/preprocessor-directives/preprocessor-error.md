---
title: '#Błąd (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186698"
---
# <a name="error-c-reference"></a><span data-ttu-id="7c9a8-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7c9a8-102">#error (C# Reference)</span></span>
<span data-ttu-id="7c9a8-103">`#error` Umożliwia wygenerowanie [CS1029](../compiler-messages/cs1029.md) błędach zdefiniowane przez użytkownika z określonych lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c9a8-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="7c9a8-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7c9a8-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="7c9a8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c9a8-105">Remarks</span></span>  
 <span data-ttu-id="7c9a8-106">Typowym zastosowaniem `#error` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="7c9a8-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="7c9a8-107">Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="7c9a8-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c9a8-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c9a8-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c9a8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c9a8-109">See Also</span></span>

- [<span data-ttu-id="7c9a8-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7c9a8-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7c9a8-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7c9a8-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7c9a8-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="7c9a8-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
