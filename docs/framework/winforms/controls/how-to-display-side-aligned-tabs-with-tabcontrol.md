---
title: 'Porady: wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Porady: wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl
<xref:System.Windows.Forms.TabControl.Alignment%2A> Właściwość <xref:System.Windows.Forms.TabControl> obsługuje wyświetlanie kart pionie (wzdłuż lewej lub prawej krawędzi formantu), w przeciwieństwie do poziomo (za pośrednictwem góry lub u dołu formantu). Domyślnie ta wyświetlania pionowego powoduje niską użytkowników, ponieważ <xref:System.Windows.Forms.TabPage.Text%2A> właściwość <xref:System.Windows.Forms.TabPage> obiektu nie są wyświetlane na karcie podczas style wizualne są włączone. Istnieje również bezpośrednim sposobem kontrolować kierunek tekstu w karcie. Można użyć właściciela Rysowanie w <xref:System.Windows.Forms.TabControl> aby poprawić działanie tej funkcji.  
  
 Poniższa procedura przedstawia sposób renderowania wyrównany karty tekstem kartę systemem od lewej do prawej, korzystając z funkcji "rysowania przez właściciela".  
  
### <a name="to-display-right-aligned-tabs"></a>Aby wyświetlić karty wyrównany do prawej  
  
1.  Dodaj <xref:System.Windows.Forms.TabControl> do formularza.  
  
2.  Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwości <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Ustaw <xref:System.Windows.Forms.TabControl.SizeMode%2A> właściwości <xref:System.Windows.Forms.TabSizeMode.Fixed>, tak aby wszystkie karty są tej samej szerokości.  
  
4.  Ustaw <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwości preferowany stały rozmiar kart. Należy pamiętać, że <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwości zachowuje się tak, jakby były karty w górnej części, chociaż są wyrównane do lewej. W związku z tym w celu karty szersze, należy zmienić <xref:System.Drawing.Size.Height%2A> właściwości, oraz w celu zapewnienia ich wyższe, należy zmienić <xref:System.Drawing.Size.Width%2A> właściwości.  
  
     Aby uzyskać najlepsze wyniki w poniższym przykładzie kodu, należy ustawić <xref:System.Drawing.Size.Width%2A> kart do 25 i <xref:System.Drawing.Size.Height%2A> do 100.  
  
5.  Ustaw <xref:System.Windows.Forms.TabControl.DrawMode%2A> właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Definiowanie procedury obsługi dla <xref:System.Windows.Forms.TabControl.DrawItem> zdarzenie <xref:System.Windows.Forms.TabControl> która renderuje tekstu od lewej do prawej.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [TabControl, kontrolka](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
