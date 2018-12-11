---
title: '#Ostrzeżenie - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 08fcefd904ad43c781017087082592120e21f5cd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236833"
---
# <a name="warning-c-reference"></a><span data-ttu-id="88fe7-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="88fe7-102">#warning (C# Reference)</span></span>
<span data-ttu-id="88fe7-103">`#warning` Umożliwia wygenerowanie [CS1030](../../misc/cs1030.md) poziom jednego ostrzeżenia kompilatora z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="88fe7-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="88fe7-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="88fe7-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="88fe7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88fe7-105">Remarks</span></span>
 <span data-ttu-id="88fe7-106">Typowym zastosowaniem `#warning` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="88fe7-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="88fe7-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="88fe7-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88fe7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="88fe7-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="88fe7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88fe7-109">See Also</span></span>

- [<span data-ttu-id="88fe7-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="88fe7-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="88fe7-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88fe7-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="88fe7-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="88fe7-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
