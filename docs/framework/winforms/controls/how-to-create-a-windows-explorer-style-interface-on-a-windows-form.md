---
title: 'Instrukcje: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039532"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Instrukcje: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows
Eksplorator Windows to typowy wybór interfejsu użytkownika dla aplikacji ze względu na jego gotowość.

 Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> formantem <xref:System.Windows.Forms.ListView> i kontrolką w oddzielnych panelach. Panele są zmieniane na rozmiar rozdzielacza. Takie rozmieszczenie formantów jest bardzo skuteczne do wyświetlania i przeglądania informacji.

 Poniższe kroki pokazują, jak rozmieścić kontrolki w formularzu podobnym do Eksploratora Windows. Nie pokazuje, jak dodać funkcję przeglądania plików aplikacji Eksploratora Windows.

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Aby utworzyć formularz systemu Windows w stylu Eksploratora Windows

1. Tworzenie nowego projektu aplikacji systemu Windows (**plik** > **Nowy** > **projekt** > **Visual C#**  lub **Visual Basic** > **klasyczny** pulpit >  **Windows Forms aplikacji**).

2. Z **przybornika**:

    1. <xref:System.Windows.Forms.SplitContainer> Przeciągnij kontrolkę na formularz.

    2. Przeciągnij kontrolkę do **SplitterPanel1** (Panel <xref:System.Windows.Forms.SplitContainer> kontrolki oznaczonej jako **element Panel1**). <xref:System.Windows.Forms.TreeView>

    3. Przeciągnij kontrolkę do **SplitterPanel2** (Panel <xref:System.Windows.Forms.SplitContainer> kontrolki oznaczonej jako **Panel2**). <xref:System.Windows.Forms.ListView>

3. Zaznacz wszystkie trzy kontrolki, naciskając klawisz CTRL i klikając je. Po wybraniu <xref:System.Windows.Forms.SplitContainer> kontrolki kliknij pasek podziału zamiast paneli.

    > [!NOTE]
    >  Nie należy używać polecenia **Zaznacz wszystko** w menu **Edycja** . Jeśli to zrobisz, właściwość wymagana w następnym kroku nie zostanie wyświetlona w oknie **Właściwości** .

4. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

5. Naciśnij klawisz F5, aby uruchomić aplikację.

     W formularzu zostanie wyświetlony dwuczęściowy interfejs użytkownika, podobny do tego w Eksploratorze Windows.

    > [!NOTE]
    >  Po przeciągnięciu rozdzielacza panele zmienią się.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [Instrukcje: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Instrukcje: Definiowanie zachowania zmiany rozmiaru i pozycjonowania w podzielonym oknie](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Instrukcje: Podziel okno w poziomie](how-to-split-a-window-horizontally.md)
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
