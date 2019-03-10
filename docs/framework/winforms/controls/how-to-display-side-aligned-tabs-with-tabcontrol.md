---
title: 'Instrukcje: Wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: 8715cb1a1f0d5795afc4003afcecdb3fb89912c3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705193"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Instrukcje: Wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl
<xref:System.Windows.Forms.TabControl.Alignment%2A> Właściwość <xref:System.Windows.Forms.TabControl> obsługuje wyświetlanie kart w pionie (wzdłuż lewej lub prawej krawędzi formantu), w przeciwieństwie do poziomo (wzdłuż górnej i dolnej części kontrolki). Domyślnie ta pionowe wyświetlanie elementu powoduje niską komfortu ponieważ <xref:System.Windows.Forms.TabPage.Text%2A> właściwość <xref:System.Windows.Forms.TabPage> obiektu nie jest wyświetlane w karcie po włączeniu funkcji stylów wizualnych. Istnieje również ma bezpośredniego sposobu, aby kontrolować kierunek tekstu na karcie. Możesz użyć właściciela rysować na <xref:System.Windows.Forms.TabControl> się udoskonalić to środowisko pracy.  
  
 Poniższa procedura przedstawia sposób renderowania kart wyrównany do prawej, z tekstem kartę uruchomione od lewej do prawej, korzystając z funkcji "draw właściciela".  
  
### <a name="to-display-right-aligned-tabs"></a>Aby wyświetlić karty wyrównany do prawej  
  
1.  Dodaj <xref:System.Windows.Forms.TabControl> do formularza.  
  
2.  Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwość <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Ustaw <xref:System.Windows.Forms.TabControl.SizeMode%2A> właściwości <xref:System.Windows.Forms.TabSizeMode.Fixed>, dzięki czemu wszystkie karty są taką samą szerokość.  
  
4.  Ustaw <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwość preferowany ustalony rozmiar dla karty. Należy pamiętać, że <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwość zachowuje się tak, jakby karty znajdowały się na górze, chociaż są wyrównane do prawej. W rezultacie, w celu szerszego karty, należy zmienić <xref:System.Drawing.Size.Height%2A> właściwości, aby były wyższe, musisz zmienić <xref:System.Drawing.Size.Width%2A> właściwości.  
  
     Najlepsze wyniki w poniższym przykładzie kodu, można ustawić <xref:System.Drawing.Size.Width%2A> kart do 25 i <xref:System.Drawing.Size.Height%2A> do 100.  
  
5.  Ustaw <xref:System.Windows.Forms.TabControl.DrawMode%2A> właściwość <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Definiowanie procedury obsługi dla <xref:System.Windows.Forms.TabControl.DrawItem> zdarzenia <xref:System.Windows.Forms.TabControl> , powoduje wyświetlenie tekstu od lewej do prawej.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [TabControl, kontrolka](tabcontrol-control-windows-forms.md)
