---
title: 'Porady: dziedziczenie z klasy formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458381"
---
# <a name="how-to-inherit-from-the-control-class"></a>Porady: dziedziczenie z klasy formantów

Jeśli chcesz utworzyć pełną kontrolkę niestandardową do użycia w formularzu systemu Windows, należy dziedziczyć z klasy <xref:System.Windows.Forms.Control>. Chociaż dziedziczenie z klasy <xref:System.Windows.Forms.Control> wymaga wykonania większej liczby planowania i implementacji, zapewnia również największy zakres opcji. Podczas dziedziczenia z <xref:System.Windows.Forms.Control>dziedziczyć bardzo podstawowe funkcje, które ułatwiają działanie kontrolek. Funkcja niezależna od klasy <xref:System.Windows.Forms.Control> obsługuje wprowadzanie danych przez użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar kontrolki, udostępnia uchwyt systemu Windows i zapewnia obsługę komunikatów i zabezpieczenia. Nie zawiera żadnego malowania, co w tym przypadku jest rzeczywistym renderowaniem interfejsu graficznego formantu lub nie zawiera żadnych określonych funkcji interakcji użytkownika. Wszystkie te aspekty należy dostarczyć za poorednictwem niestandardowego kodu.

## <a name="to-create-a-custom-control"></a>Aby utworzyć kontrolkę niestandardową

1. W programie Visual Studio Utwórz nową **aplikację systemu Windows** lub projekt **biblioteki formantów systemu Windows** .

2. W menu **projekt** wybierz polecenie **Dodaj klasę**.

3. W oknie dialogowym **Dodaj nowy element** kliknij przycisk **kontrolka niestandardowa**.

   Do projektu zostanie dodany nowy formant niestandardowy.

4. Naciśnij klawisz **F7** , aby otworzyć **Edytor kodu** dla kontrolki niestandardowej.

5. Znajdź metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, która będzie pusta, z wyjątkiem wywołania metody <xref:System.Windows.Forms.Control.OnPaint%2A> klasy bazowej.

6. Zmodyfikuj kod w celu uwzględnienia dowolnego niestandardowego malowania dla kontrolki.

   Aby uzyskać informacje na temat pisania kodu w celu renderowania grafiki dla kontrolek, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).

7. Zaimplementuj wszelkie niestandardowe metody, właściwości lub zdarzenia, które mają być dołączone przez formant.

8. Zapisz i Przetestuj swój formant.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
