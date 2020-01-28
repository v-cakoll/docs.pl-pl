---
title: Formatowanie danych w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743986"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatowanie danych w formancie DataGridView formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> zapewnia automatyczną konwersję między wartościami komórek a typami danych, które są wyświetlane w kolumnach nadrzędnych. Kolumny pól tekstowych, na przykład wyświetlanie reprezentacji ciągów wartości daty, godziny, liczby i wyliczenia oraz konwertowanie wartości ciągów wprowadzonych przez użytkownika na typy wymagane przez magazyn danych.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatowanie przy użyciu klasy DataGridViewCellStyle  
 Formant <xref:System.Windows.Forms.DataGridView> zapewnia podstawowe formatowanie danych wartości komórek za pomocą klasy <xref:System.Windows.Forms.DataGridViewCellStyle>. Właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> można użyć do sformatowania wartości daty, godziny, liczby i wyliczenia dla bieżącej kultury domyślnej przy użyciu specyfikatorów formatu opisanych w [typach formatowania](../../../standard/base-types/formatting-types.md). Możesz również sformatować te wartości dla określonych kultur przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>. Określony format służy zarówno do wyświetlania danych, jak i do analizowania danych wprowadzonych przez użytkownika w określonym formacie.  
  
 Klasa <xref:System.Windows.Forms.DataGridViewCellStyle> zapewnia dodatkowe właściwości formatowania dla WordWrap, wyrównania tekstu i niestandardowego wyświetlania wartości null baz danych. Aby uzyskać więcej informacji, zobacz [How to: format data w kontrolce DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatowanie przy użyciu zdarzenia CellFormatting  
 Jeśli podstawowe formatowanie nie spełnia Twoich potrzeb, możesz podać niestandardowe formatowanie danych w programie obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> przekazanie do procedury obsługi ma właściwość <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, która początkowo zawiera wartość komórki. Zwykle ta wartość jest automatycznie konwertowana na typ wyświetlania. Aby przekonwertować wartość samodzielnie, ustaw właściwość <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> na wartość typu wyświetlanego.  
  
> [!NOTE]
> Jeśli w komórce obowiązuje ciąg formatu, zastępuje on zmianę wartości właściwości <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, chyba że właściwość <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> zostanie ustawiona na `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie jest również przydatne, gdy chcesz ustawić właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> dla poszczególnych komórek na podstawie ich wartości. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Jeśli domyślna Analiza wartości określonych przez użytkownika nie spełnia Twoich potrzeb, można obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellParsing> formantu <xref:System.Windows.Forms.DataGridView>, aby zapewnić analizę niestandardową.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: formatowanie danych w kontrolce DataGridView formularzy Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
