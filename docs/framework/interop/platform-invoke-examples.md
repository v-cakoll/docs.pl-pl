---
title: Przykłady wywołań platformy
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
ms.openlocfilehash: 358d1ce662d56b8c31124f4b3264ec25a0f94586
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181318"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="e6432-102">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="e6432-102">Platform Invoke Examples</span></span>
<span data-ttu-id="e6432-103">Poniższe przykłady pokazują, jak zdefiniować i wywołać **messagebox** funkcji w User32.dll, przekazując prosty ciąg jako argument.</span><span class="sxs-lookup"><span data-stu-id="e6432-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="e6432-104">W przykładach <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole jest ustawione na **Auto,** aby platforma docelowa określała szerokość znaku i kierowanie ciągiem.</span><span class="sxs-lookup"><span data-stu-id="e6432-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="e6432-105">Aby uzyskać dodatkowe przykłady, zobacz [Kierowanie danych z platformą Invoke](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="e6432-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6432-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6432-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="e6432-107">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="e6432-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="e6432-108">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="e6432-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
