---
title: Jak definiować i tworzyć odwołanie do zasobu
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646510"
---
# <a name="how-to-define-and-reference-a-resource"></a>Jak definiować i tworzyć odwołanie do zasobu

W tym przykładzie pokazano, jak zdefiniować zasób i odwołać się do niego przy użyciu atrybutu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Przykład

Poniższy przykład definiuje dwa typy <xref:System.Windows.Media.SolidColorBrush> zasobów: <xref:System.Windows.Style> zasób i kilka zasobów. Zasób <xref:System.Windows.Media.SolidColorBrush> `MyBrush` jest używany do zapewnienia wartości kilku <xref:System.Windows.Media.Brush> właściwości, które każdy wziąć wartość typu. Zasoby <xref:System.Windows.Style> `PageBackground`i `TitleText` `Label` każdy cel określonego typu formantu. Style ustawiają różne właściwości formantów docelowych, gdy ten zasób stylu jest przywoływać klucz zasobu i jest używany do ustawiania <xref:System.Windows.FrameworkElement.Style%2A> właściwości kilku określonych elementów sterujących zdefiniowanych w programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Należy zauważyć, że jedna z właściwości w `Label` obrębie ustawiaczy `MyBrush` stylu odwołuje się również do zasobu zdefiniowanego wcześniej. Jest to wspólna technika, ale ważne jest, aby pamiętać, że zasoby są analizowane i wprowadzane do słownika zasobów w kolejności, w jakiej są podane. Zasoby są również wymagane przez kolejność znalezione w słowniku, jeśli używasz [StaticResource Markup Extension](staticresource-markup-extension.md) do odwoływania się do nich z poziomu innego zasobu. Upewnij się, że każdy zasób, do którego odwołujesz się, jest zdefiniowany wcześniej w kolekcji zasobów, niż tam, gdzie ten zasób jest następnie wymagany. W razie potrzeby można obejść kolejność tworzenia ścisłego odwołania do zasobów przy użyciu [rozszerzenia znaczników DynamicResource,](dynamicresource-markup-extension.md) aby odwołać się do zasobu w czasie wykonywania, ale należy pamiętać, że ta technika DynamicResource ma konsekwencje wydajności. Aby uzyskać szczegółowe informacje, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
