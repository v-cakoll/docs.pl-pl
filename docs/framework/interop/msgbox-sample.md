---
title: MsgBox — Przykład
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c4d38b60f349f0ecb87204cb980dd6681a8cc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
  
 Deklaracja `MsgBox2` tworzy nieprawidłowych danych wyjściowych w oknie komunikatu, ponieważ typ znaków, określony jako ANSI, jest niezgodny z punktem wejścia `MessageBoxW`, która jest nazwą funkcji Unicode. Deklaracja `MsgBox3` tworzy niezgodność między **punktu wejścia**, **CharSet**, i **opcję ExactSpelling** pól. Po wywołaniu `MsgBox3` zgłasza wyjątek. Aby uzyskać szczegółowe informacje na ciąg nazw i nazwę przekazywanie, zobacz [określający zestaw znaków](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling ciągów](marshaling-strings.md)  
 [Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Domyślny marshaling dla ciągów](default-marshaling-for-strings.md)  
 [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)  
 [Określanie zestawu znaków](specifying-a-character-set.md)
