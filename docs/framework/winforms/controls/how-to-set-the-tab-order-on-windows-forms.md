---
title: 'Porady: ustawianie kolejności tabulacji na formularzach systemu Windows'
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 74244ae4e3692ed210b2a8f1513b035c85e98376
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332568"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Porady: ustawianie kolejności tabulacji na formularzach systemu Windows
Kolejność tabulacji polega na kolejności, w którym użytkownik przenosi fokus z jednego formantu do drugiego, naciskając klawisz TAB. Każdy formularz ma swój własny kolejności tabulacji. Domyślnie kolejność dostępu jest taka sama jak kolejność, w którym utworzono kontrolki. Kolejność tabulacji numerowania rozpoczyna się od zera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Aby ustawić kolejność tabulacji kontrolki  
  
1.  Na **widoku** menu, kliknij przycisk **kolejność tabulacji**.  
  
     Aktywuje tryb wyboru kolejność tabulacji w formularzu. Numer (reprezentujący <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość) pojawia się w lewym górnym rogu każdej kontrolki.  
  
2.  Kliknij formanty, które po kolei, aby ustanowić kolejność tabulacji, które chcesz.  
  
    > [!NOTE]
    >  Kontrolki miejscu w kolejności tabulacji można ustawić dowolną wartość większa niż lub równa 0. Gdy występują duplikaty, porządek dwie kontrolki jest obliczane i kontroli na górze na kartach jest pierwszy. (Warstwy visual kontrolek w formularzu wzdłuż osi z formularza [głębokość] jest porządku osi z. Porządek określa formanty, które znajdują się przed innymi kontrolkami). Aby uzyskać więcej informacji na temat porządku osi z, zobacz [Układanie warstwowo obiektów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Po zakończeniu kliknij przycisk **kolejność tabulacji** na **widoku** menu ponownie, aby wyjść z trybu zlecenia kartę.  
  
    > [!NOTE]
    >  Formanty, które nie można pobrać fokus, a także wyłączone i niewidoczne formantów, nie mają <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości i są nie zawarte w kolejności tabulacji. Jako użytkownik naciśnie klawisz TAB, te kontrolki są pomijane.  
  
 Alternatywnie, można ustawić kolejność tabulacji w oknie właściwości, używając <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. <xref:System.Windows.Forms.Control.TabIndex%2A> Właściwości formantu Określa, gdzie jest umieszczony w kolejności tabulacji. Domyślnie ma pierwszy formant rysowane <xref:System.Windows.Forms.Control.TabIndex%2A> wartość 0, drugi ma <xref:System.Windows.Forms.Control.TabIndex%2A> 1 i tak dalej.  
  
 Ponadto domyślnie <xref:System.Windows.Forms.GroupBox> kontrolka ma swój własny <xref:System.Windows.Forms.Control.TabIndex%2A> wartość, która jest liczbą całkowitą. A <xref:System.Windows.Forms.GroupBox> sama kontrolka nie ma fokusu w czasie wykonywania. W związku z tym, każdy formant, w ramach <xref:System.Windows.Forms.GroupBox> ma swój własny dziesiętnych <xref:System.Windows.Forms.Control.TabIndex%2A> wartości, zaczynając od.0. Oczywiście jako <xref:System.Windows.Forms.Control.TabIndex%2A> z <xref:System.Windows.Forms.GroupBox> kontroli jest zwiększany, w związku z tym jest zwiększany zawarte w niej kontrolki. Jeśli zmienisz <xref:System.Windows.Forms.Control.TabIndex%2A> wartość z zakresu od 5 do 6, <xref:System.Windows.Forms.Control.TabIndex%2A> wartość pierwszą kontrolkę w jego grupie automatycznie zmieni się w wersji 6.0 i tak dalej.  
  
 Na koniec dowolną kontrolkę wielu w formularzu można pominąć w kolejności tabulacji. Zazwyczaj klawisza TAB kolejno w czasie wykonywania wybiera każdego formantu w kolejności tabulacji. Wyłączając <xref:System.Windows.Forms.Control.TabStop%2A> właściwości, aby włączyć kontrolki w kolejności tabulacji formularza można przekazać za pośrednictwem.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Aby usunąć formant z kolejność tabulacji  
  
1.  Ustaw dla formantu <xref:System.Windows.Forms.Control.TabStop%2A> właściwości `false` w oknie dialogowym właściwości.  
  
     A formant, którego <xref:System.Windows.Forms.Control.TabStop%2A> została ustawiona właściwość `false` nadal obsługuje jego położenie w kolejności tabulacji, mimo że formant zostanie pominięta, gdy przechodzić między formantami za pomocą klawisza TAB.  
  
    > [!NOTE]
    >  Grupa przycisków radiowych ma jedną kartę Zatrzymaj w czasie wykonywania. Wybrany przycisk (oznacza to, że przycisk z jego <xref:System.Windows.Forms.RadioButton.Checked%2A> właściwością `true`) ma jego <xref:System.Windows.Forms.Control.TabStop%2A> automatycznie właściwością `true`, podczas gdy inne przyciski powinny mieć ich <xref:System.Windows.Forms.Control.TabStop%2A> właściwością `false`. Aby uzyskać więcej informacji na temat grupowania <xref:System.Windows.Forms.RadioButton> formantów, zobacz [grupowanie Windows formantów RadioButton formularzy aby działały jak zestaw](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
