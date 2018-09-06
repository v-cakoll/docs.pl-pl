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
ms.openlocfilehash: 9458fc7f3344a5692581485a0e5bd462e45551d9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731991"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows
Niewizualne kontrolki (lub składnika) zapewnia funkcje aplikacji. W przeciwieństwie do innych formantów składniki nie udostępniają interfejs użytkownika dla użytkownika i dlatego nie powinny być wyświetlane na powierzchni projektanta formularzy Windows. Po dodaniu składnika do formularza Windows Forms Designer przedstawia o zmiennych rozmiarach na pasku w dolnej części formularza, w którym są wyświetlane wszystkie składniki. Po dodaniu kontrolki do zasobnika składnika można wybrać składnik i ustaw jego właściwości, tak jak inne kontrolki, w formularzu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Aby dodać składnik do formularza Windows  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy Windows w Projektancie](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, kliknij składnik i przeciągnij go do formularza.  
  
     Składnik jest wyświetlana w zasobniku składnika.  
  
 Ponadto składniki można dodać do formularza w czasie wykonywania. To typowy scenariusz, szczególnie, ponieważ składniki nie mają visual wyrażenia, w przeciwieństwie do formantów, które mają interfejs użytkownika. W poniższym przykładzie <xref:System.Windows.Forms.Timer> składnik zostanie dodany w czasie wykonywania. (Należy pamiętać, że program Visual Studio zawiera szereg różnych czasomierzy; w przypadku używania formularzy Windows <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji na temat różnych czasomierzy w programie Visual Studio, zobacz [wprowadzenie do serwerowych czasomierzy](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Składniki często mają właściwości specyficzne dla kontrolki, które muszą być ustawione dla składnika działał efektywnie. W przypadku właściwości <xref:System.Windows.Forms.Timer> poniżej składnika, ustawić `Interval` właściwości. Pamiętaj, podczas dodawania składników do projektu, należy ustawić właściwości niezbędne do tego składnika.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Aby programowo dodać składnik do formularza Windows  
  
1.  Utwórz wystąpienie obiektu <xref:System.Windows.Forms.Timer> klasy w kodzie.  
  
2.  Ustaw `Interval` właściwości, aby ustalić czas między taktami czasomierza.  
  
3.  Skonfiguruj inne wymagane właściwości składnika.  
  
     Poniższy kod ilustruje tworzenie <xref:System.Windows.Forms.Timer> z jego `Interval` zestawu właściwości.  
  
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
    >  Na komputerze lokalnym to zagrożenie bezpieczeństwa, za pośrednictwem sieci może narazić, odwołując się do złośliwego elementu UserControl. Powinien to być jedynie kwestią w przypadku złośliwe osoby tworzącej szkodliwe kontrolka niestandardowa, a następnie przez Ciebie przez pomyłkę dodawania do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Instrukcje: dodawanie kontrolek ActiveX do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Instrukcje: kopiowanie kontrolek pomiędzy formularzami Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Umieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
