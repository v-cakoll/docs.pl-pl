---
title: 'Porady: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 9c8cab952fd9d0c58380a308dd360dcedb2ea8f1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595586"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Porady: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant
W poniższej procedurze utworzysz złożonego interfejsu użytkownika podobny do komentarzowi użytemu w programie Microsoft Outlook przy użyciu **folderu** listy **wiadomości** okienku i **wwersjizapoznawczej** okienka. Taki układ odbywa się głównie za pośrednictwem dokowanie kontrolek za pomocą formularza.  
  
 Po zadokowaniu kontrolkę, należy określić, które krawędzią kontenera nadrzędnego formantu jest podłączony. W związku z tym Jeśli ustawisz <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią kontrolki będzie zadokowany na prawej krawędzi kontrolki nadrzędnej. Ponadto aby pasował do jego kontrolki kontenera zmieniany jest zadokowany krawędzią formantu. Aby uzyskać więcej informacji o tym, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość znaleźć [jak: Dock formantów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Ta procedura polega na rozmieszczanie <xref:System.Windows.Forms.SplitContainer> i inne kontrolki na formularzu, a nie na dodawanie funkcji do aplikacji Microsoft Outlook naśladować.  
  
 Aby utworzyć ten interfejs użytkownika, umieść wszystkie kontrolki w ramach <xref:System.Windows.Forms.SplitContainer> formant, który zawiera <xref:System.Windows.Forms.TreeView> kontrolki w panelu po lewej stronie. Na panelu po prawej stronie <xref:System.Windows.Forms.SplitContainer> kontrolka zawiera sekundy <xref:System.Windows.Forms.SplitContainer> kontrolką <xref:System.Windows.Forms.ListView> kontrolki powyżej <xref:System.Windows.Forms.RichTextBox> kontroli. Te <xref:System.Windows.Forms.SplitContainer> kontrolki umożliwiają, niezależnie od rozmiaru formantów w formularzu. Możliwość dostosowania technik w tej procedurze, aby tworzenie niestandardowych interfejsów użytkownika samodzielnie.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Aby utworzyć interfejs użytkownika programu Outlook stylu w czasie projektowania  
  
1.  Utwórz nowy projekt aplikacji Windows (**pliku** > **New** > **projektu** > **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  Przeciągnij <xref:System.Windows.Forms.SplitContainer> z kontrolować **przybornika** do formularza. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.   
  
3.  Przeciągnij <xref:System.Windows.Forms.TreeView> z kontrolować **przybornika** do panelu po lewej stronie <xref:System.Windows.Forms.SplitContainer> kontroli. W **właściwości** oknie <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Left> , klikając w panelu po lewej stronie ekranu, w edytorze wartości wyświetlane po kliknięciu strzałki w dół.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.SplitContainer> z kontrolować **przybornika**; umieść go w panelu po prawej stronie <xref:System.Windows.Forms.SplitContainer> formant został dodany do formularza. W **właściwości** oknie <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill> i <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwość <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Przeciągnij <xref:System.Windows.Forms.ListView> z kontrolować **przybornika** na górnym panelu drugi <xref:System.Windows.Forms.SplitContainer> formant został dodany do formularza. Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.ListView> kontrolę <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Przeciągnij <xref:System.Windows.Forms.RichTextBox> z kontrolować **przybornika** do dolnej części drugiej <xref:System.Windows.Forms.SplitContainer> kontroli. Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontrolę <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     W tym momencie użytkownik naciśnie klawisz F5, aby uruchomić aplikację, formularz zawiera interfejs użytkownika trzyczęściowej serii, podobnie jak w przypadku programu Microsoft Outlook.  
  
    > [!NOTE]
    >  Po umieszczeniu wskaźnika myszy nad albo rozdzielaczy w ramach <xref:System.Windows.Forms.SplitContainer> kontrolek, możesz zmienić rozmiar wewnętrznych wymiarów.  
  
     W tym momencie podczas tworzenia aplikacji ma specjalnie interfejsu użytkownika zaawansowane. Następnym krokiem jest przejściem z programowaniem aplikacji, być może, łącząc <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> kontrolki do pewnego rodzaju źródła danych. Aby uzyskać więcej informacji na temat kontrolek o łączeniu z danymi, zobacz [powiązanie danych i formularze Windows](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer, kontrolka](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
