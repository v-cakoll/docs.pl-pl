---
title: Jak określić kierunek łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459094"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Instrukcje: Określanie kierunku powiązania

W tym przykładzie pokazano, jak określić, czy powiązanie aktualizuje tylko Właściwość cel powiązania (target), właściwość Źródło powiązania (Źródło) lub właściwość target oraz Właściwość Source.  
  
## <a name="example"></a>Przykład  
 Użyj właściwości <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType>, aby określić kierunek powiązania. Dostępne są następujące opcje dla aktualizacji powiązań:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> aktualizuje właściwość docelową lub właściwość za każdym razem, gdy właściwość docelowa lub właściwość źródłowa ulegnie zmianie.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> aktualizuje właściwość docelową tylko wtedy, gdy właściwość źródłowa ulegnie zmianie.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> aktualizuje właściwość docelową tylko wtedy, gdy aplikacja zostanie uruchomiona lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> ulegnie zmianie.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> aktualizuje właściwość source po zmianie właściwości docelowej.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> powoduje użycie domyślnej <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej.  
  
 Aby uzyskać więcej informacji, zobacz Wyliczenie <xref:System.Windows.Data.BindingMode>.  
  
 Poniższy przykład pokazuje, jak ustawić właściwość <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Aby wykrywać zmiany źródła (mające zastosowanie do <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązań), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, taki jak <xref:System.ComponentModel.INotifyPropertyChanged>. Zapoznaj się z tematem implementacja [powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md) dla przykładu implementacji <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 W przypadku powiązań <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> można kontrolować chronometraż aktualizacji źródłowych przez ustawienie właściwości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
