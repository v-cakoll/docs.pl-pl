---
title: 'Instrukcje: Kontynuowanie usług Windows (Visual Basic)'
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
ms.openlocfilehash: 86c2414fd6ad9c32a37339c553ec80c98426f78a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612713"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="a7298-102">Instrukcje: Kontynuowanie usług Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7298-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="a7298-103">W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnika, aby kontynuować Administrator usług IIS na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a7298-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7298-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7298-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="a7298-105">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a7298-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a7298-106">W selektorze fragmentów kodu, znajduje się w **systemu operacyjnego Windows > usług Windows**.</span><span class="sxs-lookup"><span data-stu-id="a7298-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="a7298-107">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a7298-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7298-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a7298-108">Compiling the Code</span></span>  
 <span data-ttu-id="a7298-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a7298-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a7298-110">Odwołania projektu do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="a7298-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="a7298-111">Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a7298-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="a7298-112">Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a7298-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a7298-113">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a7298-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a7298-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a7298-114">Robust Programming</span></span>  
 <span data-ttu-id="a7298-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasa jest na komputerze lokalnym domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7298-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="a7298-116">Aby odwoływać się do usługi Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwość na nazwę tego komputera.</span><span class="sxs-lookup"><span data-stu-id="a7298-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="a7298-117">Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody dla usługi, dopóki nie zostanie stan kontrolera usługi <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="a7298-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="a7298-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a7298-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a7298-119">Nie można wznowić usługi.</span><span class="sxs-lookup"><span data-stu-id="a7298-119">The service cannot be resumed.</span></span> <span data-ttu-id="a7298-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="a7298-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="a7298-121">Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu.</span><span class="sxs-lookup"><span data-stu-id="a7298-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="a7298-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="a7298-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a7298-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7298-123">.NET Framework Security</span></span>  
 <span data-ttu-id="a7298-124">Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> wyliczeniu, aby ustawić uprawnienia w <xref:System.ServiceProcess.ServiceControllerPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7298-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="a7298-125">Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczeniu, aby ustawić uprawnienia w <xref:System.Security.Permissions.SecurityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7298-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7298-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7298-126">See also</span></span>
- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="a7298-127">Instrukcje: Wstrzymaj usługę Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7298-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
