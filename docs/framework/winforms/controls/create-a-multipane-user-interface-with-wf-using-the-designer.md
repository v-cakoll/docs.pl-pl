---
title: Tworzenie wielookienkowego interfejsu użytkownika przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 6b41d538f1cd1633cec51c89e27adf3c5b47f9a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737279"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Porady: tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows przy użyciu narzędzia Projektant
Poniższa procedura umożliwia utworzenie wielookienkowego interfejsu użytkownika, który jest podobny do tego, który jest używany w programie Microsoft Outlook, z listą **folderów** , okienkiem **wiadomości** i okienkiem **podglądu** . To rozwiązanie jest uzyskiwane głównie przez dokowanie kontrolek za pomocą formularza.

 Po zadokowanym formancie należy określić, z której krawędzią kontenera nadrzędnego jest przymocowany formant. W takim przypadku, jeśli ustawisz właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią kontrolki będzie zadokowany do prawej krawędzi jego kontrolki nadrzędnej. Ponadto zostanie zmieniony rozmiar zadokowanej krawędzi kontrolki w celu dopasowania jej do kontrolki kontenera. Aby uzyskać więcej informacji na temat działania właściwości <xref:System.Windows.Forms.SplitContainer.Dock%2A>, zobacz [How to: Docking Controls on Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Ta procedura koncentruje się na układaniu <xref:System.Windows.Forms.SplitContainer> i innych kontrolek w formularzu, a nie na dodawaniu funkcji, aby aplikacja naśladuje program Microsoft Outlook.

 Aby utworzyć ten interfejs użytkownika, należy umieścić wszystkie kontrolki w kontrolce <xref:System.Windows.Forms.SplitContainer>, która zawiera kontrolkę <xref:System.Windows.Forms.TreeView> w panelu po lewej stronie. Panel po prawej stronie kontrolki <xref:System.Windows.Forms.SplitContainer> zawiera drugą kontrolkę <xref:System.Windows.Forms.SplitContainer> z kontrolką <xref:System.Windows.Forms.ListView> nad formantem <xref:System.Windows.Forms.RichTextBox>. Te <xref:System.Windows.Forms.SplitContainer> formantów umożliwiają niezależne zmienianie rozmiarów innych kontrolek w formularzu. Można dostosować techniki w tej procedurze, aby nawiązać własne niestandardowe interfejsy użytkownika.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Aby utworzyć interfejs użytkownika w stylu programu Outlook w czasie projektowania

1. Utwórz nowy projekt aplikacji systemu Windows (**plik** > **Nowy** > **projektu** > **Wizualizacja C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).

2. Przeciągnij kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika** do formularza. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

3. Przeciągnij kontrolkę <xref:System.Windows.Forms.TreeView> z **przybornika** do panelu po lewej stronie kontrolki <xref:System.Windows.Forms.SplitContainer>. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Left>, klikając panel po lewej stronie w edytorze wartości widocznym po kliknięciu strzałki w dół.

4. Przeciągnij inną kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika**; Umieść go w panelu po prawej stronie kontrolki <xref:System.Windows.Forms.SplitContainer> dodanej do formularza. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill> i Właściwość <xref:System.Windows.Forms.SplitContainer.Orientation%2A> na <xref:System.Windows.Forms.Orientation.Horizontal>.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.ListView> z **przybornika** do górnego panelu drugiej kontrolki <xref:System.Windows.Forms.SplitContainer> dodanej do formularza. Ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> kontrolki <xref:System.Windows.Forms.ListView> na <xref:System.Windows.Forms.DockStyle.Fill>.

6. Przeciągnij kontrolkę <xref:System.Windows.Forms.RichTextBox> z **przybornika** do dolnego panelu drugiej kontrolki <xref:System.Windows.Forms.SplitContainer>. Ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> kontrolki <xref:System.Windows.Forms.RichTextBox> na <xref:System.Windows.Forms.DockStyle.Fill>.

     W tym momencie naciśnij klawisz F5, aby uruchomić aplikację, a w formularzu zostanie wyświetlony interfejs użytkownika z trzema częścią, podobny do tego w programie Microsoft Outlook.

    > [!NOTE]
    > Po umieszczeniu wskaźnika myszy nad dowolnym rozdzielaczem w kontrolkach <xref:System.Windows.Forms.SplitContainer> można zmienić rozmiar wewnętrznych wymiarów.

Na tym etapie opracowywania aplikacji przygotowano zaawansowany interfejs użytkownika. Następnym krokiem jest przechodzenie między programowaniem aplikacji, na przykład przez połączenie kontrolki <xref:System.Windows.Forms.TreeView> i kontrolek <xref:System.Windows.Forms.ListView> z pewnym rodzajem źródła danych. Aby uzyskać więcej informacji na temat łączenia formantów z danymi, zobacz [powiązanie danych i Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
