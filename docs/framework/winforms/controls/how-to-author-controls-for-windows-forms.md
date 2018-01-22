---
title: 'Porady: formanty autoryzacji dla formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 125e3f1c32c5186cce0b28aa3f8d1eff1ef95a09
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-controls-for-windows-forms"></a>Porady: formanty autoryzacji dla formularzy systemu Windows
Formant reprezentuje graficznego łącza między użytkownikiem i program. Formant można podać przetwarzania danych, akceptuje dane wejściowe użytkownika, odpowiadanie na zdarzenia lub wykonać dowolną liczbę inne funkcje, które połączenia użytkownika i aplikacji. Ponieważ formant jest zasadniczo składnika z interfejsem graficznym, może służyć każda funkcja, która jest składnikiem, a także podać interakcji z użytkownikiem. Formanty są tworzone w celu obsługi określonych celów i tworzenia formantów jest po prostu inną zadań programowania. Z tym pamiętać następujące kroki reprezentują Omówienie procesu tworzenia formantu. Łącza zawierają dodatkowe informacje na temat poszczególnych kroków.  
  
> [!NOTE]
>  Jeśli chcesz utworzyć niestandardowego formantu do używania w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-control"></a>Aby móc tworzyć formantu  
  
1.  Należy określić co chcesz formantu do wykonania, co należy ona do odtwarzania w aplikacji. Są elementami, które należy wziąć pod uwagę:  
  
    -   Jakiego rodzaju interfejsu graficznego potrzebujesz?  
  
    -   Jakie interakcji użytkownika będą obsługiwać tego formantu?  
  
    -   Funkcje, które są potrzebne są dostarczane przez wszystkich istniejących formantów?  
  
    -   Możesz uzyskać funkcji potrzebnych łącząc kilku formantów formularzy systemu Windows  
  
2.  Jeśli potrzebujesz model obiektów dla formantu określają, jak będą dystrybuowane w całym modelu obiektów funkcji i podział funkcji między formantu i wszystkich podobiektów. Model obiektów mogą być użyteczne, planowania złożonego formantu, czy chcesz dołączyć do nich kilka funkcji.  
  
3.  Określ typ formantu (na przykład kontrolki użytkownika, kontrolki niestandardowej, dziedziczone formantu formularzy systemu Windows) należy. Aby uzyskać więcej informacji, zobacz [zalecenia dotyczące typu formantu](../../../../docs/framework/winforms/controls/control-type-recommendations.md) i [odmian Kontrolki niestandardowe](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Express funkcji jako właściwości, metody i zdarzenia i jego podobiektów lub struktur pomocniczych i przypisz poziomy dostępu (na przykład publiczny, chroniony i tak dalej).  
  
5.  Jeśli potrzebujesz niestandardowych malowanie formantu, Dodaj kod dla niego. Aby uzyskać więcej informacji, zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Jeśli dziedziczy formantu <xref:System.Windows.Forms.UserControl>, można sprawdzić jego zachowania w czasie wykonywania po utworzeniu projektu kontroli i uruchomienie jej **kontenera testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Można również testowanie i debugowanie formantu za tworzenie nowego projektu, takie jak aplikacji systemu Windows i umieszczenie do kontenera. Ten proces jest przedstawiona w ramach [wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Podczas dodawania każdej funkcji dodawania funkcji do projektu testowego do korzystania z nowych funkcji.  
  
9. Powtórz udoskonalanie projektu.  
  
10. Pakiet i wdróż formantu. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji, usług i składników](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
