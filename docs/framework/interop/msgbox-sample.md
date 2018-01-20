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
ms.openlocfilehash: 0b14ee9c435d36e8d6a49cbfb29a57365bcd42d6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="msgbox-sample"></a><span data-ttu-id="754f9-102">MsgBox — Przykład</span><span class="sxs-lookup"><span data-stu-id="754f9-102">MsgBox Sample</span></span>
<span data-ttu-id="754f9-103">W przykładzie pokazano sposób przekazywania typów ciąg według wartości, tak jak parametry i kiedy należy używać <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, i <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> pól.</span><span class="sxs-lookup"><span data-stu-id="754f9-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="754f9-104">MsgBox — przykład używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="754f9-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="754f9-105">**Element MessageBox** wyeksportowane z User32.dll.</span><span class="sxs-lookup"><span data-stu-id="754f9-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="754f9-106">W tym przykładzie `LibWrap` klasa zawiera zarządzanych prototypu dla każdej funkcji niezarządzanej wywoływane przez `MsgBoxSample` klasy.</span><span class="sxs-lookup"><span data-stu-id="754f9-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="754f9-107">Metody zarządzanych prototypu `MsgBox`, `MsgBox2`, i `MsgBox3` mają różne deklaracje dla tego samego niezarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="754f9-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="754f9-108">Deklaracja `MsgBox2` tworzy nieprawidłowych danych wyjściowych w oknie komunikatu, ponieważ typ znaków, określony jako ANSI, jest niezgodny z punktem wejścia `MessageBoxW`, która jest nazwą funkcji Unicode.</span><span class="sxs-lookup"><span data-stu-id="754f9-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="754f9-109">Deklaracja `MsgBox3` tworzy niezgodność między **punktu wejścia**, **CharSet**, i **opcję ExactSpelling** pól.</span><span class="sxs-lookup"><span data-stu-id="754f9-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="754f9-110">Po wywołaniu `MsgBox3` zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="754f9-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="754f9-111">Aby uzyskać szczegółowe informacje na ciąg nazw i nazwę przekazywanie, zobacz [określający zestaw znaków](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="754f9-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="754f9-112">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="754f9-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="754f9-113">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="754f9-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="754f9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="754f9-114">See Also</span></span>  
 [<span data-ttu-id="754f9-115">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="754f9-115">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="754f9-116">Typy danych wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="754f9-116">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="754f9-117">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="754f9-117">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [<span data-ttu-id="754f9-118">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="754f9-118">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="754f9-119">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="754f9-119">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
