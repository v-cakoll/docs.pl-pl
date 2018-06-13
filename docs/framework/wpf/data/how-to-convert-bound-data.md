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
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556643"
---
# <a name="how-to-convert-bound-data"></a>Jak konwertować powiązane dane
Ten przykład przedstawia sposób stosowania konwersji danych, który jest używany w powiązaniach.  
  
 Aby dokonać konwersji danych podczas tworzenia powiązania, należy utworzyć klasę implementującą <xref:System.Windows.Data.IValueConverter> interfejsu, który zawiera <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono implementacji konwertera daty, który konwertuje wartości typu date przekazano, tak aby pokazywane są tylko rok, miesiąc i dzień. Podczas implementowania <xref:System.Windows.Data.IValueConverter> interfejsu, jest dobrym rozwiązaniem do dekoracji implementacji z <xref:System.Windows.Data.ValueConversionAttribute> atrybut do wskazania programowanie narzędzia typy danych objętego konwersji, jak w poniższym przykładzie:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Po utworzeniu konwertera można dodać go jako zasób w Twojej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku. W poniższym przykładzie *src* mapowania do przestrzeni nazw, w którym *DateConverter* jest zdefiniowany.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Ponadto można użyć konwertera w Twoje powiązanie, używając następującej składni. W poniższym przykładzie, zawartość tekstu <xref:System.Windows.Controls.TextBlock> jest powiązany z *data_rozpoczęcia*, która jest właściwością zewnętrznego źródła danych.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Zasoby stylu w powyższym przykładzie są definiowane w sekcji zasobów nie są wyświetlane w tym temacie.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie powiązanej walidacji](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
