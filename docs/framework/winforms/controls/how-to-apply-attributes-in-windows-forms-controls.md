---
title: 'Porady: stosowanie atrybutów w formantach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519604"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Porady: stosowanie atrybutów w formantach formularzy systemu Windows
Do tworzenia składników i formantów, które nawiązują prawidłową interakcję z środowiska projektowania i poprawnego wykonania w czasie wykonywania, należy poprawnie zastosować atrybutów do klas i składowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania kilka atrybutów w formancie niestandardowym. Kontrolka pokazuje prosty rejestrować. Gdy kontrolka jest powiązana ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> kontroli. Jeśli wartość przekracza wartość określoną przez `Threshold` właściwości `ThresholdExceeded` zdarzenie jest wywoływane.  
  
 `AttributesDemoControl` Dzienniki wartościami `LogEntry` klasy. `LogEntry` Klasa jest klasą szablonu, który oznacza, że jest ona parametryzowane na typ, który rejestruje. Na przykład jeśli `AttributesDemoControl` jest rejestrowanie wartości typu `float`, każdy `LogEntry` wystąpienie jest zadeklarowana i używane w następujący sposób.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Ponieważ `LogEntry` jest sparametryzowane według dowolnego typu go używać odbicia do działania na typ parametru. Dla funkcji próg do pracy z typem parametru `T` musi implementować <xref:System.IComparable> interfejsu.  
  
 Formularz, który jest hostem `AttributesDemoControl` okresowo wysyła zapytanie licznika wydajności. Każda wartość jest spakowany w `LogEntry` odpowiedniego typu i dodany do formularza <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Otrzymuje wartość za pomocą jego powiązania danych i wyświetla wartości w <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Pierwszy przykład kodu jest `AttributesDemoControl` implementacji. Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atrybuty klasy  
 Niektóre atrybuty są stosowane na poziomie klasy. Poniższy przykład kodu pokazuje atrybuty, które są często stosowane do formantu Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute> jest inny atrybut poziomie klasy często używane. Poniższy przykład kodu pokazuje jego stosowanie `LogEntry` klasy. W tym przykładzie przedstawiono również implementację <xref:System.ComponentModel.TypeConverter> dla `LogEntry` typu, o nazwie `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atrybuty na poziomie członka  
 Niektóre atrybuty są stosowane na poziomie elementu członkowskiego. W poniższych przykładach kodu pokazano niektóre atrybuty, które są często stosowane do właściwości kontrolek formularzy Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atrybut AmbientValue  
 W poniższym przykładzie pokazano <xref:System.ComponentModel.AmbientValueAttribute> i zawiera kod, który obsługuje wchodzi w interakcję z środowisko projektowania. Ta interakcja jest nazywany *otoczenie*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atrybuty wiązania danych  
 Poniższy przykład pokazuje implementację złożone powiązanie danych. Klasa poziomie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, jak pokazano wcześniej, określa `DataSource` i `DataMember` właściwości mają zostać użyte do wiązania danych. <xref:System.ComponentModel.AttributeProviderAttribute> Określa typ, do którego `DataSource` właściwość zostanie z nim powiązane.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Formularz, który jest hostem `AttributesDemoControl` wymaga odwołania do `AttributesDemoControl` zestawu w celu kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Atrybuty w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Instrukcje: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
