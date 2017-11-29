---
title: Formatowanie danych w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e716dc74946ac6f18ab82c6834518f0bd6bbea76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatowanie danych w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrola zapewnia automatycznej konwersji między wartości komórek i typy danych, które są wyświetlane kolumny nadrzędne. Tekst pola kolumny, na przykład wyświetlić reprezentacji ciągu daty, godziny, liczbę i wartości wyliczenia i konwertowanie wartości ciągu wprowadzonych przez użytkownika typów wymaganych przez Magazyn danych.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatowanie w klasie DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia podstawowe dane formatowania wartości komórki za pomocą <xref:System.Windows.Forms.DataGridViewCellStyle> klasy. Można użyć <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwości formatu daty, godziny, numer i wyliczenia wartości dla bieżącej kultury domyślnej używanie specyfikatorów formatu opisanego w [typy formatowania](../../../../docs/standard/base-types/formatting-types.md). Można również sformatować tych wartości dla określonej kultury przy użyciu <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> właściwości. Określony format jest używany do wyświetlania danych i analizy danych wprowadzonych przez użytkownika w określonym formacie.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Klasa udostępnia dodatkowe właściwości formatowania dla zawijania tekstu, wyrównanie tekstu i wyświetlanie niestandardowe wartości null bazy danych. Aby uzyskać więcej informacji, zobacz [porady: formatowanie danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatowanie ze zdarzeniem CellFormatting  
 Jeśli podstawowe formatowanie nie spełnia Twoje potrzeby, możesz podać dane niestandardowe formatowanie programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> Przekazywane do programu obsługi ma <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> właściwość, która początkowo zawiera wartość komórki. Zwykle ta wartość jest automatycznie konwertowany do typu wyświetlania. Aby przekonwertować wartość samodzielnie, ustaw <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> właściwości na wartość typu wyświetlania.  
  
> [!NOTE]
>  Jeśli ciąg formatu jest włączone dla komórki, zastępuje on zmiana <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> wartość właściwości, chyba że ustawisz <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> właściwości `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> Zdarzenie jest również przydatne, jeśli chcesz ustawić <xref:System.Windows.Forms.DataGridViewCellStyle> właściwości dla pojedynczych komórek na podstawie ich wartości. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Jeśli domyślne podczas analizowania wartości określonych przez użytkownika nie spełnia Twoje potrzeby, może obsługiwać <xref:System.Windows.Forms.DataGridView.CellParsing> zdarzenie <xref:System.Windows.Forms.DataGridView> formantu, aby zapewnić niestandardowych podczas analizowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Wyświetlanie danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Porady: formatowanie danych w systemie Windows do formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
