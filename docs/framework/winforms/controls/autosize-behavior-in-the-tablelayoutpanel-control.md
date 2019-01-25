---
title: Zachowanie AutoSize w formancie TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: fdaa34ace1f5322c9296d2520d275fdf3f176048
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515735"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Zachowanie AutoSize w formancie TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>AutoSize różne zachowania  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontrolka obsługuje automatyczne dopasowanie rozmiaru w następujący sposób:  
  
-   Za pomocą <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości  
  
-   Za pomocą <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.TableLayoutPanel> Style kolumn i wierszy dla formantu.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>AutoSize właściwość o wierszy i kolumn style  
 W poniższej tabeli opisano interakcje między <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości i <xref:System.Windows.Forms.TableLayoutPanel> Style kolumn i wierszy dla formantu.  
  
|Ustawienie AutoSize|Styl interakcji|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozpoczynające się od lewej do prawej i przydziela miejsce dla kolumny lub wiersza lub w następującej kolejności.<br /><br /> 1.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.Absolute>, liczbę pikseli, określony przez <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> jest przydzielony.<br />2.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.AutoSize>, zwracany przez kontrolę rodzicielską w pikselach <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda została przydzielona.<br />3.  Po miejsce dla wszystkich <xref:System.Windows.Forms.SizeType.Absolute> i <xref:System.Windows.Forms.SizeType.AutoSize> wierszy lub kolumn jest przydzielany, wszystkie kolumny lub wiersze z <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> równa <xref:System.Windows.Forms.SizeType.Percent> są używane do przydzielenia proporcjonalnie pozostałe wolne miejsce|  
|`true`|Podobny do poprzedniego interakcji, z wyjątkiem który <xref:System.Windows.Forms.SizeType.Percent> kolumny lub wiersze uzyskania aspektem automatycznej zmiany rozmiaru.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozwija kolumny lub wiersza, aby utworzyć odpowiednią ilością wolnego miejsca, tak, aby nie kolumny lub wiersza z <xref:System.Windows.Forms.SizeType.Percent> stylów przycina jego zawartość. <xref:System.Windows.Forms.TableLayoutPanel> Kontroli przydziela nowe miejsce proporcjonalnie na podstawie położenia <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> właściwości.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
