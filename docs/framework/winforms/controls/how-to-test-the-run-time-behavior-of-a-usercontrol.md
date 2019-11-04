---
title: 'Porady: testowanie zachowania UserControl w czasie wykonywania'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be6c913c43e3559806bc9f38a9c3152b544e4c07
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455537"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Instrukcje: testowanie zachowania elementu UserControl w czasie wykonywania

Podczas tworzenia <xref:System.Windows.Forms.UserControl> należy przetestować jego zachowanie w czasie wykonywania. Można utworzyć oddzielny projekt aplikacji oparty na systemie Windows i umieścić swój formant w formularzu testowym, ale ta procedura jest niewygodna. Szybszym i łatwiejszym sposobem jest użycie obiektu **UserControl Test Container** dostarczonego przez program Visual Studio. Ten kontener testowy jest uruchamiany bezpośrednio z projektu biblioteki formantów systemu Windows.

> [!IMPORTANT]
> Aby kontener testowy załadował <xref:System.Windows.Forms.UserControl>, formant musi mieć co najmniej jednego konstruktora publicznego.

> [!NOTE]
> Kontrolka C++ wizualizacji nie może być testowana przy użyciu obiektu **UserControl Test Container**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testowanie zachowania elementu UserControl w czasie wykonywania

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample**.

2. W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.Label> z **przybornika** na powierzchnię projektu kontrolki.

3. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić **kontener testów UserControl**. Kontener testowy pojawia się z <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .

4. Wybierz właściwość <xref:System.Windows.Forms.Control.BackColor%2A> wyświetlaną w kontrolce <xref:System.Windows.Forms.PropertyGrid> po prawej stronie okienka **podglądu** . Zmień jej wartość na **ControlDark**. Zwróć uwagę, że formant zmieni się na ciemniejszy kolor. Spróbuj zmienić inne wartości właściwości i obserwuj wpływ na kontrolkę.

5. Kliknij pole wyboru **Zadokuj wypełnienie użytkownika** w okienku **podglądu** . Zwróć uwagę, że rozmiar kontrolki został zmieniony w celu wypełnienia okienka. Zmień rozmiar kontenera testowego i zwróć uwagę, że zmiana rozmiaru kontrolki jest w okienku.

6. Zamknij kontener testowy.

7. Dodaj kolejną kontrolkę użytkownika do projektu **TestContainerExample** .

8. W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na powierzchnię projektu kontrolki.

9. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić kontener testowy.

10. Kliknij przycisk **Wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox>, aby przełączać się między dwoma kontrolkami użytkownika.

## <a name="test-user-controls-from-another-project"></a>Testowanie kontrolek użytkownika z innego projektu

Kontrolki użytkownika można testować z innych projektów w kontenerze testów bieżącego projektu.

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample2**.

2. W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.RadioButton> z **przybornika** na powierzchnię projektu kontrolki.

3. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić kontener testowy. Kontener testowy pojawia się z <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .

4. Kliknij przycisk **ładowania** .

5. W oknie dialogowym **Otwórz** przejdź do *TestContainerExample. dll*, który został utworzony w poprzedniej procedurze. Wybierz *TestContainerExample. dll* , a następnie kliknij przycisk **Otwórz** , aby załadować kontrolki użytkownika.

6. Użyj **opcji Wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox>, aby przełączać między dwoma kontrolkami użytkownika z projektu **TestContainerExample** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- [Instrukcje: tworzenie kontrolek złożonych](how-to-author-composite-controls.md)
- [Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Projektant formantów użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
