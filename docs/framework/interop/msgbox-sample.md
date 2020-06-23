---
title: MsgBox — Przykład
description: Zobacz przykład przekazywania typów ciągu według wartości, jak w parametrach przy użyciu OknoKomunikatu. Pokazuje, kiedy używać pól EntryPoint, CharSet i ExactSpelling w programie .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: ccf882e1f801dd18e5b65a4279fc580d927dd29d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904094"
---
# <a name="msgbox-sample"></a>MsgBox — Przykład
Ten przykład pokazuje, jak przekazywać typy ciągów według wartości, jak w parametrach i kiedy należy używać <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint> <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pól,, i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> .  
  
 Przykład OknoKomunikatu używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:  
  
- Element **MessageBox** wyeksportowany z User32.dll.  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 W tym przykładzie `NativeMethods` Klasa zawiera zarządzany prototyp dla każdej funkcji niezarządzanej wywoływanej przez `MsgBoxSample` klasę. Zarządzane metody prototypów `MsgBox` , `MsgBox2` i `MsgBox3` mają różne deklaracje dla tej samej funkcji niezarządzanej.  
  
 Deklaracja dla `MsgBox2` generuje nieprawidłowe dane wyjściowe w oknie komunikatu, ponieważ typ znaku określony jako ANSI jest niezgodny z punktem wejścia `MessageBoxW` , który jest nazwą funkcji Unicode. Deklaracja dla `MsgBox3` tworzy niezgodność między polami **EntryPoint**, **charset**i **ExactSpelling** . Gdy wywoływana, `MsgBox3` zgłasza wyjątek. Aby uzyskać szczegółowe informacje na temat nazewnictwa ciągów i organizowania nazw, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Deklarowanie prototypów  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Wywoływanie funkcji  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Organizowanie ciągów](marshaling-strings.md)
- [Organizowanie domyślne dotyczące ciągów](default-marshaling-for-strings.md)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Określanie zestawu znaków](specifying-a-character-set.md)
