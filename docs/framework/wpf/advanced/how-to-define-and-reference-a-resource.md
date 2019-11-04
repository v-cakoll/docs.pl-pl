---
title: Jak definiować i tworzyć odwołanie do zasobu
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460176"
---
# <a name="how-to-define-and-reference-a-resource"></a>Jak definiować i tworzyć odwołanie do zasobu

Ten przykład przedstawia sposób definiowania zasobu i odwoływania się do niego przy użyciu atrybutu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano dwa typy zasobów: zasób <xref:System.Windows.Media.SolidColorBrush> i kilka zasobów <xref:System.Windows.Style>. `MyBrush` zasobów <xref:System.Windows.Media.SolidColorBrush> służy do podania wartości kilku właściwości, z których każda pobiera <xref:System.Windows.Media.Brush> wartość typu. `PageBackground`zasobów <xref:System.Windows.Style>, `TitleText` i `Label` każdego celu określonego typu formantu. Style ustawiają różne różne właściwości w kontrolkach strategicznych, gdy ten zasób stylu jest przywoływany przez klucz zasobu i służy do ustawiania właściwości <xref:System.Windows.FrameworkElement.Style%2A> kilku określonych elementów sterujących zdefiniowanych w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Należy zauważyć, że jedna z właściwości w metodach ustawiających `Label` stylu odwołuje się również do zdefiniowanego wcześniej zasobu `MyBrush`. Jest to typowa technika, ale ważne jest, aby pamiętać, że zasoby są analizowane i wprowadzane do słownika zasobów w kolejności, w jakiej zostały określone. Zażądano również zasobów w ramach zamówienia znalezionego w słowniku, jeśli używasz [rozszerzenia StaticResource Markup](staticresource-markup-extension.md) do odwoływania się do nich z innego zasobu. Upewnij się, że wszystkie zasoby, do których odwołuje się, zostały zdefiniowane wcześniej w kolekcji Resources, a następnie zażądano tego zasobu. W razie potrzeby można obejść ścisłą kolejność tworzenia odwołań do zasobów przy użyciu [rozszerzenia znacznika DynamicResource —](dynamicresource-markup-extension.md) , aby odwołać się do zasobu w czasie wykonywania, ale należy pamiętać, że ta technika DynamicResource — ma wydajność konsekwencj. Aby uzyskać szczegółowe informacje, zobacz [zasoby XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](xaml-resources.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
