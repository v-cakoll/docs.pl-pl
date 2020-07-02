---
title: Przykłady wywołań platformy
description: Zobacz przykład wywołania platformy, który ilustruje sposób definiowania i wywoływania funkcji MessageBox w User32.dll.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 97b0720b8954bc24a4058e6a03c32d32bd9e3180
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620810"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="4fc01-103">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="4fc01-103">Platform Invoke Examples</span></span>
<span data-ttu-id="4fc01-104">W poniższych przykładach pokazano, jak definiować i wywoływać funkcję **MessageBox** w User32.dll, przekazując prosty ciąg jako argument.</span><span class="sxs-lookup"><span data-stu-id="4fc01-104">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="4fc01-105">W przykładach <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole jest ustawione na wartość **automatycznie** , aby umożliwić platformie docelowej określenie szerokości znaków i organizowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="4fc01-105">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="4fc01-106">Aby uzyskać więcej przykładów, zobacz [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="4fc01-106">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc01-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fc01-107">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4fc01-108">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="4fc01-108">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4fc01-109">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="4fc01-109">Specifying a Character Set</span></span>](specifying-a-character-set.md)
