---
title: "Jak definiować i tworzyć odwołanie do zasobu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322ac3e5ebfe2d820a4711d877396b9a1a2759a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-reference-a-resource"></a>Jak definiować i tworzyć odwołanie do zasobu
W tym przykładzie pokazano, jak zdefiniować zasobu i odwołaj się przy użyciu atrybutu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano dwa typy zasobów: <xref:System.Windows.Media.SolidColorBrush> zasobów i kilka <xref:System.Windows.Style> zasobów. <xref:System.Windows.Media.SolidColorBrush> Zasobów `MyBrush` służy do zapewnienia wartość kilka właściwości każdego zająć <xref:System.Windows.Media.Brush> wpisz wartość. <xref:System.Windows.Style> Zasobów `PageBackground`, `TitleText` i `Label` każdego docelowego typu określonego formantu. Style ustawić szereg różnych właściwości zawarte w formantach docelowej, gdy ten zasób stylu odwołuje się do niego klucz zasobu i jest używany do ustawiania <xref:System.Windows.FrameworkElement.Style%2A> właściwości zdefiniowanych w kilku elementów określonego formantu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Uwaga, że jedna z właściwości w ramach metod ustawiających `Label` odwołujący się styl `MyBrush` zasobów zdefiniowanego wcześniej. To jest typowe techniki, ale należy pamiętać, że zasoby są analizowane i wprowadzany do słownika zasobów w kolejności, czy są one. Zasoby wymagane są także według kolejności znaleziony w słowniku, jeśli używasz [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) do odwołania je z wewnątrz innego zasobu. Upewnij się, że wszystkich zasobów, do której odwołuje się zdefiniowano wcześniej w kolekcji zasobów niż gdzie jest następnie żądanego zasobu. Jeśli to konieczne, można obejść, kolejność tworzenia strict refererences zasobów za pomocą [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) można odwoływać się do zasobu w czasie wykonywania, ale pamiętaj, który to DynamicResource Metoda ma wpływ wydajności. Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby dla języka XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
