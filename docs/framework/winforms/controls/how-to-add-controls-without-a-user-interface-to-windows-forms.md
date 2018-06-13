---
title: 'Porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows'
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
ms.openlocfilehash: 0a3e9ab5a048e085b192ffc0eb796caae1e58efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529486"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows
Niewizualne kontrolki (lub składnik) zapewnia funkcje do aplikacji. W odróżnieniu od innych kontrolek składników nie udostępniają interfejsu użytkownika dla użytkownika i w związku z tym nie trzeba będzie wyświetlany na powierzchni projektanta formularzy systemu Windows. Gdy składnik zostanie dodany do formularza, Projektant formularzy systemu Windows wyświetla o zmiennym rozmiarze na pasku w dolnej części formularza, w którym są wyświetlane wszystkie składniki. Po dodaniu formantu do składnika na pasku zadań, można wybrać składnika i ustawienia swoich właściwości, jak w przypadku innych formantu w formularzu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Aby dodać składnik do formularza systemu Windows  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, kliknij i przeciągnij go do formularza.  
  
     Składnik zostanie wyświetlona na pasku składnika.  
  
 Ponadto składniki można dodać do formularza w czasie wykonywania. Jest to typowy scenariusz, szczególnie, ponieważ składniki nie ma wyrażenia visual, w przeciwieństwie do formantów interfejsu użytkownika. W poniższym przykładzie <xref:System.Windows.Forms.Timer> dodawania składnika w czasie wykonywania. (Należy pamiętać, że program Visual Studio zawiera szereg różnych czasomierze; w takim przypadku należy użyć formularzy systemu Windows <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji o różnych czasomierze w programie Visual Studio, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Składniki często mają właściwości specyficzne dla kontroli, które muszą być ustawione dla składnika efektywnie działać. W przypadku liczby <xref:System.Windows.Forms.Timer> poniższego składnika, ustawić `Interval` właściwości. Pamiętaj, podczas dodawania składników do projektu, ustawienie właściwości wymagane dla tego składnika.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Aby programowo Dodaj składnik do formularza systemu Windows  
  
1.  Utwórz wystąpienie <xref:System.Windows.Forms.Timer> klasy w kodzie.  
  
2.  Ustaw `Interval` właściwości w celu określenia czasu między taktami czasomierza.  
  
3.  Skonfiguruj inne wymagane właściwości dla składnika.  
  
     Poniższy kod przedstawia tworzenie <xref:System.Windows.Forms.Timer> z jego `Interval` zestawu właściwości.  
  
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
    >  Na komputerze lokalnym zagrożenie bezpieczeństwa w sieci może udostępniać za pomocą odwołań do elementu UserControl złośliwe. Tylko będzie to problemem w przypadku złośliwe osoby tworzenie kontrolkę niestandardową szkodliwy, następuje można przez pomyłkę dodanie go do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Instrukcje: dodawanie kontrolek ActiveX do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Instrukcje: kopiowanie kontrolek pomiędzy formularzami Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Umieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
