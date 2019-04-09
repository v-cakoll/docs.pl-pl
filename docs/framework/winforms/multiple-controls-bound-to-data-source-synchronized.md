---
title: 'Instrukcje: Zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 8f7e59720420a845fa195b8c0fb078a8699a9bc3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170342"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Instrukcje: Zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych
Często pracując przy użyciu powiązania danych w formularzach Windows Forms, wielu formantów są powiązane z tego samego źródła danych. W niektórych przypadkach może być konieczne wykonać dodatkowe czynności, aby upewnić się, że powiązanych właściwości kontrolek pozostają zsynchronizowane ze sobą i źródła danych. Te kroki są niezbędne w dwóch sytuacjach:  
  
-   Jeśli źródło danych nie zawiera implementacji <xref:System.ComponentModel.IBindingList>i w związku z tym generowania <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Jeśli źródło danych implementuje <xref:System.ComponentModel.IEditableObject>.  
  
 W pierwszym przypadku można użyć <xref:System.Windows.Forms.BindingSource> można powiązać źródła danych do kontrolek. W tym ostatnim przypadku używasz <xref:System.Windows.Forms.BindingSource> i obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzenia i wywołania <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> dla powiązanego <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak powiązać formanty trzy — dwie kontrolki pola tekstowego i <xref:System.Windows.Forms.DataGridView> kontroli — do tej samej kolumny w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. W tym przykładzie pokazano, jak obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń i upewnij się, że po zmianie wartości tekstowej pola tekstowego, dodatkowe pole tekstowe i <xref:System.Windows.Forms.DataGridView> kontrolki są aktualizowane przy użyciu poprawnej wartości.  
  
 W przykładzie użyto <xref:System.Windows.Forms.BindingSource> powiązać ze źródłem danych i kontrolki. Alternatywnie można powiązać formanty bezpośrednio ze źródłem danych i pobierać <xref:System.Windows.Forms.BindingManagerBase> dla powiązania z poziomu formularza <xref:System.Windows.Forms.Control.BindingContext%2A> i następnie obsłużyć <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenie <xref:System.Windows.Forms.BindingManagerBase>. Na przykład jak to zrobić, zobacz stronę pomocy na temat <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenia <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Poniższy przykład kodu wymaga  
  
-   Odwołuje się do <xref:System>, <xref:System.Windows.Forms>, i <xref:System.Drawing> zestawów.  
  
-   Formularz z <xref:System.Windows.Forms.Form.Load> obsługi zdarzenia i wywołania `InitializeControlsAndDataSource` metody w przykładzie z formularza <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource](./controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows](change-notification-in-windows-forms-data-binding.md)
- [Interfejsy dotyczące wiązania danych](interfaces-related-to-data-binding.md)
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
