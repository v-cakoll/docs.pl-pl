---
title: Przechwytywanie myszy
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741021"
---
# <a name="mouse-capture-in-windows-forms"></a>Przechwytywanie myszy w formularzach systemu Windows
*Przechwytywanie myszy* odnosi się do sytuacji, gdy kontrolka wykonuje polecenie wszystkich danych wejściowych myszy. Gdy kontrolka przechwytuje mysz, odbiera ona dane wejściowe za pomocą myszy niezależnie od tego, czy wskaźnik znajduje się w jego granicach.  
  
## <a name="setting-mouse-capture"></a>Ustawianie przechwytywania myszy  
 W Windows Forms wskaźnik myszy jest przechwytywany przez kontrolkę, gdy użytkownik naciśnie przycisk myszy na kontrolce, a mysz zostanie wydana przez kontrolkę, gdy użytkownik zwolni przycisk myszy.  
  
 Właściwość <xref:System.Windows.Forms.Control.Capture%2A> klasy <xref:System.Windows.Forms.Control> określa, czy kontrolka przechwytuje mysz. Aby określić, kiedy formant utraci przechwytywanie myszy, obsłuż zdarzenie <xref:System.Windows.Forms.Control.MouseCaptureChanged>.  
  
 Tylko okno pierwszego planu może przechwycić mysz. Gdy okno tła próbuje przechwycić myszą, okno odbiera komunikaty tylko dla zdarzeń myszy, które występują, gdy wskaźnik myszy znajduje się w widocznej części okna. Ponadto, nawet jeśli okno programu na pierwszym planie przechwytuje mysz, użytkownik może nadal klikać inne okna, umieszczając je na pierwszym planie. Gdy mysz zostanie przechwycona, klawisze skrótów nie działają.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
