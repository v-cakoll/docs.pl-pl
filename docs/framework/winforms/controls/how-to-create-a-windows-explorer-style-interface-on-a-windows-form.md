---
title: 'Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 249210d2bcb7a9ef2c5bf1aed00bcfe138193aab
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456710"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows
Eksplorator Windows jest wspólne wybór interfejsu użytkownika dla aplikacji ze względu na swoją znajomość gotowe.  
  
 Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> formantu w oddzielnych paneli. Rozdzielacz zostają o zmiennym rozmiarze paneli. Taki układ kontrolki jest bardzo skuteczny sposób na wyświetlanie i informacji o przeglądaniu.  
  
 Poniższe kroki pokazują, jak można rozmieścić formanty w Windows Explorer przypominającej formularza. Nie są wyświetlane jak dodać funkcję przeglądania plików aplikacji w Eksploratorze Windows.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Aby utworzyć formularz Windows stylu Eksploratora Windows  
  
1.  Utwórz nowy projekt aplikacji Windows (**pliku** > **New** > **projektu** > **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  Z **przybornika**:  
  
    1.  Przeciągnij <xref:System.Windows.Forms.SplitContainer> formantu do formularza.  
  
    2.  Przeciągnij <xref:System.Windows.Forms.TreeView> sterowania do **SplitterPanel1** (z panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel1**).  
  
    3.  Przeciągnij <xref:System.Windows.Forms.ListView> sterowania do **SplitterPanel2** (z panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **elementu Panel2**).  
  
3.  Zaznacz wszystkie trzy, naciskając klawisz CTRL i klikając je z osobna. Po wybraniu <xref:System.Windows.Forms.SplitContainer> sterowania, kliknij pasek podziału, a nie paneli.  
  
    > [!NOTE]
    >  Nie używaj **Zaznacz wszystko** polecenie **Edytuj** menu. Jeśli tak zrobisz, właściwość potrzebna w następnym kroku nie będą widoczne w **właściwości** okna.  
  
4.  W **właściwości** oknie <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Formularz zawiera interfejs użytkownika składający się z dwóch części, podobnie jak w Eksploratorze Windows.  
  
    > [!NOTE]
    >  Podczas przeciągania rozdzielacza zmienić rozmiar paneli, samodzielnie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 [Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Instrukcje: dzielenie okna w poziomie](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer, kontrolka](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
