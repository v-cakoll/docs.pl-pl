---
title: 'Porady: tworzenie warstw obiektów na formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: d67d9b204c316dce5f3818496d791ed4c1b352f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875973"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Porady: tworzenie warstw obiektów na formularzach systemu Windows
Podczas tworzenia interfejsu użytkownika złożonych lub praca wielu dokumentów (MDI) interfejsu często warto warstwy kontroli i formularze podrzędne, aby utworzyć bardziej złożone interfejsy użytkownika (UI). Aby przenieść i śledzenie kontrolek i systemu windows w ramach grupy, manipulować ich porządek osi z. *Porządek* jest warstwy visual kontrolek w formularzu wzdłuż osi z formularza (na głębokości). Okno w górnej części porządek nakłada się na inne okna. Inne okna nakładać się na okna w dolnej części porządku osi z.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-layer-controls-at-design-time"></a>Warstwa kontrolek w czasie projektowania  
  
1.  Zaznacz kontrolkę, którą chcesz warstwy.  
  
2.  Na **Format** menu wskaż **kolejności**, a następnie kliknij przycisk **Przesuń na wierzch** lub **Przesuń na spód**.  
  
### <a name="to-layer-controls-programmatically"></a>Aby programowo warstwy formantów  
  
-   Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> metody do manipulowania porządek kontrolki.  
  
     Na przykład jeśli <xref:System.Windows.Forms.TextBox> kontroli `txtFirstName`, jest poniżej innej kontrolki, a chcesz ma go na początku, użyj następującego kodu:  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Formularze Windows obsługuje *zawieranie kontrolek*. Zawieranie kontrolek obejmuje umieszczenie kontrolki w ramach zawierający kontrolki, takie jak liczba <xref:System.Windows.Forms.RadioButton> kontrolki w ramach <xref:System.Windows.Forms.GroupBox> kontroli. Można następnie warstwy kontrolek w kontrolce zawierającego. Przesunięcie pole grupy przenosi, formanty, ponieważ są zawarte wewnątrz niego.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
