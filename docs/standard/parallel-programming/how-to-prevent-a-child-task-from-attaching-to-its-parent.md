---
title: 'Instrukcje: Zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7506a57e29b7942bd06141baa2d2b048ed998214
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221534"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="4bc21-102">Instrukcje: Zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym</span><span class="sxs-lookup"><span data-stu-id="4bc21-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="4bc21-103">Ten dokument przedstawia sposób zapobiec łączeniu zadania podrzędnego z zadaniem do zadania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bc21-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="4bc21-104">Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym jest przydatne w przypadku, gdy wywołujesz składnik, który jest zapisywany przez stronę trzecią i używa również zadania.</span><span class="sxs-lookup"><span data-stu-id="4bc21-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="4bc21-105">Na przykład składnikiem innej firmy, który używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu może spowodować problemy w kodzie, gdy jest długotrwałe lub zwraca nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4bc21-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bc21-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bc21-106">Example</span></span>  
 <span data-ttu-id="4bc21-107">W poniższym przykładzie porównano skutki przy użyciu opcji domyślnej do efektów uniemożliwianie zadaniu podrzędnemu dołączania do elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bc21-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="4bc21-108">W przykładzie jest tworzony <xref:System.Threading.Tasks.Task> obiekt, który wywołuje bibliotekę innych firm, która używa również <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bc21-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="4bc21-109">Używa biblioteki innego producenta <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bc21-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="4bc21-110">Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby utworzyć zadanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4bc21-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="4bc21-111">Ta opcja powoduje, że środowisko uruchomieniowe, aby usunąć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specyfikacji w zadaniach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4bc21-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="4bc21-112">Ponieważ zadanie nadrzędne nie zakończy się aż do zakończenia wszystkich zadań podrzędnych, długo uruchamiające się zadanie podrzędne może spowodować cała aplikacja do niskiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="4bc21-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="4bc21-113">W tym przykładzie Jeśli aplikacja używa domyślnych opcji do utworzenia zadania nadrzędnego, zadanie podrzędne musi zakończyć przed zakończeniem zadania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bc21-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="4bc21-114">Jeśli aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji element podrzędny nie jest dołączony do obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bc21-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="4bc21-115">Aplikację można wykonać dodatkową pracę, po zakończeniu zadania nadrzędnego i przed musi czekać na zakończenie zadania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4bc21-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4bc21-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4bc21-116">Compiling the Code</span></span>  
 <span data-ttu-id="4bc21-117">Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DenyChildAttach.cs` (`DenyChildAttach.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w wierszu polecenia dla deweloperów programu Visual Studio okna.</span><span class="sxs-lookup"><span data-stu-id="4bc21-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Developer Command Prompt for Visual Studio window.</span></span>  
  
 <span data-ttu-id="4bc21-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="4bc21-118">Visual C#</span></span>  
  
 <span data-ttu-id="4bc21-119">**CSC.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="4bc21-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="4bc21-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bc21-120">Visual Basic</span></span>  
  
 <span data-ttu-id="4bc21-121">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="4bc21-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4bc21-122">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="4bc21-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc21-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bc21-123">See also</span></span>

- [<span data-ttu-id="4bc21-124">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="4bc21-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
