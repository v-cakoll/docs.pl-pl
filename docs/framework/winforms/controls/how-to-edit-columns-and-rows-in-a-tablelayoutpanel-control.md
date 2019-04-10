---
title: 'Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: eb194052ecd78d585f251789730a1f9855c509d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201965"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel
Można użyć edytora kolekcji <xref:System.Windows.Forms.TableLayoutPanel> kontrolę, wywoływana **Style kolumn i wierszy** okno dialogowe Edytuj wiersze i kolumny kontrolki.  
  
> [!NOTE]
>  Jeśli chcesz, aby formant ma obejmować wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu. Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Aby Wyrównaj formant w komórce lub jeśli chcesz rozciągnąć formant w komórce, należy użyć formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości. Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-edit-rows-and-columns"></a>Aby edytować wierszy i kolumn  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Kliknij przycisk <xref:System.Windows.Forms.TableLayoutPanel> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Edytuj wiersze i kolumny** otworzyć  **Style kolumn i wierszy** okno dialogowe. Możesz również kliknąć prawym przyciskiem myszy na <xref:System.Windows.Forms.TableLayoutPanel> sterowania i wybierz **Edytuj wiersze i kolumny** z menu skrótów.  
  
3.  Aby dodać lub usunąć kolumny, zaznacz **kolumn** z **typ elementu członkowskiego** pole listy rozwijanej.  
  
4.  Aby dodać lub usunąć wiersze, wybierz pozycję **wierszy** z **typ elementu członkowskiego** pole listy rozwijanej.  
  
5.  Kliknij przycisk **Dodaj** przycisk, aby dodać wiersz lub kolumnę do końca **elementu członkowskiego** listy.  
  
6.  Kliknij przycisk **Wstaw** przycisk, aby dodać wiersz lub kolumnę przed aktualnie wybranego elementu na liście.  
  
7.  W przypadku dodawania wierszy lub kolumn, wybierz **typu rozmiaru** dla nowego wiersza lub kolumny. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.  
  
8.  Aby usunąć wiersz lub kolumnę, kliknij **Usuń** przycisk, aby usunąć aktualnie wybranego elementu w **elementu członkowskiego** listy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel — kontrolka](tablelayoutpanel-control-windows-forms.md)
