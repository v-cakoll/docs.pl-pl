---
title: 'Instrukcje: testowanie zachowania UserControl w czasie wykonywania'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015777"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania

Podczas opracowywania programu <xref:System.Windows.Forms.UserControl>należy przetestować jego zachowanie w czasie wykonywania. Można utworzyć oddzielny projekt aplikacji oparty na systemie Windows i umieścić swój formant w formularzu testowym, ale ta procedura jest niewygodna. Szybszym i łatwiejszym sposobem jest użycie obiektu **UserControl Test Container** dostarczonego przez program Visual Studio. Ten kontener testowy jest uruchamiany bezpośrednio z projektu biblioteki formantów systemu Windows.

> [!IMPORTANT]
> Aby można było załadować <xref:System.Windows.Forms.UserControl>kontener testowy, formant musi mieć co najmniej jednego konstruktora publicznego.

> [!NOTE]
> Kontrolka C++ wizualizacji nie może być testowana przy użyciu obiektu **UserControl Test Container**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testowanie zachowania elementu UserControl w czasie wykonywania

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample**.

2. W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.Label> kontrolkę z przybornika na powierzchnię projektu kontrolki.

3. Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić **kontener testów UserControl**. Kontener testowy zostanie wyświetlony <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .

4. Wybierz właściwość wyświetlaną <xref:System.Windows.Forms.PropertyGrid> w kontrolce po prawej stronie okienka **podglądu.** <xref:System.Windows.Forms.Control.BackColor%2A> Zmień jej wartość na **ControlDark**. Zwróć uwagę, że formant zmieni się na ciemniejszy kolor. Spróbuj zmienić inne wartości właściwości i obserwuj wpływ na kontrolkę.

5. Kliknij pole wyboru Zadokuj **wypełnienie użytkownika** w okienku **podglądu** . Zwróć uwagę, że rozmiar kontrolki został zmieniony w celu wypełnienia okienka. Zmień rozmiar kontenera testowego i zwróć uwagę, że zmiana rozmiaru kontrolki jest w okienku.

6. Zamknij kontener testowy.

7. Dodaj kolejną kontrolkę użytkownika do projektu **TestContainerExample** .

8. W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z przybornika na powierzchnię projektu kontrolki.

9. Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić kontener testowy.

10. Kliknij przycisk **Wybierz kontrolkę** <xref:System.Windows.Forms.ComboBox> użytkownika, aby przełączać się między dwoma kontrolkami użytkownika.

## <a name="test-user-controls-from-another-project"></a>Testowanie kontrolek użytkownika z innego projektu

Kontrolki użytkownika można testować z innych projektów w kontenerze testów bieżącego projektu.

1. W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample2**.

2. W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.RadioButton> kontrolkę z przybornika na powierzchnię projektu kontrolki.

3. Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić kontener testowy. Kontener testowy zostanie wyświetlony <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .

4. Kliknij przycisk **ładowania** .

5. W oknie dialogowym **Otwórz** przejdź do **TestContainerExample**. dll, który został utworzony w poprzedniej procedurze. Wybierz **TestContainerExample**. dll, a następnie kliknij przycisk **Otwórz** , aby załadować kontrolki użytkownika

6. Użyj<xref:System.Windows.Forms.ComboBox> **kontrolki wybierz użytkownika** , aby przełączać między dwoma kontrolkami użytkownika z projektu **TestContainerExample** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- [Instrukcje: Tworzenie złożonych kontrolek](how-to-author-composite-controls.md)
- [Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Projektant formantów użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
