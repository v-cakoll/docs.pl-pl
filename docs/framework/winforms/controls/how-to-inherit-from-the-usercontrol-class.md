---
title: 'Instrukcje: dziedziczenie z klasy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5e9bdb6d6628b1c696b7944dc0ea1f4c974c8172
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941131"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Instrukcje: dziedziczenie z klasy UserControl
Aby połączyć funkcje co najmniej jednej kontrolki Windows Forms za pomocą kodu niestandardowego, można utworzyć *kontrolki użytkownika*. Formanty użytkownika połączyć rozwoju szybkiej kontroli, standardowych formularzy Windows kontrolować funkcjonalność i wszechstronności niestandardowe właściwości i metod. Po rozpoczęciu tworzenia kontrolki użytkownika, są prezentowane za pomocą projektanta widoczne, na którym można umieścić standardowych kontrolek Windows Forms. Te kontrolki zachowuje wszystkie ich używaniem funkcji, a także wygląd i zachowanie (wyglądu i działania) standardowych kontrolek. Gdy te kontrolki są wbudowane w kontrolce użytkownika, jednak nie są już dostępne za pośrednictwem kodu. Kontrolki użytkownika nie swój własny obraz, a także obsługuje wszystkie podstawowe funkcje, które są skojarzone z formantami.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-user-control"></a>Aby utworzyć kontrolkę użytkownika  
  
1. Utwórz nową **Biblioteka formantów Windows** projektu.  
  
     Nowy projekt zostanie utworzony przy użyciu kontrola pustego użytkownika.  
  
2. Przeciągnij formanty z **Windows Forms** karcie **przybornika** do projektanta.  
  
3. Te kontrolki powinien być umieszczony i zaprojektowana jako ma być wyświetlane w kontrolce użytkownika końcowego. Chcesz umożliwiają deweloperom dostęp do formantów składowych, należy zadeklarować je jako publiczne lub selektywnie udostępnianie właściwości składowych kontroli. Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie właściwości formantów składowych](how-to-expose-properties-of-constituent-controls.md).  
  
4. Implementowanie niestandardowych metod dowolnej właściwości, które będą zawierały kontrolki.  
  
5. Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**. Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Dziedziczenie z klasy formantów](how-to-inherit-from-the-control-class.md)
- [Instrukcje: Dziedzicz Windows istniejących formantów formularzy](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: Tworzenie kontrolek dla formularzy Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Instrukcje: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
