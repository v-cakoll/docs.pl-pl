---
title: "Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="c5900-102">Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym</span><span class="sxs-lookup"><span data-stu-id="c5900-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="c5900-103">Ten dokument pokazano, jak zapobiec łączeniu zadania podrzędnego z odpowiadającym zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c5900-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="c5900-104">Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym jest przydatne, gdy wywołanie składnika, która została napisana przez innych firm i używa również zadania.</span><span class="sxs-lookup"><span data-stu-id="c5900-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="c5900-105">Na przykład składnikiem innej firmy, który używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu może spowodować problemy w kodzie, jeśli jest długotrwałe lub nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5900-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5900-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5900-106">Example</span></span>  
 <span data-ttu-id="c5900-107">Poniższy przykład porównuje skutków przy użyciu opcji domyślnych skutki zapobieganie zadania podrzędnego z odpowiadającym zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c5900-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="c5900-108">W przykładzie jest tworzony <xref:System.Threading.Tasks.Task> obiektu, który odwołuje się do biblioteki innej firmy, który także używa <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5900-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="c5900-109">Biblioteka innych firm używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5900-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="c5900-110">Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby utworzyć zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c5900-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="c5900-111">Ta opcja powoduje, że środowisko uruchomieniowe, aby usunąć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> Specyfikacja zadania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5900-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="c5900-112">Ponieważ zadaniem nadrzędnym nie zakończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadania podrzędnego może spowodować ogólną aplikacji do niskiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="c5900-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="c5900-113">W tym przykładzie Jeśli aplikacja używa domyślnych opcji, można utworzyć zadania nadrzędnego zadania podrzędnego musi zakończyć przed zakończeniem zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c5900-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="c5900-114">Jeśli aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji, obiekt podrzędny nie jest dołączony do obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c5900-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="c5900-115">Aplikacja może wykonywać dodatkowe czynności, po zakończeniu zadania nadrzędnego i przed należy poczekać na zakończenie zadania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5900-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5900-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c5900-116">Compiling the Code</span></span>  
 <span data-ttu-id="c5900-117">Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DenyChildAttach.cs` (`DenyChildAttach.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5900-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="c5900-118">**CSC.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="c5900-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="c5900-119">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="c5900-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c5900-120">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c5900-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5900-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5900-121">See Also</span></span>  
 [<span data-ttu-id="c5900-122">Programowanie asynchroniczne opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="c5900-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
