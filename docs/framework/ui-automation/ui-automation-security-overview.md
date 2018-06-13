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
ms.openlocfilehash: 293cee72e80e88215fccb3902eb88963814cb2ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400201"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="25432-102">Przegląd zabezpieczeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="25432-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="25432-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="25432-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="25432-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="25432-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="25432-105">Ten przegląd zawiera opis model zabezpieczeń [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25432-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="25432-106">Kontrola konta użytkownika</span><span class="sxs-lookup"><span data-stu-id="25432-106">User Account Control</span></span>  
 <span data-ttu-id="25432-107">Zabezpieczenia są w centrum uwagi [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i między innowacji jest możliwości do uruchamiania jako standardowa użytkowników (z systemem innym niż administrator) bez zawsze blokowany jest dostęp do uruchamiania aplikacji i usług, które wymagają wyższych uprawnień przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="25432-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="25432-108">W [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], większość aplikacji są dostarczane przy użyciu standardowej lub token administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="25432-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="25432-109">Jeśli nie można zidentyfikować aplikacji jako aplikacji administracyjnej, domyślnie jest uruchamiane jako standardowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="25432-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="25432-110">Można uruchomić przed aplikacja zidentyfikowana jako administracyjne, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] monituje użytkownika o zgodę uruchomić aplikację jako podwyższonego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="25432-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="25432-111">Monit o zgodę jest wyświetlany domyślnie, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ administratorzy Uruchom jako użytkowników standardowych, dopóki aplikacja lub składnik systemu, który wymaga poświadczeń administracyjnych żąda uprawnienia do uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="25432-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="25432-112">Zadań wymagających wyższej uprawnień</span><span class="sxs-lookup"><span data-stu-id="25432-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="25432-113">Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] Wyświetla okno dialogowe z pytaniem użytkownika o zgodę kontynuować.</span><span class="sxs-lookup"><span data-stu-id="25432-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="25432-114">To okno dialogowe jest chroniony z komunikacji między procesami tak, aby złośliwego oprogramowania nie można symulować danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25432-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="25432-115">Podobnie ekran logowania pulpitu nie są zwykle dostępne przez inne procesy.</span><span class="sxs-lookup"><span data-stu-id="25432-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="25432-116">Klienci automatyzacji interfejsu użytkownika musi komunikować się z innymi procesami, niektóre z nich, być może jest uruchomiony na wyższym poziomie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="25432-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="25432-117">Klienci mogą również wymagany dostęp do okna dialogowe systemu, które nie są zwykle widoczne dla innych procesów.</span><span class="sxs-lookup"><span data-stu-id="25432-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="25432-118">W związku z tym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientów musi być uważany za zaufany przez system i musi działać z specjalne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="25432-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="25432-119">Jako zaufane do komunikowania się z aplikacji działających na wyższym poziomie uprawnień, muszą być podpisane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="25432-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="25432-120">Pliki manifestu</span><span class="sxs-lookup"><span data-stu-id="25432-120">Manifest Files</span></span>  
 <span data-ttu-id="25432-121">Aby uzyskać dostęp do chronionego systemu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikacje muszą zostać skompilowane z plikiem manifestu, który zawiera atrybut specjalne w pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="25432-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="25432-122">To `uiAccess` atrybut jest umieszczany w `requestedExecutionLevel` tagu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="25432-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="25432-123">Wartość `level` atrybut ten kod jest tylko przykładem.</span><span class="sxs-lookup"><span data-stu-id="25432-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="25432-124">`UIAccess` jest domyślnie; "false" oznacza to, jeśli ten atrybut zostanie pominięty lub brak nie manifestu zestawu, aplikacja nie będzie mógł uzyskać dostęp do chronionych [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25432-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="25432-125">Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpieczeń, podpisywanie aplikacji i tworzenie manifesty, zobacz "Najlepsze rozwiązania i wskazówki dla aplikacji w co najmniej uprzywilejowane środowiska deweloperskiego" na [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span><span class="sxs-lookup"><span data-stu-id="25432-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
