---
title: Zmień wygląd elementu TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746612"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows
Można zmienić wygląd kart w Windows Forms przy użyciu właściwości <xref:System.Windows.Forms.TabControl> i <xref:System.Windows.Forms.TabPage> obiektów, które tworzą poszczególne karty w kontrolce. Ustawiając te właściwości, można wyświetlać obrazy na kartach, wyświetlać tabulatory w pionie zamiast w poziomie, wyświetlać wiele wierszy kart i programowo włączać lub wyłączać karty.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Aby wyświetlić ikonę na etykiecie części karty  
  
1. Dodaj kontrolkę <xref:System.Windows.Forms.ImageList> do formularza.  
  
2. Dodaj obrazy do listy obrazów.  
  
     Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Ustaw właściwość <xref:System.Windows.Forms.TabControl.ImageList%2A> <xref:System.Windows.Forms.TabControl> na kontrolkę <xref:System.Windows.Forms.ImageList>.  
  
4. Ustaw właściwość <xref:System.Windows.Forms.TabPage.ImageIndex%2A> <xref:System.Windows.Forms.TabPage> na indeks odpowiedniego obrazu na liście.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Aby utworzyć wiele wierszy kart  
  
1. Dodaj liczbę żądanych stron kart.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.TabControl.Multiline%2A> <xref:System.Windows.Forms.TabControl> na `true`.  
  
3. Jeśli karty nie pojawiają się jeszcze w wielu wierszach, ustaw właściwość <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.TabControl> na węższe niż wszystkie karty.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Aby rozmieścić karty po stronie kontrolki  
  
- Ustaw właściwość <xref:System.Windows.Forms.TabControl.Alignment%2A> <xref:System.Windows.Forms.TabControl> na <xref:System.Windows.Forms.TabAlignment.Left> lub <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Aby programowo włączyć lub wyłączyć wszystkie kontrolki na karcie  
  
1. Ustaw właściwość <xref:System.Windows.Forms.TabPage.Enabled%2A> <xref:System.Windows.Forms.TabPage> na `true` lub `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Aby wyświetlić karty jako przyciski  
  
- Ustaw właściwość <xref:System.Windows.Forms.TabControl.Appearance%2A> <xref:System.Windows.Forms.TabControl> na <xref:System.Windows.Forms.TabAppearance.Buttons> lub <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Zobacz także

- [TabControl, kontrolka](tabcontrol-control-windows-forms.md)
- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: wyłączanie kart](how-to-disable-tab-pages.md)
- [Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
