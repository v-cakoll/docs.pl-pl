---
title: Jak konwertować powiązane dane
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458856"
---
# <a name="how-to-convert-bound-data"></a>Jak konwertować powiązane dane
Ten przykład pokazuje, jak zastosować konwersję do danych, które są używane w powiązaniach.  
  
 Aby przekonwertować dane podczas wiązania, należy utworzyć klasę, która implementuje interfejs <xref:System.Windows.Data.IValueConverter>, który obejmuje metody <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono implementację konwertera daty, który konwertuje przekazaną wartość daty, aby wyświetlić tylko rok, miesiąc i dzień. Podczas implementowania interfejsu <xref:System.Windows.Data.IValueConverter>, dobrym sposobem jest dekorować implementacji z atrybutem <xref:System.Windows.Data.ValueConversionAttribute>, aby wskazać narzędziom programistycznym typy danych uwzględnione w konwersji, jak w poniższym przykładzie:  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Po utworzeniu konwertera można go dodać jako zasób do pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W poniższym przykładzie *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *DateConverter* .  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Na koniec można użyć konwertera w powiązaniu przy użyciu następującej składni. W poniższym przykładzie zawartość tekstowa <xref:System.Windows.Controls.TextBlock> jest powiązana z *StartDate*, która jest właściwością zewnętrznego źródła danych.  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Zasoby stylu, do których odwołuje się powyższy przykład, są zdefiniowane w sekcji zasobów, która nie jest pokazana w tym temacie.  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie powiązanej walidacji](how-to-implement-binding-validation.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
