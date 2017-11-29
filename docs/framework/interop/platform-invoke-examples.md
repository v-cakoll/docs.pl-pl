---
title: "Przykłady wywołań platformy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 892d014060de869959835dc980a8d153908ca63c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="8528d-102">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="8528d-102">Platform Invoke Examples</span></span>
<span data-ttu-id="8528d-103">W poniższych przykładach pokazano sposób definiowania i wywołać **MessageBox** w User32.dll, przekazując prostego ciągu jako argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="8528d-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="8528d-104">W przykładach <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole jest ustawione na **automatycznie** aby umożliwić platformy docelowej określa szerokość znaków i ciągu przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="8528d-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="8528d-105">Aby uzyskać dodatkowe przykłady, zobacz [organizowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="8528d-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8528d-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8528d-106">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="8528d-107">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="8528d-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="8528d-108">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="8528d-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
