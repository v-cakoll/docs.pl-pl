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
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Porady: tworzenie warstw obiektów na formularzach systemu Windows
Tworzenie interfejsu użytkownika złożonych lub praca wielu dokumentów (MDI) interfejsu, często można warstwy zarówno kontroli, jak i formularze podrzędne, aby utworzyć bardziej złożoną interfejsy użytkownika (UI). Aby przenieść i śledzenie kontrolek i systemu windows w ramach grupy, manipulować ich porządek osi z. *Porządek osi* jest visual warstwy formantów w formularzu wzdłuż osi z formularza (głębokość). Okno w górnej części porządek nakłada się na wszystkich innych okien. Wszystkie inne okna nakładać się na okna w dolnej części porządek osi z.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>Do warstwy formantów w czasie projektowania  
  
1.  Wybierz kontrolkę, która ma być warstwy.  
  
2.  Na **Format** menu wskaż **kolejności**, a następnie kliknij przycisk **Przesuń na wierzch** lub **Wyślij ponownie**.  
  
### <a name="to-layer-controls-programmatically"></a>Aby programowo warstwy formantów  
  
-   Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> metoda manipulowania porządek osi z kontrolki.  
  
     Na przykład jeśli <xref:System.Windows.Forms.TextBox> kontroli, `txtFirstName`, jest underneath inny formant i chcesz ma go w górnej części, użyj następującego kodu:  
  
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
>  Formularze systemu Windows obsługuje *zawieranie kontrolek*. Zawierania formantów obejmuje umieszczenie kontrolki w formancie zawierającego, takie jak liczba <xref:System.Windows.Forms.RadioButton> steruje w obrębie <xref:System.Windows.Forms.GroupBox> formantu. Następnie można warstwy kontrolki wewnątrz formantu zawierającego. Przenoszenie pole grupy przenosi również formanty, ponieważ są one zawarte w nim.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
