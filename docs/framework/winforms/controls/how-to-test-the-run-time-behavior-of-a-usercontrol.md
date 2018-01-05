---
title: 'Porady: testowanie zachowania UserControl w czasie wykonywania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ccf386acd50338f1743bbf8f6be38b3267a7103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Porady: testowanie zachowania UserControl w czasie wykonywania
Podczas opracowywania <xref:System.Windows.Forms.UserControl>, należy przetestować jego zachowania w czasie wykonywania. Można utworzyć projekt oddzielne aplikacji systemu Windows i umieścić formantu w formularzu testu, ale ta procedura jest niewygodne. Sposób szybciej i łatwiej jest użycie **kontener testu UserControl** dostarczane przez program Visual Studio. Ten kontener testowy rozpoczyna się bezpośrednio z projektu biblioteki sterowania systemu Windows.  
  
> [!IMPORTANT]
>  W celu załadować kontenera testu z <xref:System.Windows.Forms.UserControl>, kontrolka musi mieć co najmniej jeden konstruktor publiczny.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Formant Visual C++ nie można przetestować przy użyciu **kontener testu UserControl**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>Aby przetestować zachowania UserControl w czasie wykonywania  
  
1.  Tworzenie projektu biblioteki sterowania systemu Windows o nazwie **TestContainerExample**. Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.Label> kontrolować z **przybornika** na powierzchnię projektu formantu.  
  
3.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić **kontener testu UserControl**. Kontener testu jest wyświetlany z Twojej <xref:System.Windows.Forms.UserControl> w **Podgląd** okienka.  
  
4.  Wybierz <xref:System.Windows.Forms.Control.BackColor%2A> właściwości wyświetlane w <xref:System.Windows.Forms.PropertyGrid> formantu z prawej strony **Podgląd** okienka. Zmień wartość na `ControlDark`. Sprawdź, czy formant zmienia kolor ciemniejszego. Spróbuj zmienić wartości innych właściwości i obserwować wpływ na formantu.  
  
5.  Kliknij przycisk **dokowania wypełnienia kontrolki użytkownika** poniższe pole wyboru **Podgląd** okienka. Sprawdź, czy do wypełnienia w okienku zostanie zmieniony rozmiar formantu. Zmień rozmiar kontener testu i sprawdź, czy okienko zostanie zmieniony rozmiar formantu.  
  
6.  Zamknij kontener testu.  
  
7.  Dodaj inny formant użytkownika do **TestContainerExample** projektu. Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na powierzchnię projektu formantu.  
  
9. Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.  
  
10. Kliknij przycisk **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> do przełączania między formantami dwóch użytkowników.  
  
## <a name="testing-user-controls-from-another-project"></a>Testowanie kontrolek użytkownika z innego projektu  
 Formanty użytkownika z innych projektów można przetestować w kontenerze testowym bieżącego projektu.  
  
#### <a name="to-test-user-controls-from-another-project"></a>Aby przetestować kontrolek użytkownika z innego projektu  
  
1.  Tworzenie projektu biblioteki sterowania systemu Windows o nazwie **TestContainerExample2**. Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.RadioButton> kontrolować z **przybornika** na powierzchnię projektu formantu.  
  
3.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu. Kontener testu jest wyświetlany z Twojej <xref:System.Windows.Forms.UserControl> w **Podgląd** okienka.  
  
4.  Kliknij przycisk **obciążenia** przycisku.  
  
5.  W **Otwórz** okno dialogowe, przejdź do **TestContainerExample**.dll, które zostały utworzone w poprzedniej procedurze. Wybierz **TestContainerExample**dll i kliknij przycisk **Otwórz** przycisk, aby załadować kontrolki użytkownika  
  
6.  Użyj **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> do przełączania między formantami dwóch użytkowników z **TestContainerExample** projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl>  
 [Instrukcje: tworzenie kontrolek złożonych](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Projektanta formantów użytkownika](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
