---
title: 'Instrukcje: stosowanie atrybutów w kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922781"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Instrukcje: stosowanie atrybutów w kontrolkach formularzy systemu Windows
Aby opracować składniki i formanty współdziałające prawidłowo ze środowiskiem projektowym i działać prawidłowo w czasie wykonywania, należy prawidłowo zastosować atrybuty do klas i elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak używać kilku atrybutów w kontrolce niestandardowej. Kontrolka pokazuje prostą funkcję rejestrowania. Gdy formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> kontrolce. Jeśli wartość przekroczy wartość określoną przez `Threshold` Właściwość `ThresholdExceeded` , zdarzenie jest zgłaszane.  
  
 `AttributesDemoControl` Rejestruje wartości zklasą`LogEntry` . `LogEntry` Klasa jest klasą szablonu, co oznacza, że jest sparametryzowane dla typu, który rejestruje. Na przykład, jeśli `AttributesDemoControl` rejestruje wartości typu `float`, każde `LogEntry` wystąpienie jest zadeklarowane i używane w następujący sposób.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Ponieważ `LogEntry` jest sparametryzowane przez dowolny typ, musi używać odbicia do działania na typie parametru. Aby funkcja progu działała, typ `T` parametru musi <xref:System.IComparable> implementować interfejs.  
  
 Formularz, który `AttributesDemoControl` okresowo kieruje zapytania do licznika wydajności. Każda wartość jest opakowana `LogEntry` do odpowiedniego typu i dodawana do <xref:System.Windows.Forms.BindingSource>formularza. Odbiera wartość za pomocą powiązania danych i wyświetla wartość <xref:System.Windows.Forms.DataGridView> w kontrolce. `AttributesDemoControl`  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Pierwszym przykładem kodu jest `AttributesDemoControl` implementacja. Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atrybuty na poziomie klasy  
 Niektóre atrybuty są stosowane na poziomie klasy. Poniższy przykład kodu pokazuje atrybuty, które są powszechnie stosowane do formantu Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter — atrybut  
 <xref:System.ComponentModel.TypeConverterAttribute>jest innym powszechnie używanym atrybutem na poziomie klasy. Poniższy przykład kodu pokazuje jego użycie dla `LogEntry` klasy. Ten przykład pokazuje również implementację <xref:System.ComponentModel.TypeConverter> `LogEntry` dla typu o nazwie `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atrybuty na poziomie elementu członkowskiego  
 Niektóre atrybuty są stosowane na poziomie elementu członkowskiego. Poniższe przykłady kodu pokazują pewne atrybuty, które są powszechnie stosowane do właściwości kontrolek Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue — atrybut  
 Poniższy przykład demonstruje <xref:System.ComponentModel.AmbientValueAttribute> i pokazuje kod, który obsługuje interakcje ze środowiskiem projektowym. Ta interakcja jest nazywana *Ambience*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atrybuty wiązania danych  
 W poniższych przykładach przedstawiono implementację złożonego powiązania danych. Pokazany wcześniej poziom <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>klasy, `DataSource` określa właściwości i `DataMember` , które mają być używane do wiązania danych. Określa typ, do `DataSource` którego zostanie powiązana właściwość. <xref:System.ComponentModel.AttributeProviderAttribute>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Formularz `AttributesDemoControl` obsługujący wymaga odwołania `AttributesDemoControl` do zestawu, aby można było go skompilować.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)
- [Instrukcje: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
