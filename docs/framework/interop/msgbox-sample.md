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
# <a name="msgbox-sample"></a><span data-ttu-id="b9ce0-102">MsgBox — Przykład</span><span class="sxs-lookup"><span data-stu-id="b9ce0-102">MsgBox Sample</span></span>
<span data-ttu-id="b9ce0-103">Ten przykład pokazuje, jak przekazywać typy ciągów według wartości jak w parametrach i kiedy używać pól <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="b9ce0-104">Przykład OknoKomunikatu używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="b9ce0-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="b9ce0-105">Element **MessageBox** wyeksportowany z User32. dll.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="b9ce0-106">W tym przykładzie Klasa `NativeMethods` zawiera zarządzany prototyp dla każdej funkcji niezarządzanej wywoływanej przez klasę `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-106">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="b9ce0-107">Zarządzane metody prototypów `MsgBox`, `MsgBox2`i `MsgBox3` mają różne deklaracje dla tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="b9ce0-108">Deklaracja dla `MsgBox2` generuje nieprawidłowe dane wyjściowe w oknie komunikatu, ponieważ typ znaku określony jako ANSI jest niezgodny z punktem wejścia `MessageBoxW`, który jest nazwą funkcji Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="b9ce0-109">Deklaracja `MsgBox3` tworzy niezgodność między polami **EntryPoint**, **charset**i **ExactSpelling** .</span><span class="sxs-lookup"><span data-stu-id="b9ce0-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="b9ce0-110">Gdy jest wywoływana, `MsgBox3` zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="b9ce0-111">Aby uzyskać szczegółowe informacje na temat nazewnictwa ciągów i organizowania nazw, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="b9ce0-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="b9ce0-112">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="b9ce0-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="b9ce0-113">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="b9ce0-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b9ce0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9ce0-114">See also</span></span>

- [<span data-ttu-id="b9ce0-115">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="b9ce0-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="b9ce0-116">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="b9ce0-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="b9ce0-117">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b9ce0-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="b9ce0-118">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="b9ce0-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
