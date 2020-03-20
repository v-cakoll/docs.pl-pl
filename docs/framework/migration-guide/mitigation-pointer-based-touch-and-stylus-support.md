---
title: 'Łagodzenie: Obsługa dotykowa i rysików oparta na wskaźnikach'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094478"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Łagodzenie: Obsługa dotykowa i rysików oparta na wskaźnikach

Aplikacje WPF, które są przeznaczone dla programu .NET Framework 4.7 i są `WM_POINTER`uruchomione w systemie Windows, począwszy od aktualizacji Windows 10 Creators Update, mogą włączyć opcjonalny stos WPF touch/pisak.

## <a name="impact"></a>Wpływ

Deweloperzy, którzy nie jawnie włączyć wskaźnik oparte na obsłudze touch/pisaka powinny zobaczyć żadnych zmian w WPF touch/pisak zachowanie.

Poniżej przedstawiono bieżące `WM_POINTER`znane problemy z opcjonalnym stosem dotykowym/pióra opartym na sobie:

- Brak obsługi pisma oduniającego w czasie rzeczywistym.

   Podczas gdy wtyczek pisma od pisma od pisma od pisma od pisającego i pisaka nadal działają, są one przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.

- Zmiany w zachowaniu spowodowane zmianami w promocji ze zdarzeń dotykowych/pisaka na zdarzenia myszy.

  - Manipulacja może zachowywać się inaczej.

  - Przeciąganie/upuszczanie nie będzie wyświetlane odpowiednie informacje zwrotne dla wprowadzania dotykowego. (Nie ma to wpływu na dane wejściowe pisaka).

  - Przeciągania/Upuszczania nie można już inicjować podczas zdarzeń dotykowych/pisaka.

      Może to potencjalnie spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryte dane wejściowe myszy. Zamiast tego deweloperzy powinni zainicjować przeciąganie i upuszczanie ze zdarzeń myszy.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Rezygnacja z obsługi WM_POINTER dotykowego/rysika

Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku *app.config* aplikacji.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Usunięcie tego wpisu lub `false` ustawienie jego wartości na wyłączenia tego opcjonalnego stosu.

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
