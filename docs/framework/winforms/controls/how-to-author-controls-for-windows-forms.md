---
title: 'Porady: formanty autoryzacji dla formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 844e38fc62fc9fb04a723c1a4a8ad834e957c8ce
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870929"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Porady: formanty autoryzacji dla formularzy systemu Windows
Formant reprezentuje graficzny link między użytkownikiem i program. Kontrolki można podać i przetwarzania danych, akceptują dane wejściowe użytkownika, odpowiadanie na zdarzenia lub wykonywać dowolna liczba innych funkcji, które łączą się z użytkownikiem a aplikacją. Ponieważ formant jest zasadniczo składnika za pomocą interfejsu graficznego, może być każda funkcja, która jest składnikiem, również zapewnić interakcji z użytkownikiem. Formanty są tworzone do obsługi określonych celów i tworzenie formantów jest po prostu kolejne zadania programowania. Mając to na uwadze następujące kroki przedstawiają Przegląd kontroli procesu tworzenia. Linki udostępniają dodatkowe informacje na temat poszczególnych kroków.  
  
> [!NOTE]
>  Jeśli chcesz utworzyć formant niestandardowy do użycia w formularzach sieci Web, zobacz artykuł [tworzenie niestandardowe formanty serwera ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Tworzenie formantu  
  
1.  Należy określić co chcesz kontrolki do wykonania, co do część będzie odtwarzany w aplikacji. Dostępne są następujące czynniki do rozważenia:  
  
    -   Jakiego rodzaju interfejsu graficznego potrzebujesz?  
  
    -   Jakie interakcji użytkownika będzie obsługiwać ten formant?  
  
    -   Funkcje, których potrzebujesz świadczą żadnych istniejących kontrolek?  
  
    -   Możesz uzyskać funkcjonalność, czego potrzebujesz, łącząc kilka kontrolek Windows Forms  
  
2.  Jeśli potrzebujesz model obiektów dla kontrolki określają, jak będą dystrybuowane w całym modelu obiektów funkcje i podzielić funkcje między formantem i wszystkich podobiektów. Model obiektu może być przydatne, planowania złożonych kontroli, czy chcesz zastosować kilka funkcji.  
  
3.  Określanie typu formantu (na przykład, kontrolki użytkownika, formantu niestandardowego, odziedziczoną kontrolkę Windows Forms) należy. Aby uzyskać więcej informacji, zobacz [zalecenia dotyczące typu formantu](../../../../docs/framework/winforms/controls/control-type-recommendations.md) i [różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Express funkcjonalność, jak właściwości, metod i zdarzeń formantu i jego podobiektów lub struktur pomocniczych i przypisz poziomy dostępu (na przykład w publicznych, chronionych i tak dalej).  
  
5.  Jeśli potrzebujesz niestandardowego rysowania kontrolki, Dodaj kod dla niego. Aby uzyskać więcej informacji, zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Jeśli formant dziedziczy z <xref:System.Windows.Forms.UserControl>, możesz przetestować jej zachowanie środowiska uruchomieniowego, tworząc projekt kontroli i uruchomiony w **UserControl — kontener testu**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Można również testowanie i debugowanie kontrolki, tworząc nowy projekt, na przykład w przypadku aplikacji Windows i umieszczenie go w kontenerze. Ten proces jest przedstawiona jako część [wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  W miarę dodawania każdej funkcji, należy dodać funkcje do swojego projektu testowego, aby korzystać z nowych funkcji.  
  
9. Powtórz udoskonalanie projektu.  
  
10. Tworzenie pakietów i wdrażanie formantu. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji, usług i składników](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
