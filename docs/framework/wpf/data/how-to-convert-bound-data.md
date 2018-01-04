---
title: "Jak konwertować powiązane dane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
