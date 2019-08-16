---
title: 'Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 0804b9824b84a32bdd79c763031a3de4ffa54099
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039877"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows

Kontrolka reprezentuje graficzny link między użytkownikiem a programem. Kontrolka może udostępniać lub przetwarzać dane, akceptować wprowadzanie danych przez użytkownika, odpowiadać na zdarzenia lub wykonywać dowolną liczbę innych funkcji, które łączą użytkownika i aplikację. Ponieważ kontrolka jest zasadniczo składnikiem interfejsu graficznego, może służyć dowolnej funkcji, która robi składnik, a także zapewnia interakcję z użytkownikiem. Formanty są tworzone w celu obsłużenia określonych celów, a formanty tworzenia są po prostu innym zadaniem programistycznym. Z tego względu poniższe kroki przedstawiają przegląd procesu tworzenia kontroli. Linki zawierają dodatkowe informacje dotyczące poszczególnych kroków.

> [!NOTE]
> Jeśli chcesz utworzyć kontrolkę niestandardową do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="to-author-a-control"></a>Aby utworzyć kontrolkę

1. Określ, co ma być wykonywane przez formant, lub część, która będzie odtwarzana w aplikacji. Czynniki, które należy wziąć pod uwagę:

    - Jakiego rodzaju interfejsu graficznego potrzebujesz?

    - Jakie Interakcje użytkownika będą obsługiwane przez tę kontrolkę?

    - Czy wymagane funkcje są dostępne w ramach istniejących kontrolek?

    - Czy możesz uzyskać dostęp do potrzebnych funkcji, łącząc kilka Windows Forms formantów?

2. Jeśli potrzebujesz modelu obiektowego dla kontrolki, określ, w jaki sposób funkcje będą dystrybuowane w całym modelu obiektów, i Podziel się funkcjonalnością między kontrolką a podobiektami. Model obiektu może być przydatny, jeśli planujesz kontrolę złożoną lub chcesz dołączyć kilka funkcji.

3. Określ typ formantu (na przykład kontrolka użytkownika, kontrolka niestandardowa, dziedziczona Windows Forms kontrolki). Aby uzyskać szczegółowe informacje, zobacz [zalecenia dotyczące typu kontroli](control-type-recommendations.md) i różne [rodzaje kontrolek niestandardowych](varieties-of-custom-controls.md).

4. Funkcje ekspresowe jako właściwości, metody i zdarzenia kontrolki i jej podobiektów lub struktur oddziałów, a także Przypisz odpowiednie poziomy dostępu (na przykład publiczne, chronione itd.).

5. Jeśli potrzebujesz niestandardowego rysowania kontrolki, Dodaj do niej kod. Aby uzyskać szczegółowe informacje, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).

6. Jeśli formant dziedziczy z <xref:System.Windows.Forms.UserControl>, można przetestować jego zachowanie w czasie wykonywania przez skompilowanie projektu kontrolki i uruchomienie go w **kontenerze testów UserControl**. Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.

7. Możesz również testować i debugować kontrolkę, tworząc nowy projekt, taki jak aplikacja systemu Windows i umieszczając go w kontenerze. Ten proces jest przedstawiany jako część [przewodnika: Tworzenie złożonego formantu z Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md).

8. Podczas dodawania każdej funkcji Dodaj funkcje do projektu testowego, aby skorzystać z nowych funkcji.

9. Powtórz tę czynność, aby udoskonalić projekt.

10. Spakuj i Wdróż swój formant. Aby uzyskać szczegółowe informacje, zobacz [pierwsze spojrzenie na wdrożenie w programie Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie złożonego formantu z Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Przewodnik: Dziedziczenie z kontrolki Windows Forms z Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)
- [Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
