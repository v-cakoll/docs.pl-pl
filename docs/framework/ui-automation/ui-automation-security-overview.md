---
title: Przegląd zabezpieczeń automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f55112c5eead082eae10aa50590b915f5049d5a6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855168"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="373f3-102">Przegląd zabezpieczeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="373f3-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="373f3-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="373f3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="373f3-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="373f3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="373f3-105">W tym omówieniu opisano model zabezpieczeń [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="373f3-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="373f3-106">Kontrola konta użytkownika</span><span class="sxs-lookup"><span data-stu-id="373f3-106">User Account Control</span></span>  
 <span data-ttu-id="373f3-107">Zabezpieczenia są w centrum uwagi [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i między innowacji polega na tym użytkownikom na uruchamianie jako standardowych użytkowników (inni niż administrator) bez zawsze blokowane uruchamianie aplikacji i usług, które wymagają wyższych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="373f3-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="373f3-108">W [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], większość aplikacji są dostarczane za pomocą standardowej lub tokenu administracyjne.</span><span class="sxs-lookup"><span data-stu-id="373f3-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="373f3-109">Jeśli nie można zidentyfikować aplikacji jako aplikacji administracyjnej, domyślnie zostanie uruchomiony jako standardowa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="373f3-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="373f3-110">Zanim aplikacja zidentyfikowana jako administracyjne można uruchamiać, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] monituje użytkownika o zgodę uruchomić aplikację jako podwyższonego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="373f3-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="373f3-111">Monit o wyrażenie zgody jest wyświetlany domyślnie, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ administratorzy uruchamiać jako standardowych użytkowników, dopóki aplikacja lub składnik systemu, który wymaga poświadczeń administracyjnych żąda uprawnienia do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="373f3-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="373f3-112">Zadań wymagających wyższymi uprawnieniami</span><span class="sxs-lookup"><span data-stu-id="373f3-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="373f3-113">Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] przedstawia okno dialogowe z monitem o wyrażenie zgody kontynuować.</span><span class="sxs-lookup"><span data-stu-id="373f3-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="373f3-114">To okno dialogowe pozostaje chroniony i z komunikacji między procesami, złośliwe oprogramowanie, nie można symulować dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="373f3-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="373f3-115">Podobnie ekranie logowania pulpitu zwykle nie są dostępne przez inne procesy.</span><span class="sxs-lookup"><span data-stu-id="373f3-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="373f3-116">Klienci automatyzacji interfejsu użytkownika muszą komunikować się z innymi procesami, niektóre z nich może być uruchomiony na wyższym poziomie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="373f3-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="373f3-117">Klienci mogą również potrzebują dostępu do okna dialogowe systemu, które nie są zwykle widoczne dla innych procesów.</span><span class="sxs-lookup"><span data-stu-id="373f3-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="373f3-118">W związku z tym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientów musi być zaufany przez system i musi działać z specjalne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="373f3-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="373f3-119">Jako zaufane do komunikowania się z aplikacjami uruchomionymi na wyższym poziomie uprawnień, muszą być podpisane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="373f3-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="373f3-120">Pliki manifestu</span><span class="sxs-lookup"><span data-stu-id="373f3-120">Manifest Files</span></span>  
 <span data-ttu-id="373f3-121">Aby uzyskać dostęp do chronionych systemu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikacje muszą zostać skompilowane przy użyciu pliku manifestu, który zawiera atrybut specjalne w pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="373f3-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="373f3-122">To `uiAccess` atrybut jest umieszczany w `requestedExecutionLevel` tagu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="373f3-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="373f3-123">Wartość `level` atrybut, w tym kodzie jest tylko przykładem.</span><span class="sxs-lookup"><span data-stu-id="373f3-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="373f3-124">`UIAccess` Domyślnie; "false" oznacza to, jeśli ten atrybut zostanie pominięty lub jeśli nie manifestu zestawu, aplikacja nie będzie można uzyskać dostęp do chronionych [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="373f3-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="373f3-125">Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpieczenia, na podpisywanie aplikacji i na temat tworzenia zestawu manifestów, zobacz "Najlepsze praktyki i wytyczne dla aplikacji w co najmniej uprzywilejowane środowiska deweloperskiego" na [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span><span class="sxs-lookup"><span data-stu-id="373f3-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
