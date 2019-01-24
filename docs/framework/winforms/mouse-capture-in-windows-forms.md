---
title: Przechwytywanie myszy w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: ca16d2fa2339f8d9110bb748a687f90e093598fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690335"
---
# <a name="mouse-capture-in-windows-forms"></a>Przechwytywanie myszy w formularzach systemu Windows
*Przechwytywanie myszy* odwołuje się do polecenia myszy wszystkich danych wejściowych podczas kontrolki. Po przechwyceniu myszy kontrolkę odbiera wejście myszy czy kursor znajduje się w jego granicach.  
  
## <a name="setting-mouse-capture"></a>Przechwytywanie myszy ustawienie  
 W formularzach Windows Forms myszy są przechwytywane przez kontrolkę, użytkownik naciśnie przycisk myszy na kontrolce, gdy wskaźnik myszy jest zwalniany przez kontrolkę, gdy użytkownik zwolni przycisk myszy.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Właściwość <xref:System.Windows.Forms.Control> klasa określa, czy formant został przechwycony myszy. Aby określić, kiedy traci przechwytywanie myszy w kontrolce, obsługi <xref:System.Windows.Forms.Control.MouseCaptureChanged> zdarzeń.  
  
 Tylko okna pierwszoplanowego możliwość przechwytywania myszą. Gdy próbuje oknem tła do przechwytywania myszą, okno odbiera wiadomości tylko w przypadku zdarzenia myszy, które występują, gdy wskaźnik myszy znajduje się w obrębie widoczne części okna. Ponadto nawet wtedy, gdy przechwyceniu myszy okna pierwszoplanowego użytkownik może nadal kliknąć innego okna, wprowadzić ją na pierwszym planie. Po przechwyceniu myszy klawiszy skrótów nie działa.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
