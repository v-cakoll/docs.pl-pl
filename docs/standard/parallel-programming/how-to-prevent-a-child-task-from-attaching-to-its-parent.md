---
title: 'Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 654bfec4e8ba163c9dc9adf470c45401c0babd8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="f4970-102">Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym</span><span class="sxs-lookup"><span data-stu-id="f4970-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="f4970-103">Ten dokument pokazano, jak zapobiec łączeniu zadania podrzędnego z odpowiadającym zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="f4970-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="f4970-104">Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym jest przydatne, gdy wywołanie składnika, która została napisana przez innych firm i używa również zadania.</span><span class="sxs-lookup"><span data-stu-id="f4970-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="f4970-105">Na przykład składnikiem innej firmy, który używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu może spowodować problemy w kodzie, jeśli jest długotrwałe lub nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f4970-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4970-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4970-106">Example</span></span>  
 <span data-ttu-id="f4970-107">Poniższy przykład porównuje skutków przy użyciu opcji domyślnych skutki zapobieganie zadania podrzędnego z odpowiadającym zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="f4970-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="f4970-108">W przykładzie jest tworzony <xref:System.Threading.Tasks.Task> obiektu, który odwołuje się do biblioteki innej firmy, który także używa <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4970-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="f4970-109">Biblioteka innych firm używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4970-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="f4970-110">Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby utworzyć zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="f4970-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="f4970-111">Ta opcja powoduje, że środowisko uruchomieniowe, aby usunąć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> Specyfikacja zadania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4970-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="f4970-112">Ponieważ zadaniem nadrzędnym nie zakończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadania podrzędnego może spowodować ogólną aplikacji do niskiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="f4970-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="f4970-113">W tym przykładzie Jeśli aplikacja używa domyślnych opcji, można utworzyć zadania nadrzędnego zadania podrzędnego musi zakończyć przed zakończeniem zadaniem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="f4970-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="f4970-114">Jeśli aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji, obiekt podrzędny nie jest dołączony do obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f4970-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="f4970-115">Aplikacja może wykonywać dodatkowe czynności, po zakończeniu zadania nadrzędnego i przed należy poczekać na zakończenie zadania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4970-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4970-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f4970-116">Compiling the Code</span></span>  
 <span data-ttu-id="f4970-117">Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DenyChildAttach.cs` (`DenyChildAttach.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f4970-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="f4970-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="f4970-118">Visual C#</span></span>  
  
 <span data-ttu-id="f4970-119">**CSC.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="f4970-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="f4970-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4970-120">Visual Basic</span></span>  
  
 <span data-ttu-id="f4970-121">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="f4970-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f4970-122">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f4970-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4970-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4970-123">See Also</span></span>  
 [<span data-ttu-id="f4970-124">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="f4970-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
