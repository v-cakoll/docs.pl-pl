---
title: "#<a name=\"pragma-warning-c-reference\"></a>warning elementu pragma (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma warning'
helpviewer_keywords: '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="8872d-102">#pragma warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8872d-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="8872d-103">`#pragma warning`można włączyć lub wyłączyć pewne ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8872d-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8872d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8872d-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8872d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8872d-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="8872d-106">Rozdzielana przecinkami lista numerów ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="8872d-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="8872d-107">Prefiks "CS" jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8872d-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="8872d-108">Jeśli numerów ostrzeżeń, które nie są określone, `disable` wyłącza wszystkie ostrzeżenia i `restore` włącza wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8872d-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8872d-109">Aby znaleźć numery ostrzeżeń w Visual Studio, skompilować projekt, a następnie znajdź numery ostrzeżeń w **dane wyjściowe** okna.</span><span class="sxs-lookup"><span data-stu-id="8872d-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8872d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8872d-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8872d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8872d-111">See Also</span></span>  
 [<span data-ttu-id="8872d-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8872d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8872d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8872d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8872d-114">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="8872d-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="8872d-115">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="8872d-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
