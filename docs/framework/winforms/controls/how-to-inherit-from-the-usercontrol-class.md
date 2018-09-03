---
title: 'Porady: dziedziczenie z klasy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5a826b9fc68bebfa32049a38899ddffaacd25607
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488134"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Porady: dziedziczenie z klasy UserControl
Aby połączyć funkcje co najmniej jednej kontrolki Windows Forms za pomocą kodu niestandardowego, można utworzyć *kontrolki użytkownika*. Formanty użytkownika połączyć rozwoju szybkiej kontroli, standardowych formularzy Windows kontrolować funkcjonalność i wszechstronności niestandardowe właściwości i metod. Po rozpoczęciu tworzenia kontrolki użytkownika, są prezentowane za pomocą projektanta widoczne, na którym można umieścić standardowych kontrolek Windows Forms. Te kontrolki zachowuje wszystkie ich używaniem funkcji, a także wygląd i zachowanie (wyglądu i działania) standardowych kontrolek. Gdy te kontrolki są wbudowane w kontrolce użytkownika, jednak nie są już dostępne za pośrednictwem kodu. Kontrolki użytkownika nie swój własny obraz, a także obsługuje wszystkie podstawowe funkcje, które są skojarzone z formantami.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-user-control"></a>Aby utworzyć kontrolkę użytkownika  
  
1.  Utwórz nową **Biblioteka formantów Windows** projektu.  
  
     Nowy projekt zostanie utworzony przy użyciu kontrola pustego użytkownika.  
  
2.  Przeciągnij formanty z **Windows Forms** karcie **przybornika** do projektanta.  
  
3.  Te kontrolki powinien być umieszczony i zaprojektowana jako ma być wyświetlane w kontrolce użytkownika końcowego. Chcesz umożliwiają deweloperom dostęp do formantów składowych, należy zadeklarować je jako publiczne lub selektywnie udostępnianie właściwości składowych kontroli. Aby uzyskać więcej informacji, zobacz [porady: udostępnianie właściwości formantów składników](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Implementowanie niestandardowych metod dowolnej właściwości, które będą zawierały kontrolki.  
  
5.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
