---
title: 'Instrukcje: dziedziczenie z klasy kontrolek'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 535827db660ab1113a25a01b7a0553a1c4414c74
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037786"
---
# <a name="how-to-inherit-from-the-control-class"></a>Instrukcje: dziedziczenie z klasy kontrolek
Jeśli chcesz utworzyć pełną kontrolkę niestandardową do użycia w formularzu systemu Windows, należy dziedziczyć z <xref:System.Windows.Forms.Control> klasy. Chociaż dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga wykonania większej liczby zaplanowanych i implementacji, zapewnia również największą gamę opcji. Podczas dziedziczenia z <xref:System.Windows.Forms.Control>, dziedziczysz bardzo podstawową funkcję, która sprawia, że formanty działają. Funkcja niezależna od <xref:System.Windows.Forms.Control> klasy obsługuje wprowadzanie danych przez użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar kontrolki, udostępnia uchwyt systemu Windows i zapewnia obsługę komunikatów i zabezpieczenia. Nie zawiera żadnego malowania, co w tym przypadku jest rzeczywistym renderowaniem interfejsu graficznego formantu lub nie zawiera żadnych określonych funkcji interakcji użytkownika. Wszystkie te aspekty należy dostarczyć za poorednictwem niestandardowego kodu.

## <a name="to-create-a-custom-control"></a>Aby utworzyć kontrolkę niestandardową

1. Utwórz nową **aplikację systemu Windows** lub projekt **biblioteki formantów systemu Windows** .

2. W menu **projekt** wybierz polecenie **Dodaj klasę**.

3. W oknie dialogowym **Dodaj nowy element** kliknij przycisk **kontrolka**niestandardowa.

     Do projektu zostanie dodany nowy formant niestandardowy.

4. Naciśnij klawisz F7, aby otworzyć **Edytor kodu** dla kontrolki niestandardowej.

5. Znajdź metodę, która będzie pusta, z wyjątkiem wywołania <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej. <xref:System.Windows.Forms.Control.OnPaint%2A>

6. Zmodyfikuj kod w celu uwzględnienia dowolnego niestandardowego malowania dla kontrolki.

     Aby uzyskać informacje na temat pisania kodu w celu renderowania grafiki dla kontrolek, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).

7. Zaimplementuj wszelkie niestandardowe metody, właściwości lub zdarzenia, które mają być dołączone przez formant.

8. Zapisz i Przetestuj swój formant.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
