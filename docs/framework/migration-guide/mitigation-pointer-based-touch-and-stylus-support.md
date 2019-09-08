---
title: Środki zaradcze Obsługa dotykowa i pióra na podstawie wskaźnika
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67e41450ed69d73a4b27b0aa37974ae01be69687
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779238"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Środki zaradcze Obsługa dotykowa i pióra na podstawie wskaźnika

Aplikacje WPF, które są przeznaczone dla .NET Framework 4,7 i działają w systemach Windows, począwszy od aktualizacji systemu Windows 10 Creators `WM_POINTER`, mogą umożliwić opcjonalny stos dotykowy/pióra WPF.

## <a name="impact"></a>Wpływ

Deweloperzy, którzy nie umożliwiają jawnie włączania obsługi dotykowej opartej na wskaźnikach, nie powinni zmieniać zachowań dotykowych i pióra WPF.

Poniżej przedstawiono bieżące znane problemy z opcjonalnym `WM_POINTER`stosem dotyk/piórem:

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

Usunięcie tego wpisu lub ustawienie jego wartości powoduje `false` wyłączenie tego opcjonalnego stosu.

## <a name="see-also"></a>Zobacz także

- [Przekierowywanie zmian w .NET Framework 4,7](retargeting-changes-in-the-net-framework-4-7.md)
