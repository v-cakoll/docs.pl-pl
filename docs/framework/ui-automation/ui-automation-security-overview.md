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
# <a name="ui-automation-security-overview"></a>Przegląd zabezpieczeń automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu opisano model zabezpieczeń [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Kontrola konta użytkownika  
 Zabezpieczenia są w centrum uwagi [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i między innowacji polega na tym użytkownikom na uruchamianie jako standardowych użytkowników (inni niż administrator) bez zawsze blokowane uruchamianie aplikacji i usług, które wymagają wyższych uprawnień.  
  
 W [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], większość aplikacji są dostarczane za pomocą standardowej lub tokenu administracyjne. Jeśli nie można zidentyfikować aplikacji jako aplikacji administracyjnej, domyślnie zostanie uruchomiony jako standardowa aplikacja. Zanim aplikacja zidentyfikowana jako administracyjne można uruchamiać, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] monituje użytkownika o zgodę uruchomić aplikację jako podwyższonego poziomu uprawnień. Monit o wyrażenie zgody jest wyświetlany domyślnie, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ administratorzy uruchamiać jako standardowych użytkowników, dopóki aplikacja lub składnik systemu, który wymaga poświadczeń administracyjnych żąda uprawnienia do uruchomienia.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Zadań wymagających wyższymi uprawnieniami  
 Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] przedstawia okno dialogowe z monitem o wyrażenie zgody kontynuować. To okno dialogowe pozostaje chroniony i z komunikacji między procesami, złośliwe oprogramowanie, nie można symulować dane wejściowe użytkownika. Podobnie ekranie logowania pulpitu zwykle nie są dostępne przez inne procesy.  
  
 Klienci automatyzacji interfejsu użytkownika muszą komunikować się z innymi procesami, niektóre z nich może być uruchomiony na wyższym poziomie uprawnień. Klienci mogą również potrzebują dostępu do okna dialogowe systemu, które nie są zwykle widoczne dla innych procesów. W związku z tym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientów musi być zaufany przez system i musi działać z specjalne uprawnienia.  
  
 Jako zaufane do komunikowania się z aplikacjami uruchomionymi na wyższym poziomie uprawnień, muszą być podpisane aplikacje.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Pliki manifestu  
 Aby uzyskać dostęp do chronionych systemu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikacje muszą zostać skompilowane przy użyciu pliku manifestu, który zawiera atrybut specjalne w pliku manifestu. To `uiAccess` atrybut jest umieszczany w `requestedExecutionLevel` tagu w następujący sposób:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Wartość `level` atrybut, w tym kodzie jest tylko przykładem.  
  
 `UIAccess` Domyślnie; "false" oznacza to, jeśli ten atrybut zostanie pominięty lub jeśli nie manifestu zestawu, aplikacja nie będzie można uzyskać dostęp do chronionych [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpieczenia, na podpisywanie aplikacji i na temat tworzenia zestawu manifestów, zobacz "Najlepsze praktyki i wytyczne dla aplikacji w co najmniej uprzywilejowane środowiska deweloperskiego" na [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
