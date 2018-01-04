---
title: "MsgBox — Przykład"
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
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5dcabfadae35cad980d210806c47dab3f5a0082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msgbox-sample"></a>MsgBox — Przykład
W przykładzie pokazano sposób przekazywania typów ciąg według wartości, tak jak parametry i kiedy należy używać <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> pól.  
  
 MsgBox — przykład używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:  
  
-   **Element MessageBox** wyeksportowane z User32.dll.  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 W tym przykładzie `LibWrap` klasa zawiera zarządzanych prototypu dla każdej funkcji niezarządzanej wywoływane przez `MsgBoxSample` klasy. Metody zarządzanych prototypu `MsgBox`, `MsgBox2`, i `MsgBox3` mają różne deklaracje dla tego samego niezarządzanych funkcji.  
  
 Deklaracja `MsgBox2` tworzy nieprawidłowych danych wyjściowych w oknie komunikatu, ponieważ typ znaków, określony jako ANSI, jest niezgodny z punktem wejścia `MessageBoxW`, która jest nazwą funkcji Unicode. Deklaracja `MsgBox3` tworzy niezgodność między **punktu wejścia**, **CharSet**, i **opcję ExactSpelling** pól. Po wywołaniu `MsgBox3` zgłasza wyjątek. Aby uzyskać szczegółowe informacje na ciąg nazw i nazwę przekazywanie, zobacz [określający zestaw znaków](../../../docs/framework/interop/specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling ciągów](../../../docs/framework/interop/marshaling-strings.md)  
 [Typy danych wywołanie platformy](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Domyślny marshaling dla ciągów](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Określanie zestawu znaków](../../../docs/framework/interop/specifying-a-character-set.md)
