---
title: '#błąd — C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712523"
---
# <a name="error-c-reference"></a><span data-ttu-id="52ef2-102">#error (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="52ef2-102">#error (C# Reference)</span></span>
<span data-ttu-id="52ef2-103">`#error` umożliwia wygenerowanie błędu zdefiniowanego przez użytkownika [CS1029](../compiler-messages/cs1029.md) z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="52ef2-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="52ef2-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="52ef2-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="52ef2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52ef2-105">Remarks</span></span>  
 <span data-ttu-id="52ef2-106">Typowym zastosowaniem `#error` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="52ef2-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="52ef2-107">Istnieje również możliwość wygenerowania ostrzeżenia zdefiniowanego przez użytkownika przy użyciu dyrektywy [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="52ef2-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52ef2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="52ef2-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52ef2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52ef2-109">See also</span></span>

- [<span data-ttu-id="52ef2-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="52ef2-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="52ef2-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52ef2-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="52ef2-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="52ef2-112">C# Preprocessor Directives</span></span>](./index.md)
