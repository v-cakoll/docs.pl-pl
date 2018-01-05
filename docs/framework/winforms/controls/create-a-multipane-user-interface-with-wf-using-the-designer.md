---
title: "Porady: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cfd9f258aa7c43f4c98e475c40af7fe7d9c286b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Porady: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant
W poniższej procedurze utworzysz złożonego interfejsu użytkownika podobny do tego używanego w programie Microsoft Outlook z **folderu** listy **wiadomości** okienku i **wwersjizapoznawczej** okienka. To rozmieszczenie odbywa się głównie za pośrednictwem dokowanie formantów w formularzu.  
  
 Dokowanie formantu, określić, które krawędzią kontenera nadrzędnego formantu jest podłączony. W związku z tym Jeśli ustawisz <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią formantu zostanie zadokowane do prawej krawędzi kontrolki nadrzędnej. Ponadto zadokowanych krawędzią formantu jest zmieniany na zgodny z jego formantu kontenera. Aby uzyskać więcej informacji na temat sposobu <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości znaleźć [porady: dokowania formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Ta procedura polega na rozmieszczanie <xref:System.Windows.Forms.SplitContainer> i innych kontrolek w formularzu, a nie na dodawanie funkcji, aby aplikacja naśladować Microsoft Outlook.  
  
 Aby utworzyć ten interfejs użytkownika, umieść wszystkie formanty w <xref:System.Windows.Forms.SplitContainer> formant, który zawiera <xref:System.Windows.Forms.TreeView> kontroli w lewym panelu. Na prawym panelu <xref:System.Windows.Forms.SplitContainer> formant zawiera drugi <xref:System.Windows.Forms.SplitContainer> sterować za pomocą <xref:System.Windows.Forms.ListView> powyższej kontrolki <xref:System.Windows.Forms.RichTextBox> formantu. Te <xref:System.Windows.Forms.SplitContainer> formanty włączyć niezależne zmiana rozmiaru formantów w formularzu. Istnieje możliwość dostosowania technik w ramach tej procedury, aby jednostki niestandardowych interfejsów użytkownika własny.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Aby utworzyć interfejsu użytkownika w stylu programu Outlook w czasie projektowania  
  
1.  Utwórz nowy projekt aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Przeciągnij <xref:System.Windows.Forms.SplitContainer> kontrolować z **przybornika** do formularza. W **właściwości** ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Przeciągnij <xref:System.Windows.Forms.TreeView> kontrolować z **przybornika** na lewym panelu <xref:System.Windows.Forms.SplitContainer> formantu. W **właściwości** ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Left> , klikając panel po lewej stronie w edytorze wartości wyświetlane, gdy zostanie kliknięty strzałkę w dół.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.SplitContainer> kontrolować z **przybornika**; umieść go w prawym panelu <xref:System.Windows.Forms.SplitContainer> formant został dodany do formularza. W **właściwości** ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill> i <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwości <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Przeciągnij <xref:System.Windows.Forms.ListView> kontrolować z **przybornika** górny panel drugiego <xref:System.Windows.Forms.SplitContainer> formant został dodany do formularza. Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.ListView> formant <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Przeciągnij <xref:System.Windows.Forms.RichTextBox> kontrolować z **przybornika** do dolnej części drugiego <xref:System.Windows.Forms.SplitContainer> formantu. Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formant <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     W tym momencie naciśnij klawisz F5, aby uruchomić aplikację, formularz zawiera interfejs użytkownika trzyczęściowej, podobnie jak program Microsoft Outlook.  
  
    > [!NOTE]
    >  Gdy umieść kursor myszy nad albo rozdzielaczy w <xref:System.Windows.Forms.SplitContainer> formantów, można zmienić rozmiar wewnętrznych wymiarów.  
  
     W tym momencie do rozwoju aplikacji, mają co interfejs użytkownika zaawansowane. Następnym krokiem jest postępowania z programowaniem aplikacji, prawdopodobnie łącząc <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> formanty do określonego rodzaju źródła danych. Aby uzyskać więcej informacji na temat łączenie kontrolek z danymi, zobacz [powiązania danych i formularze systemu Windows](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer, kontrolka](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
