---
title: Przegląd zabezpieczeń automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 70d24c3dcc531abcec6d4dce75b5f0b31757e0c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448768"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="418dd-102">Przegląd zabezpieczeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="418dd-102">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="418dd-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="418dd-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="418dd-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="418dd-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="418dd-105">W tym omówieniu opisano model zabezpieczeń [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="418dd-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="418dd-106">Kontrola konta użytkownika</span><span class="sxs-lookup"><span data-stu-id="418dd-106">User Account Control</span></span>

<span data-ttu-id="418dd-107">Bezpieczeństwo jest głównym fokusem systemu Windows Vista i wśród innowacji jest możliwość, aby użytkownicy mogli uruchamiać jako użytkownicy ze standardem (nie będącymi administratorami) bez konieczności blokowania uruchamiania aplikacji i usług, które wymagają wyższego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="418dd-107">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="418dd-108">W systemie Windows Vista większość aplikacji jest dostarczana z tokenem standardowym lub administracyjnym.</span><span class="sxs-lookup"><span data-stu-id="418dd-108">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="418dd-109">Jeśli aplikacja nie może być zidentyfikowana jako aplikacja administracyjna, domyślnie jest uruchamiana jako aplikacja standardowa.</span><span class="sxs-lookup"><span data-stu-id="418dd-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="418dd-110">Aby można było uruchomić aplikację zidentyfikowaną jako administracyjna, system Windows Vista monituje użytkownika o zgodę na uruchomienie aplikacji jako podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="418dd-110">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="418dd-111">Monit o zgodę jest domyślnie wyświetlany, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ Administratorzy są uruchamiani jako użytkownicy standardowi do momentu, gdy aplikacja lub składnik systemowy, który wymaga poświadczeń administracyjnych, żąda uprawnień do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="418dd-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="418dd-112">Zadania wymagające wyższych uprawnień</span><span class="sxs-lookup"><span data-stu-id="418dd-112">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="418dd-113">Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych, w systemie Windows Vista zostanie wyświetlone okno dialogowe z prośbą o zgodę na kontynuowanie przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="418dd-113">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="418dd-114">To okno dialogowe jest chronione przed procesami komunikacji, dzięki czemu złośliwe oprogramowanie nie może symulować danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="418dd-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="418dd-115">Podobnie nie można uzyskać dostępu do ekranu logowania pulpitu przez inne procesy.</span><span class="sxs-lookup"><span data-stu-id="418dd-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="418dd-116">Klienci automatyzacji interfejsu użytkownika muszą komunikować się z innymi procesami, ale niektóre z nich są prawdopodobnie uruchomione na wyższym poziomie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="418dd-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="418dd-117">Klienci mogą również potrzebować dostępu do okien dialogowych systemu, które nie są zwykle widoczne dla innych procesów.</span><span class="sxs-lookup"><span data-stu-id="418dd-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="418dd-118">W związku z tym klienci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] muszą być Zaufani przez system i muszą mieć specjalne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="418dd-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="418dd-119">Aby mieć zaufanie do komunikacji z aplikacjami działającymi na wyższym poziomie uprawnień, aplikacje muszą być podpisane.</span><span class="sxs-lookup"><span data-stu-id="418dd-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="418dd-120">Pliki manifestu</span><span class="sxs-lookup"><span data-stu-id="418dd-120">Manifest Files</span></span>

<span data-ttu-id="418dd-121">Aby uzyskać dostęp do interfejsu użytkownika chronionego systemu, aplikacje muszą być skompilowane przy użyciu pliku manifestu, który zawiera atrybut `uiAccess` w tagu `requestedExecutionLevel`, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="418dd-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

<span data-ttu-id="418dd-122">Wartość atrybutu `level` w tym kodzie jest tylko przykładem.</span><span class="sxs-lookup"><span data-stu-id="418dd-122">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="418dd-123">`uiAccess` domyślnie ma wartość "false"; oznacza to, że jeśli atrybut zostanie pominięty lub nie ma manifestu dla zestawu, aplikacja nie będzie w stanie uzyskać dostępu do chronionego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="418dd-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
