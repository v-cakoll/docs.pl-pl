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
ms.openlocfilehash: 8b88a07115871e48a7981bbb868ff2ef4ce8cf85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127702"
---
# <a name="msgbox-sample"></a><span data-ttu-id="413e6-102">MsgBox — Przykład</span><span class="sxs-lookup"><span data-stu-id="413e6-102">MsgBox Sample</span></span>
<span data-ttu-id="413e6-103">Niniejszy przykład pokazuje, jak przekazać typów ciągów według wartości, tak jak parametry i kiedy należy używać <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> pola.</span><span class="sxs-lookup"><span data-stu-id="413e6-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="413e6-104">MsgBox — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="413e6-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="413e6-105">**MessageBox** wyeksportowane z User32.dll.</span><span class="sxs-lookup"><span data-stu-id="413e6-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="413e6-106">W tym przykładzie `LibWrap` klasa zawiera zarządzane prototypu dla każdej funkcji niezarządzanych wywoływane przez `MsgBoxSample` klasy.</span><span class="sxs-lookup"><span data-stu-id="413e6-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="413e6-107">Zarządzane metody prototypu `MsgBox`, `MsgBox2`, i `MsgBox3` mają różne deklaracje dla tego samego niezarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="413e6-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="413e6-108">Deklaracja `MsgBox2` tworzy nieprawidłowych danych wyjściowych w oknie komunikatu, ponieważ typ znaku, określony jako ANSI, jest niezgodny z punktem wejścia `MessageBoxW`, czyli nazwę funkcji standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="413e6-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="413e6-109">Deklaracja `MsgBox3` tworzy niezgodność między **punktu wejścia**, **CharSet**, i **ExactSpelling** pola.</span><span class="sxs-lookup"><span data-stu-id="413e6-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="413e6-110">Po wywołaniu `MsgBox3` zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="413e6-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="413e6-111">Szczegółowe informacje na temat nazewnictwa ciągu i organizowanie nazwy, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="413e6-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="413e6-112">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="413e6-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="413e6-113">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="413e6-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="413e6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="413e6-114">See also</span></span>

- [<span data-ttu-id="413e6-115">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="413e6-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="413e6-116">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="413e6-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="413e6-117">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="413e6-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="413e6-118">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="413e6-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
