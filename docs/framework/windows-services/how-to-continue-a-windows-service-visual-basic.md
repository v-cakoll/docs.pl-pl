---
title: 'Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)'
description: Przeczytaj, jak używać składnika ServiceController do kontynuowania usługi systemu Windows (na przykład usługi administratora usług IIS) na komputerze lokalnym z Visual Basic.
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
ms.openlocfilehash: 2a04e330ea7dc37552053b2a7915909c011727f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925790"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="4b32c-103">Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b32c-103">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="4b32c-104">Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do kontynuowania usługi administratora usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4b32c-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b32c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b32c-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="4b32c-106">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4b32c-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4b32c-107">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4b32c-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="4b32c-108">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4b32c-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b32c-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b32c-109">Compiling the Code</span></span>  
 <span data-ttu-id="4b32c-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4b32c-110">This example requires:</span></span>  
  
- <span data-ttu-id="4b32c-111">Odwołanie do projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="4b32c-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="4b32c-112">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4b32c-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="4b32c-113">Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b32c-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="4b32c-114">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4b32c-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4b32c-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="4b32c-115">Robust Programming</span></span>  
 <span data-ttu-id="4b32c-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4b32c-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="4b32c-117">Aby odwoływać się do usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="4b32c-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="4b32c-118">Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody w usłudze do momentu, gdy kontroler usług nie ma stanu <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .</span><span class="sxs-lookup"><span data-stu-id="4b32c-118">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="4b32c-119">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="4b32c-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4b32c-120">Nie można wznowić usługi.</span><span class="sxs-lookup"><span data-stu-id="4b32c-120">The service cannot be resumed.</span></span> <span data-ttu-id="4b32c-121">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="4b32c-121">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="4b32c-122">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="4b32c-122">An error occurred when accessing a system API.</span></span> <span data-ttu-id="4b32c-123">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="4b32c-123">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4b32c-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4b32c-124">.NET Framework Security</span></span>  
 <span data-ttu-id="4b32c-125">Kontrola usług na komputerze może być ograniczona przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> wyliczenia, aby ustawić uprawnienia w <xref:System.ServiceProcess.ServiceControllerPermission> klasie.</span><span class="sxs-lookup"><span data-stu-id="4b32c-125">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="4b32c-126">Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczenia w celu ustawienia uprawnień w <xref:System.Security.Permissions.SecurityPermission> klasie.</span><span class="sxs-lookup"><span data-stu-id="4b32c-126">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b32c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b32c-127">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="4b32c-128">Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b32c-128">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
