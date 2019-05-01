---
title: 'Środki zaradcze: Oparte na wskaźnikach Dotyk i pomocy technicznej pióra'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d750087cc000ad31a24d91411c0885a75d59e74f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871349"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Środki zaradcze: Oparte na wskaźnikach Dotyk i pomocy technicznej pióra

Aplikacje WPF, docelowych programu .NET Framework 4.7, które są uruchomione w systemach Windows, począwszy od systemu Windows 10 Creators Update można włączyć opcjonalnie `WM_POINTER`— na podstawie stosu dotyk/pióro WPF.

## <a name="impact"></a>Wpływ

Deweloperzy, którzy nie jawnie włączyć obsługę dotyku/pióro oparte na wskaźnikach powinien zostać wyświetlony bez zmian w zachowaniu dotyk/pióro WPF.

Poniżej przedstawiono obecnie znane problemy z opcjonalnym `WM_POINTER`— na podstawie dotyk/pióro stosu:

- Brak obsługi pisma odręcznego w czasie rzeczywistym.

   Gdy wtyczek pisma odręcznego i Pióro nadal działać, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do pogorszenia wydajności.

- Zachowania zmian z powodu zmian w ramach podwyższenia poziomu dotyk/pióro zdarzeń do zdarzenia myszy.

  - Manipulowanie może zachowywać się inaczej.

  - Przeciągania i upuszczania nie będzie widoczna odpowiednią opinię dotyczącą wprowadzania dotykowego. (Nie wpływa to wejście pióra.)

  - Już nie można zainicjować przeciągania i upuszczania zdarzeń dotyk/pióra.

      To potencjalnie zawieszanie aplikacji, dopóki nie zostanie wykryte wejście myszy. Zamiast tego deweloperów należy zainicjować przeciągnij i upuść z zdarzeń myszy.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Zgody na korzystanie z pomocy technicznej na podstawie WM_POINTER dotyk/pióra

Deweloperzy, którzy chcą włączyć ten stos może Dodaj następujący element do pliku app.config swoich aplikacji:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Usunięcie tego wpisu lub ustawiając jej wartość na `false` wyłącza ten stos opcjonalne.

## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu w programie .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
