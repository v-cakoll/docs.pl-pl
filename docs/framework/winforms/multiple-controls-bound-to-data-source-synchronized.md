---
title: 'Porady: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 5ab7eebd4f4087502f8709e17dde3f3de448c9aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Porady: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych
Często, podczas pracy z powiązanie danych w formularzach systemu Windows, wielu formantów powiązanych z tym samym źródle danych. W niektórych przypadkach może być konieczne wykonać dodatkowe czynności, aby upewnić się, czy powiązania właściwości formantów pozostają zsynchronizowane ze sobą i źródła danych. Te kroki są niezbędne w dwóch sytuacjach:  
  
-   Jeśli źródło danych nie implementuje <xref:System.ComponentModel.IBindingList>i w związku z tym Generowanie <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Jeśli źródło danych implementuje <xref:System.ComponentModel.IEditableObject>.  
  
 W pierwszym przypadku można użyć <xref:System.Windows.Forms.BindingSource> można powiązać źródła danych do kontrolek. W drugim przypadku należy użyć <xref:System.Windows.Forms.BindingSource> i obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń i wywołanie <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> na skojarzonym <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak powiązanie formantów trzy — dwa kontrolki pola tekstowego i <xref:System.Windows.Forms.DataGridView> kontroli — w tej samej kolumnie w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. W tym przykładzie pokazano, jak obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń i upewnij się, że po zmianie wartości tekstowej pola tekstowego, okno dodatkowy tekst i <xref:System.Windows.Forms.DataGridView> formantu są aktualizowane przy użyciu poprawnej wartości.  
  
 W przykładzie użyto <xref:System.Windows.Forms.BindingSource> można powiązać źródła danych i kontrolek. Alternatywnie powiązanie formantów bezpośrednio ze źródłem danych i pobierania <xref:System.Windows.Forms.BindingManagerBase> dla powiązania z formularza <xref:System.Windows.Forms.Control.BindingContext%2A> , a następnie obsługi <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenia dla <xref:System.Windows.Forms.BindingManagerBase>. Na przykład jak to zrobić, zobacz stronę pomocy <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenie <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W tym przykładzie kodu wymaga  
  
-   Odwołuje się do <xref:System>, <xref:System.Windows.Forms>, i <xref:System.Drawing> zestawów.  
  
-   Formularz z <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń i wywołanie `InitializeControlsAndDataSource` metody w przykładzie z formularza <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Interfejsy dotyczące wiązania danych](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
