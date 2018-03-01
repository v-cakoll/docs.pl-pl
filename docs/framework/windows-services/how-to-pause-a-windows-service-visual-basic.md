---
title: "Porady: wstrzymywanie usług systemu Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 90f2b01fae057a05cc71f77cecea3fdf85c832b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="12eeb-102">Porady: wstrzymywanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12eeb-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="12eeb-103">W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnika można wstrzymać usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="12eeb-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12eeb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="12eeb-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="12eeb-105">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="12eeb-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="12eeb-106">Selektor wstawek kodu, znajduje się się w **systemu operacyjnego Windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="12eeb-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="12eeb-107">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="12eeb-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12eeb-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="12eeb-108">Compiling the Code</span></span>  
 <span data-ttu-id="12eeb-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="12eeb-109">This example requires:</span></span>  
  
-   <span data-ttu-id="12eeb-110">Odwołanie projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="12eeb-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="12eeb-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="12eeb-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="12eeb-112">Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="12eeb-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="12eeb-113">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="12eeb-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="12eeb-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="12eeb-114">Robust Programming</span></span>  
 <span data-ttu-id="12eeb-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest komputerem lokalnym domyślnie.</span><span class="sxs-lookup"><span data-stu-id="12eeb-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="12eeb-116">Aby odwołać usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwości nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="12eeb-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="12eeb-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="12eeb-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="12eeb-118">Nie można wstrzymać usługi.</span><span class="sxs-lookup"><span data-stu-id="12eeb-118">The service cannot be paused.</span></span> <span data-ttu-id="12eeb-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="12eeb-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="12eeb-120">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="12eeb-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="12eeb-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="12eeb-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="12eeb-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="12eeb-122">.NET Framework Security</span></span>  
 <span data-ttu-id="12eeb-123">Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> można ustawić uprawnień <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="12eeb-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="12eeb-124">Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> można ustawić uprawnień <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="12eeb-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12eeb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12eeb-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="12eeb-126">Instrukcje: kontynuowanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12eeb-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
