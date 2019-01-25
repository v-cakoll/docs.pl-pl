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
ms.openlocfilehash: bef8ce86a3dba5449e50c890b09acdee1375317c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719550"
---
# <a name="msgbox-sample"></a><span data-ttu-id="5cdb4-102">MsgBox — Przykład</span><span class="sxs-lookup"><span data-stu-id="5cdb4-102">MsgBox Sample</span></span>
<span data-ttu-id="5cdb4-103">Niniejszy przykład pokazuje, jak przekazać typów ciągów według wartości, tak jak parametry i kiedy należy używać <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> pola.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="5cdb4-104">MsgBox — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="5cdb4-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="5cdb4-105">**MessageBox** wyeksportowane z User32.dll.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="5cdb4-106">W tym przykładzie `LibWrap` klasa zawiera zarządzane prototypu dla każdej funkcji niezarządzanych wywoływane przez `MsgBoxSample` klasy.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="5cdb4-107">Zarządzane metody prototypu `MsgBox`, `MsgBox2`, i `MsgBox3` mają różne deklaracje dla tego samego niezarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="5cdb4-108">Deklaracja `MsgBox2` tworzy nieprawidłowych danych wyjściowych w oknie komunikatu, ponieważ typ znaku, określony jako ANSI, jest niezgodny z punktem wejścia `MessageBoxW`, czyli nazwę funkcji standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="5cdb4-109">Deklaracja `MsgBox3` tworzy niezgodność między **punktu wejścia**, **CharSet**, i **ExactSpelling** pola.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="5cdb4-110">Po wywołaniu `MsgBox3` zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5cdb4-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="5cdb4-111">Szczegółowe informacje na temat nazewnictwa ciągu i organizowanie nazwy, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="5cdb4-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="5cdb4-112">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5cdb4-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="5cdb4-113">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5cdb4-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdb4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cdb4-114">See also</span></span>
- [<span data-ttu-id="5cdb4-115">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="5cdb4-115">Marshaling Strings</span></span>](marshaling-strings.md)
- <span data-ttu-id="5cdb4-116">[Typy danych w wywołaniu platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5cdb4-116">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>
- [<span data-ttu-id="5cdb4-117">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="5cdb4-117">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="5cdb4-118">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="5cdb4-118">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="5cdb4-119">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="5cdb4-119">Specifying a Character Set</span></span>](specifying-a-character-set.md)
