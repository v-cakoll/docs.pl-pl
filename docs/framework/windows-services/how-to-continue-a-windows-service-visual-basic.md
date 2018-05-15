---
title: 'Porady: kontynuowanie usług systemu Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
manager: douge
ms.openlocfilehash: 15ef15e0afe43d56db0972a686cd093e22c672dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="f4b90-102">Porady: kontynuowanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4b90-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="f4b90-103">W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnik, aby kontynuować korzystanie z usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f4b90-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4b90-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4b90-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="f4b90-105">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f4b90-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f4b90-106">Selektor wstawek kodu, znajduje się się w **systemu operacyjnego Windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="f4b90-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="f4b90-107">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f4b90-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4b90-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f4b90-108">Compiling the Code</span></span>  
 <span data-ttu-id="f4b90-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f4b90-109">This example requires:</span></span>  
  
-   <span data-ttu-id="f4b90-110">Odwołanie projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="f4b90-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="f4b90-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4b90-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="f4b90-112">Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f4b90-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="f4b90-113">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="f4b90-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f4b90-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f4b90-114">Robust Programming</span></span>  
 <span data-ttu-id="f4b90-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest komputerem lokalnym domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f4b90-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="f4b90-116">Aby odwołać usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwości nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="f4b90-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="f4b90-117">Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody dla usługi, dopóki nie zostanie stan kontrolera usługi <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="f4b90-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="f4b90-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="f4b90-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f4b90-119">Nie można wznowić usługi.</span><span class="sxs-lookup"><span data-stu-id="f4b90-119">The service cannot be resumed.</span></span> <span data-ttu-id="f4b90-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="f4b90-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="f4b90-121">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="f4b90-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="f4b90-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="f4b90-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f4b90-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f4b90-123">.NET Framework Security</span></span>  
 <span data-ttu-id="f4b90-124">Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> wyliczeniu, aby ustawić uprawnień w <xref:System.ServiceProcess.ServiceControllerPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="f4b90-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="f4b90-125">Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczeniu, aby ustawić uprawnień w <xref:System.Security.Permissions.SecurityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="f4b90-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b90-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4b90-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="f4b90-127">Instrukcje: wstrzymywanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4b90-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
