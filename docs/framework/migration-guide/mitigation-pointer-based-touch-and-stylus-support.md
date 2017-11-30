---
title: "Środki zaradcze: Na podstawie wskaźnika Touch i pomocy technicznej pióro"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: "2"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 053ff4c5fba7b4f2b5a4c29a35c954e888cb095a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Środki zaradcze: Na podstawie wskaźnika Touch i pomocy technicznej pióro

Aplikacje WPF, docelowa .NET Framework 4.7, które są uruchomione w systemie Windows począwszy od systemu Windows 10 twórców Update można włączyć opcjonalny `WM_POINTER`— na podstawie stosu touch/pióro WPF.

## <a name="impact"></a>Wpływ

Deweloperzy, którzy jawnie nie należy włączać obsługi opartej na wskaźnik touch/pióro powinny być widoczne nie zmiany w zachowaniu touch/pióro WPF.

Oto obecnie znane problemy z opcjonalnym `WM_POINTER`— na podstawie touch/pióro stosu:

- Brak obsługi pisma odręcznego w czasie rzeczywistym.

   Gdy wtyczek pisma odręcznego i Pióro nadal działać, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.

- Zachowania zmian z powodu zmian w ramach podwyższenia poziomu z touch/pióro zdarzenia do zdarzenia myszy.

  - Manipulowanie może zachowywać się inaczej.

  - Przeciągnij i upuść nie zostanie wyświetlone odpowiednie opinię dotyczącą wprowadzania dotykowego. (Nie dotyczy to wprowadzania danych piórem.)

  - Nie można zainicjować przeciągnij i upuść zdarzeń touch/pióra.

      To potencjalnie zawieszenie aplikacji, dopóki nie zostanie wykryty wejście myszy. Zamiast tego deweloperzy należy zainicjować przeciągnij i upuść z zdarzeń myszy.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Zgody na korzystanie z pomocy technicznej na podstawie WM_POINTER touch/pióra

Deweloperów, którzy chcą włączyć ten stos można dodać następujące do pliku app.config ich aplikacji:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Usunięcie tego wpisu lub ustawienie jej wartość `false` wyłącza to opcjonalne stosu.

## <a name="see-also"></a>Zobacz także

[Zmiany w przekierowywaniu w programie .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
