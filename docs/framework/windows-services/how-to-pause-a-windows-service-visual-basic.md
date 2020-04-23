---
title: 'Porady: wstrzymywanie usług systemu Windows (Visual Basic)'
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
ms.openlocfilehash: 166eda4a9348188fa6e5048fd3ce41645cde4816
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053596"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="7ba08-102">Porady: wstrzymywanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ba08-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="7ba08-103">Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do wstrzymania usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="7ba08-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ba08-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ba08-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="7ba08-105">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7ba08-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7ba08-106">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="7ba08-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="7ba08-107">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="7ba08-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ba08-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7ba08-108">Compiling the Code</span></span>  
 <span data-ttu-id="7ba08-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7ba08-109">This example requires:</span></span>  
  
- <span data-ttu-id="7ba08-110">Odwołanie do projektu do System. ServiceProcess. dll.</span><span class="sxs-lookup"><span data-stu-id="7ba08-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="7ba08-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7ba08-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="7ba08-112">Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ba08-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="7ba08-113">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="7ba08-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7ba08-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="7ba08-114">Robust Programming</span></span>  
 <span data-ttu-id="7ba08-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="7ba08-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="7ba08-116">Aby odwoływać się do usług systemu Windows na innym <xref:System.ServiceProcess.ServiceController.MachineName%2A> komputerze, należy zmienić właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="7ba08-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="7ba08-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="7ba08-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7ba08-118">Nie można wstrzymać usługi.</span><span class="sxs-lookup"><span data-stu-id="7ba08-118">The service cannot be paused.</span></span> <span data-ttu-id="7ba08-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="7ba08-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="7ba08-120">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="7ba08-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="7ba08-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="7ba08-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7ba08-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ba08-122">.NET Framework Security</span></span>  
 <span data-ttu-id="7ba08-123">Kontrolowanie usług na komputerze może być ograniczone przy użyciu programu w <xref:System.ServiceProcess.ServiceControllerPermissionAccess> celu ustawienia uprawnień w <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="7ba08-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="7ba08-124">Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> do ustawiania uprawnień w <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="7ba08-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba08-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ba08-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="7ba08-126">Instrukcje: kontynuowanie usług systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ba08-126">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
