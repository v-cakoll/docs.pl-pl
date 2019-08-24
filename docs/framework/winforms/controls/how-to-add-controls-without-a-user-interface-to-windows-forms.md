---
title: 'Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987085"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows

Niewizualny formant (lub składnik) zapewnia funkcjonalność aplikacji. W przeciwieństwie do innych kontrolek składniki nie udostępniają użytkownikowi interfejsu użytkownika, więc nie muszą być wyświetlane na powierzchni Projektant formularzy systemu Windows. Po dodaniu składnika do formularza Projektant formularzy systemu Windows wyświetla zasobnik o zmiennym rozmiarze w dolnej części formularza, w którym są wyświetlane wszystkie składniki. Po dodaniu kontrolki do zasobnika składników można wybrać składnik i ustawić jego właściwości, tak jak każda inna kontrolka w formularzu.

## <a name="add-a-component-to-a-windows-form"></a>Dodawanie składnika do formularza systemu Windows

1. Otwórz formularz w programie Visual Studio. Aby uzyskać szczegółowe informacje [, zobacz How to: Wyświetl Windows Forms w projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. W **przyborniku**kliknij składnik i przeciągnij go do formularza.

     Składnik zostanie wyświetlony na pasku składnika.

Ponadto składniki mogą być dodawane do formularza w czasie wykonywania. Jest to typowy scenariusz, szczególnie ze względu na to, że składniki nie mają wyrażenia wizualnego, w przeciwieństwie do kontrolek, które mają interfejs użytkownika. W poniższym <xref:System.Windows.Forms.Timer> przykładzie składnik jest dodawany w czasie wykonywania. (Należy zauważyć, że program Visual Studio zawiera szereg różnych czasomierzy; w tym przypadku należy użyć <xref:System.Windows.Forms.Timer> składnika Windows Forms. Aby uzyskać więcej informacji na temat różnych czasomierzy w programie Visual Studio, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)

> [!CAUTION]
> Składniki często mają właściwości specyficzne dla kontrolki, które muszą być ustawione, aby składnik działał efektywnie. W przypadku <xref:System.Windows.Forms.Timer> składnika poniżej ustawia się `Interval` właściwość. Należy pamiętać, że podczas dodawania składników do projektu ustawiane są właściwości niezbędne dla tego składnika.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Programistyczne Dodawanie składnika do formularza systemu Windows

1. Utwórz wystąpienie <xref:System.Windows.Forms.Timer> klasy w kodzie.

2. Ustaw właściwość `Interval` , aby określić czas między taktami czasomierza.

3. Skonfiguruj inne niezbędne właściwości składnika.

     Poniższy kod przedstawia tworzenie elementu <xref:System.Windows.Forms.Timer> `Interval` z zestawem właściwości.

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do złośliwego elementu UserControl. Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Instrukcje: Dodaj kontrolki ActiveX do Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Umieszczanie kontrolek na formularzach Windows Forms](putting-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
