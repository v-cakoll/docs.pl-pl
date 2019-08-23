---
title: 'Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 20bc177ccf2646f79994553803568531233ea5c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935480"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="87757-102">Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87757-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="87757-103">Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do wstrzymania usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="87757-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87757-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="87757-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="87757-105">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="87757-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="87757-106">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="87757-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="87757-107">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="87757-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87757-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="87757-108">Compiling the Code</span></span>  
 <span data-ttu-id="87757-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="87757-109">This example requires:</span></span>  
  
- <span data-ttu-id="87757-110">Odwołanie do projektu do System. ServiceProcess. dll.</span><span class="sxs-lookup"><span data-stu-id="87757-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="87757-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="87757-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="87757-112">`Imports` Dodaj instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="87757-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="87757-113">Aby uzyskać więcej informacji, zobacz Imports — [instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="87757-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="87757-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="87757-114">Robust Programming</span></span>  
 <span data-ttu-id="87757-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość<xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="87757-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="87757-116">Aby odwoływać się do usług systemu Windows na innym <xref:System.ServiceProcess.ServiceController.MachineName%2A> komputerze, należy zmienić właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="87757-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="87757-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="87757-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="87757-118">Nie można wstrzymać usługi.</span><span class="sxs-lookup"><span data-stu-id="87757-118">The service cannot be paused.</span></span> <span data-ttu-id="87757-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="87757-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="87757-120">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="87757-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="87757-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="87757-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="87757-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="87757-122">.NET Framework Security</span></span>  
 <span data-ttu-id="87757-123">Kontrolowanie usług na komputerze może być ograniczone przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> programu w celu ustawienia uprawnień <xref:System.ServiceProcess.ServiceControllerPermission>w.</span><span class="sxs-lookup"><span data-stu-id="87757-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="87757-124">Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> do ustawiania uprawnień <xref:System.Security.Permissions.SecurityPermission>w.</span><span class="sxs-lookup"><span data-stu-id="87757-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87757-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87757-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="87757-126">Instrukcje: Kontynuuj działanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87757-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
