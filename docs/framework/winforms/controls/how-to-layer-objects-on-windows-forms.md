---
title: 'Instrukcje: tworzenie warstw obiektów na formularzach systemu Windows'
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
ms.openlocfilehash: 8d0abbf0f71ac176d17261a0ae863938c575bdaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941079"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Instrukcje: tworzenie warstw obiektów na formularzach systemu Windows
Podczas tworzenia interfejsu użytkownika złożonych lub praca wielu dokumentów (MDI) interfejsu często warto warstwy kontroli i formularze podrzędne, aby utworzyć bardziej złożone interfejsy użytkownika (UI). Aby przenieść i śledzenie kontrolek i systemu windows w ramach grupy, manipulować ich porządek osi z. *Porządek* jest warstwy visual kontrolek w formularzu wzdłuż osi z formularza (na głębokości). Okno w górnej części porządek nakłada się na inne okna. Inne okna nakładać się na okna w dolnej części porządku osi z.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-layer-controls-at-design-time"></a>Warstwa kontrolek w czasie projektowania  
  
1. Zaznacz kontrolkę, którą chcesz warstwy.  
  
2. Na **Format** menu wskaż **kolejności**, a następnie kliknij przycisk **Przesuń na wierzch** lub **Przesuń na spód**.  
  
### <a name="to-layer-controls-programmatically"></a>Aby programowo warstwy formantów  
  
- Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> metody do manipulowania porządek kontrolki.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
