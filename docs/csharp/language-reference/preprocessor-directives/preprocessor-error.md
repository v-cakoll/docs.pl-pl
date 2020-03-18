---
title: '#error - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173409"
---
# <a name="error-c-reference"></a><span data-ttu-id="d9989-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d9989-102">#error (C# Reference)</span></span>
<span data-ttu-id="d9989-103">`#error`umożliwia wygenerowanie błędu zdefiniowanego przez użytkownika w usiuł [CS1029](../compiler-messages/cs1029.md) z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d9989-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="d9989-104">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d9989-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9989-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9989-105">Remarks</span></span>  
 <span data-ttu-id="d9989-106">Powszechne stosowanie `#error` jest w dyrektywie warunkowej.</span><span class="sxs-lookup"><span data-stu-id="d9989-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="d9989-107">Możliwe jest również wygenerowanie ostrzeżenia zdefiniowanego przez użytkownika za pomocą [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="d9989-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9989-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9989-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9989-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9989-109">See also</span></span>

- [<span data-ttu-id="d9989-110">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="d9989-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9989-111">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d9989-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9989-112">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="d9989-112">C# Preprocessor Directives</span></span>](./index.md)
