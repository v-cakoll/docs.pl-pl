---
title: 'Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 2d5b79244d867ea4b6134413d42710b2eadc871e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532389"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows
Z powodu jego gotowy znajomości Eksploratora Windows jest typowe wybór interfejsu użytkownika dla aplikacji.  
  
 Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> formantu w oddzielnych paneli. Rozdzielacz zostają o zmiennym rozmiarze panelu. To rozmieszczenie formantów jest bardzo efektywnym sposobem wyświetlania oraz informacji o przeglądaniu.  
  
 Poniższe kroki przedstawiają sposób rozmieszczanie formantów w oknie Eksploratora przypominającej formularza systemu Windows. Nie pokazuj sposób dodawania funkcji przeglądania plików aplikacji Eksploratora Windows.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Aby utworzyć formularzu systemu Windows w stylu Eksploratora Windows  
  
1.  Utwórz nowy projekt aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Z **przybornika**:  
  
    1.  Przeciągnij <xref:System.Windows.Forms.SplitContainer> sterowania do formularza.  
  
    2.  Przeciągnij <xref:System.Windows.Forms.TreeView> sterowania do **SplitterPanel1** (panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel1**).  
  
    3.  Przeciągnij <xref:System.Windows.Forms.ListView> sterowania do **SplitterPanel2** (panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel2**).  
  
3.  Zaznacz wszystkie trzy naciśnięcie klawisza CTRL i klikając kolejno. Po wybraniu <xref:System.Windows.Forms.SplitContainer> sterowania, kliknij przycisk pasek podziału, a nie panele.  
  
    > [!NOTE]
    >  Nie używaj **Zaznacz wszystko** na **Edytuj** menu. Jeśli tak zrobisz, właściwość potrzebnych w następnym kroku nie będą widoczne w **właściwości** okna.  
  
4.  W **właściwości** ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Formularz zawiera interfejs użytkownika dwuczęściową, podobnie jak w Eksploratorze Windows.  
  
    > [!NOTE]
    >  Podczas przeciągania rozdzielacza panele resize samodzielnie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SplitContainer>  
 [Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Instrukcje: dzielenie okna w poziomie](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer, kontrolka](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
