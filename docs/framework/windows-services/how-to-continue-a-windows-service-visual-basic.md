---
title: 'Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)'
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
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053635"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="8053e-102">Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8053e-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="8053e-103">Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do kontynuowania usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8053e-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8053e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8053e-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="8053e-105">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8053e-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8053e-106">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="8053e-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="8053e-107">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8053e-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8053e-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8053e-108">Compiling the Code</span></span>  
 <span data-ttu-id="8053e-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8053e-109">This example requires:</span></span>  
  
- <span data-ttu-id="8053e-110">Odwołanie do projektu do System. ServiceProcess. dll.</span><span class="sxs-lookup"><span data-stu-id="8053e-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="8053e-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8053e-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="8053e-112">`Imports` Dodaj instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8053e-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="8053e-113">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="8053e-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8053e-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8053e-114">Robust Programming</span></span>  
 <span data-ttu-id="8053e-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość<xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8053e-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="8053e-116">Aby odwoływać się do usług systemu Windows na innym <xref:System.ServiceProcess.ServiceController.MachineName%2A> komputerze, należy zmienić właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="8053e-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="8053e-117">Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody w usłudze do momentu, gdy kontroler usług nie <xref:System.ServiceProcess.ServiceControllerStatus.Paused>ma stanu.</span><span class="sxs-lookup"><span data-stu-id="8053e-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="8053e-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="8053e-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8053e-119">Nie można wznowić usługi.</span><span class="sxs-lookup"><span data-stu-id="8053e-119">The service cannot be resumed.</span></span> <span data-ttu-id="8053e-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="8053e-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="8053e-121">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="8053e-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="8053e-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="8053e-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8053e-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="8053e-123">.NET Framework Security</span></span>  
 <span data-ttu-id="8053e-124">Kontrola usług na komputerze może być ograniczona przy użyciu wyliczenia, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> aby ustawić uprawnienia <xref:System.ServiceProcess.ServiceControllerPermission> w klasie.</span><span class="sxs-lookup"><span data-stu-id="8053e-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="8053e-125">Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczenia w celu ustawienia uprawnień <xref:System.Security.Permissions.SecurityPermission> w klasie.</span><span class="sxs-lookup"><span data-stu-id="8053e-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8053e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8053e-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="8053e-127">Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8053e-127">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
