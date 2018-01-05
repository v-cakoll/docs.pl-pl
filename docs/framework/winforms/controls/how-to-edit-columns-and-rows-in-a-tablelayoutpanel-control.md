---
title: "Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75b83a2d7475f1a01d80c82013dac519edc4de08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel
Za pomocą edytora kolekcji z <xref:System.Windows.Forms.TableLayoutPanel> formantu o nazwie **Style kolumn i wierszy** okno dialogowe, aby edytować wierszy i kolumn dla Twoich kontrolek.  
  
> [!NOTE]
>  Jeśli chcesz, aby formant ma obejmować wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Jeśli chcesz wyrównać formant w komórce lub jeśli chcesz rozciągnąć formant w komórce, użyj formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Aby edytować wierszy i kolumn  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Kliknij przycisk <xref:System.Windows.Forms.TableLayoutPanel> kontrolki symbolu tagu (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Edytuj wiersze i kolumny** otworzyć  **Style kolumn i wierszy** okno dialogowe. Możesz również kliknąć prawym przyciskiem myszy na <xref:System.Windows.Forms.TableLayoutPanel> sterowania i wybierz **Edytuj wiersze i kolumny** z menu skrótów.  
  
3.  Aby dodać lub usunąć kolumny, zaznacz **kolumn** z **typ elementu członkowskiego** pole listy rozwijanej.  
  
4.  Aby dodać lub usunąć wiersze, wybierz **wierszy** z **typ elementu członkowskiego** pole listy rozwijanej.  
  
5.  Kliknij przycisk **Dodaj** przycisk, aby dodać wiersz lub kolumnę do końca **elementu członkowskiego** listy.  
  
6.  Kliknij przycisk **Wstaw** przycisk, aby dodać wiersz lub kolumnę przed aktualnie wybrany element na liście.  
  
7.  Jeśli dodajesz wiersz lub kolumnę, wybierz **typu rozmiaru** nowy wiersz lub kolumnę. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.  
  
8.  Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** przycisk, aby usunąć element aktualnie zaznaczony w **elementu członkowskiego** listy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SizeType>  
 [TableLayoutPanel, kontrolka](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
