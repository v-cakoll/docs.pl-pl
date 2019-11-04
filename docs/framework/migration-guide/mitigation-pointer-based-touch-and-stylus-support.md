---
title: 'Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 6b3e8068be2f5ed82c483b760fe100ea0a751588
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457855"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach

Aplikacje WPF, które są przeznaczone dla .NET Framework 4,7 i działają w systemach Windows, począwszy od aktualizacji systemu Windows 10 Creators, mogą włączyć opcjonalny stos dotykowy/pióra WPF oparty na `WM_POINTER`.

## <a name="impact"></a>Wpływ

Deweloperzy, którzy nie umożliwiają jawnie włączania obsługi dotykowej opartej na wskaźnikach, nie powinni zmieniać zachowań dotykowych i pióra WPF.

Poniżej znajdują się obecnie znane problemy z opcjonalnym stosem dotykowy/piórem na `WM_POINTER`:

- Brak obsługi pisma odręcznego w czasie rzeczywistym.

   Podczas gdy wtyczki pisma odręcznego i pióra nadal działają, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.

- Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy.

  - Manipulowanie może zachowywać się inaczej.

  - Wartość przeciągnij/upuść nie będzie zawierać odpowiedniej opinii na temat wprowadzania dotykowego. (Nie ma to wpływu na wprowadzanie piórem).

  - Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra.

      Może to spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryta mysz. Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Możliwość skorzystania z obsługi dotyku i pióra na WM_POINTER

Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku App. config aplikacji:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Usunięcie tego wpisu lub ustawienie jego wartości `false` powoduje wyłączenie tego opcjonalnego stosu.

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
