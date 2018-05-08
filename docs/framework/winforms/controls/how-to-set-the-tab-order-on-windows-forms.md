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
ms.openlocfilehash: ca5b9c29d9138d4e17fbf187e35951dbec614aab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Porady: ustawianie kolejności tabulacji na formularzach systemu Windows
Kolejność tabulacji to kolejność, w którym użytkownik przenosi fokus z jednego formantu do innego, naciskając klawisz TAB. Każdy formularz ma własną kolejności tabulacji. Domyślnie kolejność tabulacji jest taka sama jak kolejność, w której utworzono kontrolki. Kolejność tabulacji numerowanie rozpoczyna się od zera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Aby ustawić kolejność tabulacji formantu  
  
1.  Na **widoku** menu, kliknij przycisk **kolejności tabulacji**.  
  
     Aktywuje tryb zaznaczania kolejność tabulacji w formularzu. Numer (reprezentujący <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości) pojawi się w lewym górnym rogu każdej kontrolki.  
  
2.  Kliknij formanty sekwencyjnie ustanowienie kolejności tabulacji, który ma.  
  
    > [!NOTE]
    >  Miejsce formantu w kolejności tabulacji można ustawić dowolną wartość większa niż lub równa 0. Gdy występują duplikaty, porządek osi z dwóch formantów jest obliczane i kontroli w górnej części jest kartach do pierwszej. (Porządek osi jest visual warstwy formantów w formularzu wzdłuż osi z formularza [głębokość]. Porządek osi określa, które kontrolki znajdują się przed inne formanty.) Aby uzyskać więcej informacji o porządek, zobacz [Układanie warstwowo obiektów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Po zakończeniu kliknij przycisk **kolejności tabulacji** na **widoku** menu ponownie, aby wyjść z trybu kolejności kartę.  
  
    > [!NOTE]
    >  Formanty, które nie może uzyskać fokusu, a także wyłączone i niewidoczne formantów, nie mają <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości i są niewymienione w kolejności tabulacji. Jako użytkownik naciśnie klawisz TAB, są pomijane tych kontrolek.  
  
 Alternatywnie można ustawić kolejność tabulacji w oknie właściwości, używając <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. <xref:System.Windows.Forms.Control.TabIndex%2A> Właściwości formantu Określa, gdzie znajduje się w kolejności tabulacji. Domyślnie pierwszą kontrolkę rysowane ma <xref:System.Windows.Forms.Control.TabIndex%2A> wartość 0, drugi ma <xref:System.Windows.Forms.Control.TabIndex%2A> 1 i tak dalej.  
  
 Ponadto domyślnie <xref:System.Windows.Forms.GroupBox> formantu ma własną <xref:System.Windows.Forms.Control.TabIndex%2A> wartość, która jest liczbą całkowitą. A <xref:System.Windows.Forms.GroupBox> formancie nie ma fokusu w czasie wykonywania. W związku z tym każdego formantu w <xref:System.Windows.Forms.GroupBox> ma własną dziesiętnych <xref:System.Windows.Forms.Control.TabIndex%2A> wartości, zaczynając od.0. Oczywiście jako <xref:System.Windows.Forms.Control.TabIndex%2A> z <xref:System.Windows.Forms.GroupBox> kontroli jest zwiększany, odpowiednio jest zwiększany formantów w niej. Jeśli zmienisz <xref:System.Windows.Forms.Control.TabIndex%2A> z zakresu od 5 do 6, <xref:System.Windows.Forms.Control.TabIndex%2A> wartość pierwszą kontrolkę w jego grupie automatycznie zmienia się na 6.0 i tak dalej.  
  
 Na koniec żadnego formantu wiele w formularzu można pominięte w kolejności tabulacji. Zazwyczaj naciśnięcie klawisza TAB kolejno w czasie wykonywania wybiera każdego formantu w kolejności tabulacji. Wyłączenie <xref:System.Windows.Forms.Control.TabStop%2A> właściwości, możesz wprowadzić formantu można przekazać kolejności tabulacji dla formularza.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Aby usunąć formant z kolejność tabulacji  
  
1.  Ustawianie formantu <xref:System.Windows.Forms.Control.TabStop%2A> właściwości `false` w oknie właściwości.  
  
     A kontroli, których <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną właściwość `false` nadal utrzymuje jej położenie w kolejności tabulacji, mimo że formantu zostanie pominięty podczas cyklu przez kontrolki przy pomocy klawisza TAB.  
  
    > [!NOTE]
    >  Grupa przycisków radiowych ma jedną kartę zatrzymać w czasie wykonywania. Przycisku (czyli element button z jego <xref:System.Windows.Forms.RadioButton.Checked%2A> ustawioną właściwość `true`) ma jego <xref:System.Windows.Forms.Control.TabStop%2A> automatycznie ustawioną właściwość `true`, podczas gdy inne przyciski mają ich <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną właściwość `false`. Aby uzyskać więcej informacji na temat grupowania <xref:System.Windows.Forms.RadioButton> formantów, zobacz [Grupowanie formantów formularzy systemu Windows RadioButton mógł działać jako zestaw](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
