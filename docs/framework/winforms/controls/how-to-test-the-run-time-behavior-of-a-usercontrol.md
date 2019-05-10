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
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211714"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Instrukcje: Testowanie zachowania UserControl w czasie wykonywania

Podczas opracowywania <xref:System.Windows.Forms.UserControl>, należy przetestować jej zachowanie w czasie wykonywania. Można utworzyć projekt oddzielną aplikację z systemem Windows i umieść swój formant na formularzu testu, ale ta procedura jest wygodne. Szybciej i łatwiej metodą jest użycie **UserControl — kontener testowy** dostarczane przez program Visual Studio. Ten kontener testowy uruchamia się bezpośrednio z Twojego Projekt Biblioteka formantów Windows.

> [!IMPORTANT]
> Dla kontenera testów, które można załadować usługi <xref:System.Windows.Forms.UserControl>, kontrolka musi mieć co najmniej jeden konstruktor publiczny.

> [!NOTE]
> Kontrolki języka Visual C++ nie można przetestować za pomocą **UserControl — kontener testowy**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testowanie zachowania UserControl w czasie wykonywania

1. W programie Visual Studio Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample**. Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Label> z kontrolować **przybornika** na powierzchnię projektowania formantu.

3. Naciśnij klawisz **F5** Aby skompilować projekt i uruchomić **UserControl — kontener testowy**. Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.

4. Wybierz <xref:System.Windows.Forms.Control.BackColor%2A> właściwości wyświetlane w <xref:System.Windows.Forms.PropertyGrid> kontroli po prawej stronie **Podgląd** okienka. Zmień jej wartość na `ControlDark`. Sprawdź, czy kontrolka zmienia kolor ciemniejszego. Spróbuj zmienić wartości innych właściwości i obserwuj wpływ na Twoją kontrolą.

5. Kliknij przycisk **kontrolki użytkownika wypełnienia dokowania** poniższe pole wyboru **Podgląd** okienka. Sprawdź, czy zmieni się rozmiar kontrolki do wypełnienia okienka. Zmień rozmiar kontenera testu i obserwować zmiany rozmiaru za pomocą okienka kontrolki.

6. Zamknij kontener testu.

7. Dodaj inną kontrolkę użytkownika do **TestContainerExample** projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodaj istniejące elementy do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).

8. W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na powierzchnię projektowania formantu.

9. Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.

10. Kliknij przycisk **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników.

## <a name="test-user-controls-from-another-project"></a>Formanty użytkownika testów z innego projektu

Możesz przetestować kontrolki użytkownika z innych projektów w kontenerze testów bieżącego projektu.

1. Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample2**. Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.RadioButton> z kontrolować **przybornika** na powierzchnię projektowania formantu.

3. Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu. Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.

4. Kliknij przycisk **obciążenia** przycisku.

5. W **Otwórz** okno dialogowe, przejdź do **TestContainerExample**.dll, która utworzoną w poprzedniej procedurze. Wybierz **TestContainerExample**.dll i kliknij przycisk **Otwórz** przycisk, aby załadować kontrolki użytkownika

6. Użyj **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników z **TestContainerExample** projektu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- [Instrukcje: Formanty złożone autora](how-to-author-composite-controls.md)
- [Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Projektant kontrolki użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
