---
title: 'Instrukcje: zmienianie wyglądu składnika TabControl formularzy systemu Windows'
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
ms.openlocfilehash: 05df05a52914f27a4b62cf7bde92e5d942b6ea06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331341"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Instrukcje: zmienianie wyglądu składnika TabControl formularzy systemu Windows
Można zmienić wygląd karty w formularzach Windows Forms za pomocą właściwości <xref:System.Windows.Forms.TabControl> i <xref:System.Windows.Forms.TabPage> obiektów, które składają się na poszczególnych kartach formantu. Przez ustawienie tych właściwości, można wyświetlanie obrazów na kartach, wyświetlanie kart w pionie zamiast w poziomie, wyświetlić wiele wierszy kart i włączyć lub wyłączyć karty programowo.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Aby wyświetlić ikonę na części etykieta karty  
  
1. Dodaj <xref:System.Windows.Forms.ImageList> formantu do formularza.  
  
2. Dodawanie obrazów do listy obrazów.  
  
     Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Ustaw <xref:System.Windows.Forms.TabControl.ImageList%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.ImageList> kontroli.  
  
4. Ustaw <xref:System.Windows.Forms.TabPage.ImageIndex%2A> właściwość <xref:System.Windows.Forms.TabPage> do indeksu odpowiedniego obrazu na liście.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Aby utworzyć wiele wierszy kart  
  
1. Dodaj numer strony kart, które chcesz.  
  
2. Ustaw <xref:System.Windows.Forms.TabControl.Multiline%2A> właściwość <xref:System.Windows.Forms.TabControl> do `true`.  
  
3. Jeśli karty nie ma już w wielu wierszach, ustaw <xref:System.Windows.Forms.Control.Width%2A> właściwość <xref:System.Windows.Forms.TabControl> być mniejsza niż wszystkie karty.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Aby rozmieścić karty boku kontrolki  
  
-   Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAlignment.Left> lub <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Aby programowo włączyć lub wyłączyć wszystkie kontrolki na karcie  
  
1. Ustaw <xref:System.Windows.Forms.TabPage.Enabled%2A> właściwość <xref:System.Windows.Forms.TabPage> do `true` lub `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Aby wyświetlić karty przyciski  
  
-   Ustaw <xref:System.Windows.Forms.TabControl.Appearance%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAppearance.Buttons> lub <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Zobacz także

- [TabControl, kontrolka](tabcontrol-control-windows-forms.md)
- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: Wyłączanie kart](how-to-disable-tab-pages.md)
- [Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
