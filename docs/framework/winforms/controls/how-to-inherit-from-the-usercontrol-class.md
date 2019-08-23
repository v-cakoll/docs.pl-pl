---
title: 'Instrukcje: dziedziczenie z klasy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966570"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Instrukcje: dziedziczenie z klasy UserControl
Aby połączyć funkcje co najmniej jednej kontrolki Windows Forms z kodem niestandardowym, można utworzyć *kontrolkę użytkownika*. Kontrolki użytkownika łączą programowanie szybkiej kontroli, standardowe funkcje kontroli Windows Forms i uniwersalność niestandardowych właściwości i metod. Po rozpoczęciu tworzenia kontrolki użytkownika zostanie wyświetlony widoczny Projektant, na którym można umieścić standardowe kontrolki Windows Forms. Te kontrolki zachowują wszystkie funkcje, a także wygląd i zachowanie (wyglądu i działania) standardowych kontrolek. Po wbudowaniu tych kontrolek w kontrolce użytkownika nie są one już dostępne za pomocą kodu. Kontrolka użytkownika wykonuje własne malowanie, a także obsługuje wszystkie podstawowe funkcje związane z kontrolkami.

## <a name="to-create-a-user-control"></a>Aby utworzyć kontrolkę użytkownika

1. Utwórz nowy projekt **biblioteki formantów systemu Windows** .

     Tworzony jest nowy projekt z pustą kontrolką użytkownika.

2. Przeciągnij kontrolki z karty **Windows Forms** przybornika do projektanta.

3. Te kontrolki powinny być rozmieszczone i zaprojektowane tak, aby były wyświetlane w końcowej kontrolce użytkownika. Aby umożliwić deweloperom dostęp do kontrolek składnika, należy zadeklarować je jako publiczne lub selektywnie uwidocznić właściwości kontrolki składnik. Aby uzyskać szczegółowe informacje [, zobacz How to: Uwidacznia właściwości kontrolek](how-to-expose-properties-of-constituent-controls.md)składnika.

4. Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.

5. Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**. Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)
- [Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
