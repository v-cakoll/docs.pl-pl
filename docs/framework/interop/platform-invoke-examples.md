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
# <a name="platform-invoke-examples"></a>Przykłady wywołań platformy
W poniższych przykładach pokazano, jak definiować i wywoływać funkcję **MessageBox** w User32. dll, przekazując prosty ciąg jako argument. W przykładach <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pole jest ustawione na wartość **automatycznie** , aby umożliwić platformie docelowej określenie szerokości znaków i organizowania ciągu.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Aby uzyskać więcej przykładów, zobacz [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Określanie zestawu znaków](specifying-a-character-set.md)
