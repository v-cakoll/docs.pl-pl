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
ms.openlocfilehash: 8a75c6a03f130e0a141107c81c946fc6a33b9f6c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592541"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="6b735-102">Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b735-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="6b735-103">W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnika, aby wstrzymać Administrator usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6b735-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b735-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b735-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="6b735-105">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6b735-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6b735-106">W selektorze fragmentów kodu, znajduje się w **systemu operacyjnego Windows > usług Windows**.</span><span class="sxs-lookup"><span data-stu-id="6b735-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="6b735-107">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="6b735-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b735-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6b735-108">Compiling the Code</span></span>  
 <span data-ttu-id="6b735-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6b735-109">This example requires:</span></span>  
  
- <span data-ttu-id="6b735-110">Odwołania projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="6b735-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="6b735-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6b735-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="6b735-112">Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6b735-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="6b735-113">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="6b735-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6b735-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="6b735-114">Robust Programming</span></span>  
 <span data-ttu-id="6b735-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasa jest na komputerze lokalnym domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b735-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="6b735-116">Aby odwoływać się do usługi Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="6b735-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="6b735-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6b735-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6b735-118">Nie można wstrzymać usługę.</span><span class="sxs-lookup"><span data-stu-id="6b735-118">The service cannot be paused.</span></span> <span data-ttu-id="6b735-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="6b735-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="6b735-120">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="6b735-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="6b735-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="6b735-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6b735-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6b735-122">.NET Framework Security</span></span>  
 <span data-ttu-id="6b735-123">Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> ustawiania uprawnień w <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="6b735-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="6b735-124">Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> ustawiania uprawnień w <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="6b735-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b735-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b735-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="6b735-126">Instrukcje: Kontynuowanie usług Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b735-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
