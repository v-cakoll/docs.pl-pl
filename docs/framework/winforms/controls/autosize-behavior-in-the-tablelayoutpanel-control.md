---
title: Zachowanie AutoSize w formancie TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Zachowanie AutoSize w formancie TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>AutoSize różne zachowania  
 <xref:System.Windows.Forms.TableLayoutPanel> Sterowanie obsługuje zachowanie automatycznej zmiany rozmiaru w następujący sposób:  
  
-   Za pomocą <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości;  
  
-   Za pomocą <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.TableLayoutPanel> formantu Style kolumn i wierszy.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>AutoSize właściwość Style kolumn i wierszy  
 W poniższej tabeli opisano interakcje między <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości i <xref:System.Windows.Forms.TableLayoutPanel> formantu Style kolumn i wierszy.  
  
|Ustawienia automatycznego dopasowania rozmiaru|Styl interakcji|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> Formant przechodzi od lewej do prawej i przydziela miejsce dla kolumny lub wiersza lub w następującej kolejności.<br /><br /> 1.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.Absolute>, liczbę pikseli określone przez <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> został przydzielony.<br />2.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.AutoSize>, zwracane przez formant podrzędny w pikselach <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody został przydzielony.<br />3.  Po miejsca dla wszystkich <xref:System.Windows.Forms.SizeType.Absolute> i <xref:System.Windows.Forms.SizeType.AutoSize> kolumn lub wierszy jest przydzielona, wszystkie kolumny lub wiersze z <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> ustawioną <xref:System.Windows.Forms.SizeType.Percent> służą do proporcjonalnie przydzielić pozostałej ilości wolnego miejsca|  
|`true`|Podobnie jak poprzednie interakcji, z wyjątkiem tego, który <xref:System.Windows.Forms.SizeType.Percent> kolumn lub wierszy uzyskać aspekt automatycznej zmiany rozmiaru.<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozszerza kolumny lub wiersza, aby utworzyć odpowiednią ilością wolnego miejsca, aby nie kolumny lub wiersza z <xref:System.Windows.Forms.SizeType.Percent> stylów klipy jego zawartość. <xref:System.Windows.Forms.TableLayoutPanel> Kontroli przydziela nowe miejsce proporcjonalnie zgodnie z <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
