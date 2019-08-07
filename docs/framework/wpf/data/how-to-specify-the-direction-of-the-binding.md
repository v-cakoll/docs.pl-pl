---
title: 'Instrukcje: Określanie kierunku powiązania'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817910"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Instrukcje: Określ kierunek powiązania

W tym przykładzie pokazano, jak określić, czy powiązanie aktualizuje tylko Właściwość cel powiązania (target), właściwość Źródło powiązania (Źródło) lub właściwość target oraz Właściwość Source.  
  
## <a name="example"></a>Przykład  
 Użyj właściwości, <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> aby określić kierunek powiązania. Dostępne są następujące opcje dla aktualizacji powiązań:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>aktualizuje właściwość docelową lub właściwość za każdym razem, gdy właściwość docelowa lub właściwość źródłowa ulegnie zmianie.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>aktualizuje właściwość docelową tylko wtedy, gdy właściwość źródłowa ulegnie zmianie.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>aktualizuje właściwość docelową tylko wtedy, gdy aplikacja jest uruchamiana lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> zostanie zmieniona.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>aktualizuje właściwość source po zmianie właściwości docelowej.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>powoduje użycie domyślnej <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> Wyliczenie.  
  
 Poniższy przykład pokazuje, <xref:System.Windows.Data.Binding.Mode%2A> jak ustawić właściwość.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby wykryć zmiany źródła (odpowiednie dla <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, <xref:System.ComponentModel.INotifyPropertyChanged>taki jak. Aby zapoznać się z <xref:System.ComponentModel.INotifyPropertyChanged> przykładem implementacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md) .  
  
 W <xref:System.Windows.Data.BindingMode.TwoWay> przypadku <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań lub można kontrolować chronometraż aktualizacji <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> źródłowych przez ustawienie właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
