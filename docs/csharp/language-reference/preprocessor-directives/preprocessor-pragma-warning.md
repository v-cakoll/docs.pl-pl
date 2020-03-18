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
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="b5b1f-102">#pragma warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b5b1f-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="b5b1f-103">`#pragma warning`można włączyć lub wyłączyć niektóre ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="b5b1f-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5b1f-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5b1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5b1f-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="b5b1f-106">Lista numerów ostrzegawczych rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b5b1f-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="b5b1f-107">Prefiks "CS" jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b5b1f-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="b5b1f-108">Jeśli nie określono żadnych `disable` numerów ostrzegawczych, `restore` wyłącza wszystkie ostrzeżenia i włącza wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="b5b1f-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5b1f-109">Aby znaleźć numery ostrzeżeń w programie Visual Studio, skompiluj projekt, a następnie poszukaj numerów ostrzeżeń w oknie **Dane wyjściowe.**</span><span class="sxs-lookup"><span data-stu-id="b5b1f-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b1f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5b1f-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5b1f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5b1f-111">See also</span></span>

- [<span data-ttu-id="b5b1f-112">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="b5b1f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b5b1f-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b5b1f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b5b1f-114">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="b5b1f-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="b5b1f-115">Błędy kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="b5b1f-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
