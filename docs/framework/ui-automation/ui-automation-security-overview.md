---
title: Przegląd zabezpieczeń automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 8b798aef528cccdedb1fcaa53c1782632037600d
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133784"
---
# <a name="ui-automation-security-overview"></a>Przegląd zabezpieczeń automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.

[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] W tym omówieniu opisano model zabezpieczeń programu w [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]programie.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>Kontrola konta użytkownika

Bezpieczeństwo jest głównym fokusem [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] i wśród innowacji jest możliwość, aby użytkownicy mogli uruchamiać jako użytkownicy standardowi (nie będący administratorami) bez konieczności blokowania uruchamiania aplikacji i usług, które wymagają wyższych uprawnień.

W [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]programie większość aplikacji jest dostarczana z tokenem standardowym lub administracyjnym. Jeśli aplikacja nie może być zidentyfikowana jako aplikacja administracyjna, domyślnie jest uruchamiana jako aplikacja standardowa. Aby można było uruchomić aplikację zidentyfikowaną jako administracyjną [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] , program monituje użytkownika o zgodę na uruchomienie aplikacji jako podniesienia uprawnień. Monit o zgodę jest domyślnie wyświetlany, nawet jeśli użytkownik jest członkiem lokalnej grupy administratorów, ponieważ Administratorzy są uruchamiani jako użytkownicy standardowi do momentu, gdy aplikacja lub składnik systemowy, który wymaga poświadczeń administracyjnych, żąda uprawnień do uruchomienia.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Zadania wymagające wyższych uprawnień

Gdy użytkownik próbuje wykonać zadanie, które wymaga uprawnień administracyjnych, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] wyświetli okno dialogowe z prośbą o zgodę na kontynuowanie przez użytkownika. To okno dialogowe jest chronione przed procesami komunikacji, dzięki czemu złośliwe oprogramowanie nie może symulować danych wejściowych użytkownika. Podobnie nie można uzyskać dostępu do ekranu logowania pulpitu przez inne procesy.

Klienci automatyzacji interfejsu użytkownika muszą komunikować się z innymi procesami, ale niektóre z nich są prawdopodobnie uruchomione na wyższym poziomie uprawnień. Klienci mogą również potrzebować dostępu do okien dialogowych systemu, które nie są zwykle widoczne dla innych procesów. W związku z tym kliencimusząbyćZaufaniprzezsystemimusząmiećspecjalneuprawnienia.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

Aby mieć zaufanie do komunikacji z aplikacjami działającymi na wyższym poziomie uprawnień, aplikacje muszą być podpisane.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Pliki manifestu

Aby uzyskać dostęp do interfejsu użytkownika chronionego systemu, aplikacje muszą być skompilowane przy użyciu pliku manifestu, `uiAccess` który zawiera atrybut `requestedExecutionLevel` w tagu w następujący sposób:

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

Wartość `level` atrybutu w tym kodzie jest tylko przykładem.

`uiAccess`Domyślnie ma wartość "false"; oznacza to, że jeśli atrybut zostanie pominięty lub nie ma manifestu dla zestawu, aplikacja nie będzie w stanie uzyskać dostępu do chronionego interfejsu użytkownika.
