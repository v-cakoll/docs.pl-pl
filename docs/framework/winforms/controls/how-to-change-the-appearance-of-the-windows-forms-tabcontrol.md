---
title: 'Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows'
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
ms.openlocfilehash: 1ea2208229d790f69e517d55e2de5ee042bdfb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531043"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows
Można zmienić wygląd kart w formularzach systemu Windows za pomocą właściwości <xref:System.Windows.Forms.TabControl> i <xref:System.Windows.Forms.TabPage> obiektów, które składają się na poszczególnych kartach w formancie. Przez ustawienie tych właściwości, można wyświetlanie obrazów na kartach, wyświetlić karty w pionie zamiast w poziomie, wyświetlane wiele wierszy kart i włączyć lub wyłączyć karty programowo.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Aby wyświetlić ikony na części etykiety karty  
  
1.  Dodaj <xref:System.Windows.Forms.ImageList> sterowania do formularza.  
  
2.  Dodawanie obrazów do listy obrazów.  
  
     Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) i [porady: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Ustaw <xref:System.Windows.Forms.TabControl.ImageList%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.ImageList> formantu.  
  
4.  Ustaw <xref:System.Windows.Forms.TabPage.ImageIndex%2A> właściwość <xref:System.Windows.Forms.TabPage> do indeksu odpowiedniego obrazu na liście.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Aby utworzyć wiele wierszy kart  
  
1.  Dodaj liczba kart, które mają.  
  
2.  Ustaw <xref:System.Windows.Forms.TabControl.Multiline%2A> właściwość <xref:System.Windows.Forms.TabControl> do `true`.  
  
3.  Jeśli karty nie są już wyświetlane w wielu wierszach, ustaw <xref:System.Windows.Forms.Control.Width%2A> właściwość <xref:System.Windows.Forms.TabControl> być mniejsza niż wszystkich kart.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Aby zorganizować karty boku formantu  
  
-   Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAlignment.Left> lub <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Aby programowo włączyć lub wyłączyć wszystkie formanty na karcie  
  
1.  Ustaw <xref:System.Windows.Forms.TabPage.Enabled%2A> właściwość <xref:System.Windows.Forms.TabPage> do `true` lub `false`.  
  
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
  
-   Ustaw <xref:System.Windows.Forms.TabControl.Appearance%2A> właściwość <xref:System.Windows.Forms.TabControl> do <xref:System.Windows.Forms.TabAppearance.Buttons> lub <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Zobacz też  
 [TabControl, kontrolka](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl, kontrolka — omówienie](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie kontrolki do karty](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Instrukcje: wyłączanie kart](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
