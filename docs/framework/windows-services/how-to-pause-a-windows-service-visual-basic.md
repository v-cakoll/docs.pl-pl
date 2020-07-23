---
title: 'Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)'
description: Przeczytaj, jak używać składnika ServiceController do wstrzymania usługi systemu Windows (na przykład usługi administratora usług IIS) na komputerze lokalnym z Visual Basic.
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
ms.openlocfilehash: 628cc2e896f7f8a289e52674b721c4aef605854c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925569"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="a4ac6-103">Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ac6-103">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="a4ac6-104">Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do wstrzymania usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4ac6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4ac6-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="a4ac6-106">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a4ac6-107">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="a4ac6-108">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a4ac6-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4ac6-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a4ac6-109">Compiling the Code</span></span>  
 <span data-ttu-id="a4ac6-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a4ac6-110">This example requires:</span></span>  
  
- <span data-ttu-id="a4ac6-111">Odwołanie do projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="a4ac6-112">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="a4ac6-113">Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a4ac6-114">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a4ac6-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a4ac6-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a4ac6-115">Robust Programming</span></span>  
 <span data-ttu-id="a4ac6-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="a4ac6-117">Aby odwoływać się do usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="a4ac6-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a4ac6-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a4ac6-119">Nie można wstrzymać usługi.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-119">The service cannot be paused.</span></span> <span data-ttu-id="a4ac6-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="a4ac6-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="a4ac6-121">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="a4ac6-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="a4ac6-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="a4ac6-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a4ac6-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4ac6-123">.NET Framework Security</span></span>  
 <span data-ttu-id="a4ac6-124">Kontrolowanie usług na komputerze może być ograniczone przy użyciu programu w <xref:System.ServiceProcess.ServiceControllerPermissionAccess> celu ustawienia uprawnień w <xref:System.ServiceProcess.ServiceControllerPermission> .</span><span class="sxs-lookup"><span data-stu-id="a4ac6-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="a4ac6-125">Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> do ustawiania uprawnień w <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="a4ac6-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ac6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4ac6-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="a4ac6-127">Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ac6-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
