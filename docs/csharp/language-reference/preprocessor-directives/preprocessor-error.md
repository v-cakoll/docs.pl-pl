---
title: '#Błąd — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660024"
---
# <a name="error-c-reference"></a><span data-ttu-id="1492f-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1492f-102">#error (C# Reference)</span></span>
<span data-ttu-id="1492f-103">`#error` Umożliwia wygenerowanie [CS1029](../compiler-messages/cs1029.md) błędach zdefiniowane przez użytkownika z określonych lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1492f-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="1492f-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1492f-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="1492f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1492f-105">Remarks</span></span>  
 <span data-ttu-id="1492f-106">Typowym zastosowaniem `#error` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="1492f-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="1492f-107">Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="1492f-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1492f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1492f-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1492f-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1492f-109">See also</span></span>

- [<span data-ttu-id="1492f-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1492f-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="1492f-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1492f-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1492f-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="1492f-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
