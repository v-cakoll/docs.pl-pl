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
ms.openlocfilehash: b970a5a193f82ca141c030491febce5ef352eb70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181347"
---
# <a name="msgbox-sample"></a><span data-ttu-id="e5576-102">MsgBox — Przykład</span><span class="sxs-lookup"><span data-stu-id="e5576-102">MsgBox Sample</span></span>
<span data-ttu-id="e5576-103">Ten przykład pokazuje, jak przekazywać typy ciągów według wartości, jak w parametrach i kiedy <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>należy <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>używać pól <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> ,, i.</span><span class="sxs-lookup"><span data-stu-id="e5576-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="e5576-104">Przykład OknoKomunikatu używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="e5576-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="e5576-105">Element **MessageBox** wyeksportowany z User32. dll.</span><span class="sxs-lookup"><span data-stu-id="e5576-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="e5576-106">W tym przykładzie `NativeMethods` Klasa zawiera zarządzany prototyp dla każdej funkcji niezarządzanej wywoływanej przez `MsgBoxSample` klasę.</span><span class="sxs-lookup"><span data-stu-id="e5576-106">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="e5576-107">Zarządzane metody `MsgBox`prototypów, `MsgBox2`i `MsgBox3` mają różne deklaracje dla tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="e5576-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="e5576-108">Deklaracja dla `MsgBox2` generuje nieprawidłowe dane wyjściowe w oknie komunikatu, ponieważ typ znaku określony jako ANSI jest niezgodny z punktem `MessageBoxW`wejścia, który jest nazwą funkcji Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5576-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="e5576-109">Deklaracja `MsgBox3` dla tworzy niezgodność między polami **EntryPoint**, **charset**i **ExactSpelling** .</span><span class="sxs-lookup"><span data-stu-id="e5576-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="e5576-110">Gdy wywoływana, `MsgBox3` zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e5576-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="e5576-111">Aby uzyskać szczegółowe informacje na temat nazewnictwa ciągów i organizowania nazw, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="e5576-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="e5576-112">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="e5576-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="e5576-113">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="e5576-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e5576-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5576-114">See also</span></span>

- [<span data-ttu-id="e5576-115">Organizowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="e5576-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="e5576-116">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="e5576-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="e5576-117">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="e5576-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="e5576-118">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="e5576-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
