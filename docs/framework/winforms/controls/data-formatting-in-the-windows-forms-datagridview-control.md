---
title: Formatowanie danych w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969185"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Formatowanie danych w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrolka zapewnia automatyczną konwersję między wartościami komórek a typami danych, które są wyświetlane w kolumnach nadrzędnych. Kolumny pól tekstowych, na przykład wyświetlanie reprezentacji ciągów wartości daty, godziny, liczby i wyliczenia oraz konwertowanie wartości ciągów wprowadzonych przez użytkownika na typy wymagane przez magazyn danych.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Formatowanie przy użyciu klasy DataGridViewCellStyle  
 Kontrolka zapewnia podstawowe formatowanie danych wartości komórek <xref:System.Windows.Forms.DataGridViewCellStyle> za pomocą klasy. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Właściwości można użyć do sformatowania wartości daty, godziny, liczby i wyliczenia dla bieżącej kultury domyślnej przy użyciu specyfikatorów formatu opisanych w [typach formatowania](../../../standard/base-types/formatting-types.md). Możesz również sformatować te wartości dla określonych kultur przy użyciu <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> właściwości. Określony format służy zarówno do wyświetlania danych, jak i do analizowania danych wprowadzonych przez użytkownika w określonym formacie.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Klasa zapewnia dodatkowe właściwości formatowania dla WordWrap, wyrównania tekstu i niestandardowego wyświetlania wartości null baz danych. Aby uzyskać więcej informacji, zobacz [jak: Sformatuj dane w kontrolce](how-to-format-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.  
  
## <a name="formatting-with-the-cellformatting-event"></a>Formatowanie przy użyciu zdarzenia CellFormatting  
 Jeśli podstawowe formatowanie nie spełnia Twoich potrzeb, możesz podać niestandardowe formatowanie danych w programie obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenia. Przesłany do procedury obsługi <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> ma właściwość, która początkowo zawiera wartość komórki. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> Zwykle ta wartość jest automatycznie konwertowana na typ wyświetlania. Aby przekonwertować wartość samodzielnie, należy ustawić <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> właściwość na wartość typu wyświetlanego.  
  
> [!NOTE]
> Jeśli ciąg formatu jest obowiązujący dla komórki, zastępuje on zmianę <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> wartości właściwości, chyba że <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> właściwość jest ustawiona na `true`.  
  
 To zdarzenie jest również przydatne, gdy chcesz ustawić <xref:System.Windows.Forms.DataGridViewCellStyle> właściwości dla poszczególnych komórek na podstawie ich wartości. <xref:System.Windows.Forms.DataGridView.CellFormatting> Aby uzyskać więcej informacji, zobacz [jak: Dostosuj formatowanie danych w kontrolce](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.  
  
 Jeśli domyślna Analiza wartości określonych przez użytkownika nie spełnia Twoich potrzeb, można obsłużyć <xref:System.Windows.Forms.DataGridView.CellParsing> zdarzenie <xref:System.Windows.Forms.DataGridView> kontrolki, aby zapewnić niestandardową analizę.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Formatowanie danych w kontrolce DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
