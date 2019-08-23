---
title: 'Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 97888a77dfc731be591d5f0284e87f45ef7dc437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930171"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant
Poniższa procedura umożliwia utworzenie wielookienkowego interfejsu użytkownika, który jest podobny do tego, który jest używany w programie Microsoft Outlook, z listą **folderów** , okienkiem **wiadomości** i okienkiem **podglądu** . To rozwiązanie jest uzyskiwane głównie przez dokowanie kontrolek za pomocą formularza.

 Po zadokowanym formancie należy określić, z której krawędzią kontenera nadrzędnego jest przymocowany formant. W takim przypadku, jeśli ustawisz <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość na <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią kontrolki będzie zadokowany do prawej krawędzi jego kontrolki nadrzędnej. Ponadto zostanie zmieniony rozmiar zadokowanej krawędzi kontrolki w celu dopasowania jej do kontrolki kontenera. Aby uzyskać więcej informacji o tym <xref:System.Windows.Forms.SplitContainer.Dock%2A> , jak działa Właściwość [, zobacz How to: Zadokuj kontrolki na Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Ta procedura koncentruje się <xref:System.Windows.Forms.SplitContainer> na układaniu i innych kontrolkach w formularzu, a nie na dodawaniu funkcji w celu naśladowania aplikacji Microsoft Outlook.

 Aby utworzyć ten interfejs użytkownika, należy umieścić wszystkie kontrolki w <xref:System.Windows.Forms.SplitContainer> kontrolce, która <xref:System.Windows.Forms.TreeView> zawiera kontrolkę w panelu po lewej stronie. Panel <xref:System.Windows.Forms.SplitContainer> po prawej stronie kontrolki zawiera drugą <xref:System.Windows.Forms.SplitContainer> kontrolkę <xref:System.Windows.Forms.RichTextBox> z <xref:System.Windows.Forms.ListView> kontrolką nad kontrolką. Formanty <xref:System.Windows.Forms.SplitContainer> te umożliwiają niezależne zmienianie rozmiarów innych kontrolek w formularzu. Można dostosować techniki w tej procedurze, aby nawiązać własne niestandardowe interfejsy użytkownika.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Aby utworzyć interfejs użytkownika w stylu programu Outlook w czasie projektowania

1. Tworzenie nowego projektu aplikacji systemu Windows (**plik** > **Nowy** > **projekt** > **Visual C#**  lub **Visual Basic** > **klasyczny** pulpit >  **Windows Forms aplikacji**).

2. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.SplitContainer> W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

3. Przeciągnij kontrolkę z **przybornika** do panelu <xref:System.Windows.Forms.SplitContainer> po lewej stronie kontrolki. <xref:System.Windows.Forms.TreeView> W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość na <xref:System.Windows.Forms.DockStyle.Left> , klikając panel po lewej stronie w edytorze wartości widocznym po kliknięciu strzałki w dół.

4. Przeciągnij inny <xref:System.Windows.Forms.SplitContainer> formant z **przybornika**, umieść go w panelu <xref:System.Windows.Forms.SplitContainer> po prawej stronie kontrolki dodanej do formularza. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill> <xref:System.Windows.Forms.Orientation.Horizontal>właściwość na i właściwość na. <xref:System.Windows.Forms.SplitContainer.Orientation%2A>

5. Przeciągnij kontrolkę z **przybornika** do górnego panelu drugiej <xref:System.Windows.Forms.SplitContainer> kontrolki dodanej do formularza. <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.SplitContainer.Dock%2A> Ustaw właściwość <xref:System.Windows.Forms.ListView> formantu na <xref:System.Windows.Forms.DockStyle.Fill>.

6. Przeciągnij kontrolkę z **przybornika** do dolnego panelu drugiej <xref:System.Windows.Forms.SplitContainer> kontrolki. <xref:System.Windows.Forms.RichTextBox> <xref:System.Windows.Forms.SplitContainer.Dock%2A> Ustaw właściwość <xref:System.Windows.Forms.RichTextBox> formantu na <xref:System.Windows.Forms.DockStyle.Fill>.

     W tym momencie naciśnij klawisz F5, aby uruchomić aplikację, a w formularzu zostanie wyświetlony interfejs użytkownika z trzema częścią, podobny do tego w programie Microsoft Outlook.

    > [!NOTE]
    > Po umieszczeniu wskaźnika myszy nad dowolnym rozdzielaczem w <xref:System.Windows.Forms.SplitContainer> kontrolkach można zmienić rozmiar wewnętrznych wymiarów.

Na tym etapie opracowywania aplikacji przygotowano zaawansowany interfejs użytkownika. Następnym krokiem jest przechodzenie między programowaniem aplikacji, na przykład przez połączenie <xref:System.Windows.Forms.TreeView> kontrolki i <xref:System.Windows.Forms.ListView> kontrolek z pewnym rodzajem źródła danych. Aby uzyskać więcej informacji na temat łączenia formantów z danymi, zobacz [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
