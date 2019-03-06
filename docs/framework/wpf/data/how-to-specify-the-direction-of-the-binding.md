---
title: 'Instrukcje: Określ kierunek łączenia'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378226"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Instrukcje: Określ kierunek łączenia
Ten przykład przedstawia sposób określania, czy powiązanie aktualizuje właściwość target (docelowy) powiązania, powiązania właściwość source (źródło), lub zarówno właściwość docelowa, jak i właściwość source.  
  
## <a name="example"></a>Przykład  
 Możesz użyć <xref:System.Windows.Data.Binding.Mode%2A> właściwość, aby określić kierunek łączenia. Na poniższej liście wyliczenia przedstawiono dostępne opcje powiązanie aktualizacji:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje właściwość target lub zawsze wtedy, gdy zmieni się właściwość docelowa lub właściwość source.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Aktualizuje właściwości docelowych, tylko wtedy, gdy zmieni się właściwość source.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> Aktualizuje właściwości docelowych, tylko wtedy, gdy aplikacja jest uruchamiana, lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> ulega zmianie.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> Aktualizuje właściwości source, gdy zmieni się właściwość docelowa.  
  
-   <xref:System.Windows.Data.BindingMode.Default> powoduje, że wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> wartość właściwości docelowym ma być używany.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> wyliczenia.  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Data.Binding.Mode%2A> właściwości.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby wykryć zmiany źródła (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), źródło musi zaimplementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>. Zobacz [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.  
  
 Aby uzyskać <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań chronometraż aktualizacji źródła można kontrolować przez ustawienie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
