---
title: 'Instrukcje: Konwertuj powiązane dane'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 5069b6d6b7ded52011ec4c65ca2c47e41bba2ece
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705725"
---
# <a name="how-to-convert-bound-data"></a>Instrukcje: Konwertuj powiązane dane
Ten przykład przedstawia sposób zastosowania konwersji na dane, które jest używane w powiązaniach.  
  
 Aby dokonać konwersji danych podczas tworzenia powiązania, należy utworzyć klasę, która implementuje <xref:System.Windows.Data.IValueConverter> interfejsu, który zawiera <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje implementację konwerter daty, która konwertuje wartość daty przekazanej tak, aby pokazywał tylko rok, miesiąc i dzień. Podczas implementowania <xref:System.Windows.Data.IValueConverter> interfejsu, jest dobrym rozwiązaniem do dekorowania implementacji przy użyciu <xref:System.Windows.Data.ValueConversionAttribute> atrybutu, aby wskazać programowania narzędzi typy danych związane z konwersją, jak w poniższym przykładzie:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Po utworzeniu konwertera można dodać go jako zasób w swojej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku. W poniższym przykładzie *src* mapuje do przestrzeni nazw, w którym *DateConverter* jest zdefiniowana.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Na koniec konwertera można używać w Twoje powiązanie, używając następującej składni. W poniższym przykładzie, zawartość tekstu <xref:System.Windows.Controls.TextBlock> jest powiązany z *StartDate*, który jest właściwością zewnętrznego źródła danych.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Zasoby stylów, do których odwołuje się w powyższym przykładzie są zdefiniowane w sekcji zasobów nie są wyświetlane w tym temacie.  
  
## <a name="see-also"></a>Zobacz także
- [Implementowanie powiązanej walidacji](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
