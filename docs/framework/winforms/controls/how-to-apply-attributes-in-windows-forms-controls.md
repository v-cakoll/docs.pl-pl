---
title: "Porady: stosowanie atrybutów w formantach formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4d5bfb445ce6ed37ad1dc63d92fde833ac9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Porady: stosowanie atrybutów w formantach formularzy systemu Windows
Aby opracować składników i formantów, które nawiązują prawidłową interakcję z środowiska projektowania i poprawnego wykonania w czasie wykonywania, należy poprawnie zastosować atrybutów do klas i członków.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak używać kilka atrybutów na kontrolkę niestandardową. Formant pokazuje możliwości rejestrowania proste. Jeśli formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> formantu. Jeśli wartość przekracza wartość określoną przez `Threshold` właściwość `ThresholdExceeded` zdarzenia.  
  
 `AttributesDemoControl` Dzienniki wartości z `LogEntry` klasy. `LogEntry` Klasy to klasa szablonu, który oznacza, że jest ona sparametryzowana na typ, który rejestruje. Na przykład jeśli `AttributesDemoControl` jest rejestrowanie wartości typu `float`, każdy `LogEntry` wystąpienia został zadeklarowany i używane w następujący sposób.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Ponieważ `LogEntry` jest sparametryzowana przez dowolnego typu, należy użyć odbicia do działania na typ parametru. Do poprawnego, z typem parametru funkcji próg `T` musi implementować <xref:System.IComparable> interfejsu.  
  
 Formularz, który jest hostem `AttributesDemoControl` okresowo kwerendy licznika wydajności. Każda wartość jest spakowany w `LogEntry` odpowiedniego typu i dodany do formularza <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Otrzymuje wartość za pośrednictwem jej powiązania danych i wyświetla wartość w <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 W pierwszym przykładzie kodu jest `AttributesDemoControl` implementacji. Drugi przykład kodu pokazuje formularza korzystającego z `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atrybuty klasy  
 Niektóre atrybuty są stosowane na poziomie klasy. Poniższy przykład kodu pokazuje atrybuty, które są często stosowane do formantu formularzy systemu Windows.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atrybut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute>jest inny atrybut często używane klasy poziomie. Poniższy przykład kodu pokazuje jej na użytek `LogEntry` klasy. W tym przykładzie przedstawiono również implementacja <xref:System.ComponentModel.TypeConverter> dla `LogEntry` typu o nazwie `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atrybuty na poziomie członka  
 Niektóre atrybuty są stosowane na poziomie elementu członkowskiego. W poniższych przykładach kodu pokazano niektóre atrybuty, które są często stosowane do właściwości formantów formularzy systemu Windows.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atrybut AmbientValue  
 W poniższym przykładzie pokazano <xref:System.ComponentModel.AmbientValueAttribute> i zawiera kod, który obsługuje jego interakcji z środowisku projektowania. Ta interakcja jest nazywany *otoczenie*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atrybuty wiązania danych  
 W poniższych przykładach pokazano implementacja złożone powiązanie danych. Klasa poziomie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, pokazano wcześniej, określa `DataSource` i `DataMember` właściwości do użycia podczas wiązania z danymi. <xref:System.ComponentModel.AttributeProviderAttribute> Określa typ, do którego `DataSource` właściwość zostanie z nim powiązane.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Formularz, który jest hostem `AttributesDemoControl` wymaga odwołania do `AttributesDemoControl` zestawu w celu przeprowadzenia kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Atrybuty w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Porady: serializacji kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
