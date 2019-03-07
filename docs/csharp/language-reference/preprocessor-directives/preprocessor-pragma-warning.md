---
title: '#warning elementu pragma - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 0145df533572ff9d5004a653bb232a7ff60af5f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495107"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="aa476-102">#pragma warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="aa476-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="aa476-103">Dyrektywa `#pragma warning` służy do włączania i wyłączania określonych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="aa476-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa476-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa476-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa476-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa476-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="aa476-106">Rozdzielana przecinkami lista numerów ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="aa476-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="aa476-107">Prefiks „CS” jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="aa476-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="aa476-108">Jeżeli numery ostrzeżeń nie są wymienione, `disable` wyłącza wszystkie ostrzeżenia, a `restore` włącza wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="aa476-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa476-109">Aby znaleźć numery ostrzeżeń w programie Visual Studio, należy skompilować projekt, a następnie znaleźć numery ostrzeżeń w oknie **Dane wyjściowe**.</span><span class="sxs-lookup"><span data-stu-id="aa476-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa476-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa476-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa476-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa476-111">See also</span></span>

- [<span data-ttu-id="aa476-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa476-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="aa476-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aa476-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="aa476-114">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="aa476-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="aa476-115">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="aa476-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
