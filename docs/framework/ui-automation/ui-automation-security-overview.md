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
---
# <a name="ui-automation-security-overview"></a>Przegląd zabezpieczeń automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis model zabezpieczeń [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Kontrola konta użytkownika  
 Zabezpieczenia są w centrum uwagi [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i między innowacji jest możliwości do uruchamiania jako standardowa użytkowników (z systemem innym niż administrator) bez zawsze blokowany jest dostęp do uruchamiania aplikacji i usług, które wymagają wyższych uprawnień przez użytkowników.  
  
 W [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], większość aplikacji są dostarczane przy użyciu standardowej lub token administracyjnych. Jeśli nie można zidentyfikować aplikacji jako aplikacji administracyjnej, domyślnie jest uruchamiane jako standardowe aplikacji. Można uruchomić przed aplikacja zidentyfikowana jako administracyjne, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] monituje użytkownika o zgodę uruchomić aplikację jako podwyższonego poziomu uprawnień. Monit o zgodę jest wyświetlany domyślnie, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ administratorzy Uruchom jako użytkowników standardowych, dopóki aplikacja lub składnik systemu, który wymaga poświadczeń administracyjnych żąda uprawnienia do uruchamiania.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Zadań wymagających wyższej uprawnień  
 Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] Wyświetla okno dialogowe z pytaniem użytkownika o zgodę kontynuować. To okno dialogowe jest chroniony z komunikacji między procesami tak, aby złośliwego oprogramowania nie można symulować danych wejściowych użytkownika. Podobnie ekran logowania pulpitu nie są zwykle dostępne przez inne procesy.  
  
 Klienci automatyzacji interfejsu użytkownika musi komunikować się z innymi procesami, niektóre z nich, być może jest uruchomiony na wyższym poziomie uprawnień. Klienci mogą również wymagany dostęp do okna dialogowe systemu, które nie są zwykle widoczne dla innych procesów. W związku z tym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientów musi być uważany za zaufany przez system i musi działać z specjalne uprawnienia.  
  
 Jako zaufane do komunikowania się z aplikacji działających na wyższym poziomie uprawnień, muszą być podpisane aplikacje.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Pliki manifestu  
 Aby uzyskać dostęp do chronionego systemu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikacje muszą zostać skompilowane z plikiem manifestu, który zawiera atrybut specjalne w pliku manifestu. To `uiAccess` atrybut jest umieszczany w `requestedExecutionLevel` tagu w następujący sposób:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Wartość `level` atrybut ten kod jest tylko przykładem.  
  
 `UIAccess` jest domyślnie; "false" oznacza to, jeśli ten atrybut zostanie pominięty lub brak nie manifestu zestawu, aplikacja nie będzie mógł uzyskać dostęp do chronionych [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpieczeń, podpisywanie aplikacji i tworzenie manifesty, zobacz "Najlepsze rozwiązania i wskazówki dla aplikacji w co najmniej uprzywilejowane środowiska deweloperskiego" na [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
