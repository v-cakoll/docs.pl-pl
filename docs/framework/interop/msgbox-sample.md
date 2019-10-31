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
ms.openlocfilehash: 9f1e6d58742f60b6043a4be9218b80b323cd523e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124111"
---
# <a name="msgbox-sample"></a>MsgBox — Przykład
Ten przykład pokazuje, jak przekazywać typy ciągów według wartości jak w parametrach i kiedy używać pól <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.  
  
 Przykład OknoKomunikatu używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:  
  
- Element **MessageBox** wyeksportowany z User32. dll.  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 W tym przykładzie Klasa `NativeMethods` zawiera zarządzany prototyp dla każdej funkcji niezarządzanej wywoływanej przez klasę `MsgBoxSample`. Zarządzane metody prototypów `MsgBox`, `MsgBox2`i `MsgBox3` mają różne deklaracje dla tej samej funkcji niezarządzanej.  
  
 Deklaracja dla `MsgBox2` generuje nieprawidłowe dane wyjściowe w oknie komunikatu, ponieważ typ znaku określony jako ANSI jest niezgodny z punktem wejścia `MessageBoxW`, który jest nazwą funkcji Unicode. Deklaracja `MsgBox3` tworzy niezgodność między polami **EntryPoint**, **charset**i **ExactSpelling** . Gdy jest wywoływana, `MsgBox3` zgłasza wyjątek. Aby uzyskać szczegółowe informacje na temat nazewnictwa ciągów i organizowania nazw, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Marshaling ciągów](marshaling-strings.md)
- [Domyślny marshaling dla ciągów](default-marshaling-for-strings.md)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Określanie zestawu znaków](specifying-a-character-set.md)
