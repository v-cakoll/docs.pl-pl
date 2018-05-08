---
title: Jak określić kierunek łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 100130f3dc099d1cf1f216c841e7e1dc1d083f39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Jak określić kierunek łączenia
Ten przykład przedstawia sposób określić, czy powiązanie aktualizować tylko właściwość target (docelowy) powiązania powiązania właściwości source (źródło), lub zarówno właściwość target właściwości oraz źródła.  
  
## <a name="example"></a>Przykład  
 Możesz użyć <xref:System.Windows.Data.Binding.Mode%2A> właściwości do określania kierunku powiązania. Na poniższej liście wyliczenia przedstawia dostępne opcje aktualizacji powiązania:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje właściwość docelowego lub zmianie właściwości target lub właściwości source.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Właściwość target aktualizacji, tylko wtedy, gdy zmienia się właściwości source.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> aktualizuje właściwość target tylko podczas uruchamiania aplikacji lub <xref:System.Windows.FrameworkElement.DataContext%2A> ulega zmianie.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> Aktualizuje właściwości source po zmianie właściwości target.  
  
-   <xref:System.Windows.Data.BindingMode.Default> powoduje, że wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej do użycia.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> wyliczenia.  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Data.Binding.Mode%2A> właściwości.  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby wykryć zmiany źródła (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązań), źródło musi implementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>. Zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.  
  
 Dla <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań, można kontrolować czas aktualizacji źródła przez ustawienie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.Binding>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
