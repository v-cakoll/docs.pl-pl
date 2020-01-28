---
title: Zastosuj atrybuty w kontrolkach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741496"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Porady: stosowanie atrybutów w formantach formularzy systemu Windows
Aby opracować składniki i formanty współdziałające prawidłowo ze środowiskiem projektowym i działać prawidłowo w czasie wykonywania, należy prawidłowo zastosować atrybuty do klas i elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak używać kilku atrybutów w kontrolce niestandardowej. Kontrolka pokazuje prostą funkcję rejestrowania. Gdy formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w kontrolce <xref:System.Windows.Forms.DataGridView>. Jeśli wartość przekroczy wartość określoną przez właściwość `Threshold`, zostanie zgłoszone zdarzenie `ThresholdExceeded`.  
  
 `AttributesDemoControl` rejestruje wartości z klasą `LogEntry`. Klasa `LogEntry` jest klasą szablonu, co oznacza, że jest sparametryzowane dla typu, który rejestruje. Na przykład jeśli `AttributesDemoControl` rejestruje wartości typu `float`, każde wystąpienie `LogEntry` jest zadeklarowane i używane w następujący sposób.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Ponieważ `LogEntry` jest sparametryzowane przez dowolny typ, musi używać odbicia do operowania na typie parametru. Aby funkcja progu działała, typ parametru `T` musi implementować interfejs <xref:System.IComparable>.  
  
 Formularz, który hostuje `AttributesDemoControl` wysyła zapytanie do licznika wydajności okresowo. Każda wartość jest pakowana w `LogEntry` odpowiedniego typu i dodawane do <xref:System.Windows.Forms.BindingSource>formularza. `AttributesDemoControl` otrzymuje wartość za pomocą powiązania danych i wyświetla wartość w kontrolce <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Pierwszy przykład kodu jest implementacją `AttributesDemoControl`. Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atrybuty na poziomie klasy  
 Niektóre atrybuty są stosowane na poziomie klasy. Poniższy przykład kodu pokazuje atrybuty, które są powszechnie stosowane do formantu Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter — atrybut  
 <xref:System.ComponentModel.TypeConverterAttribute> jest innym powszechnie używanym atrybutem na poziomie klasy. Poniższy przykład kodu pokazuje jego użycie dla klasy `LogEntry`. W tym przykładzie przedstawiono również implementację <xref:System.ComponentModel.TypeConverter> typu `LogEntry` o nazwie `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atrybuty na poziomie elementu członkowskiego  
 Niektóre atrybuty są stosowane na poziomie elementu członkowskiego. Poniższe przykłady kodu pokazują pewne atrybuty, które są powszechnie stosowane do właściwości kontrolek Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue — atrybut  
 Poniższy przykład ilustruje <xref:System.ComponentModel.AmbientValueAttribute> i pokazuje kod, który obsługuje interakcje ze środowiskiem projektowym. Ta interakcja jest nazywana *Ambience*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atrybuty wiązania danych  
 W poniższych przykładach przedstawiono implementację złożonego powiązania danych. <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>na poziomie klasy, pokazane wcześniej, określa `DataSource` i `DataMember` właściwości, które mają być używane do wiązania danych. <xref:System.ComponentModel.AttributeProviderAttribute> określa typ, do którego zostanie powiązana właściwość `DataSource`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Formularz, który hostuje `AttributesDemoControl` wymaga odwołania do zestawu `AttributesDemoControl` w celu skompilowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)
- [Instrukcje: serializacja kolekcji typów standardowych przy użyciu za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
