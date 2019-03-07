---
title: 'Instrukcje: Definiuj i twórz odwołanie do zasobu'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 80be1460906100072e6263c967c213df7968c705
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492065"
---
# <a name="how-to-define-and-reference-a-resource"></a>Instrukcje: Definiuj i twórz odwołanie do zasobu

W tym przykładzie pokazano, jak zdefiniować zasób i odwoływać się do niego przy użyciu atrybutu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano dwa typy zasobów: <xref:System.Windows.Media.SolidColorBrush> zasobów i kilka <xref:System.Windows.Style> zasobów. <xref:System.Windows.Media.SolidColorBrush> Zasobów `MyBrush` służy do zapewnienia wartość kilka właściwości, aby uwzględniać <xref:System.Windows.Media.Brush> wpisz wartość. <xref:System.Windows.Style> Zasobów `PageBackground`, `TitleText` i `Label` docelowych każdego typu określonego formantu. Style nastavit szereg różnych właściwości formantów docelowych, podczas tego zasobu stylu odwołuje się do niego klucz zasobu i służy do ustawiania <xref:System.Windows.FrameworkElement.Style%2A> właściwości zdefiniowanych w kilku elementów sterowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Pamiętaj, że jedna z właściwości setterami z `Label` odwołuje się styl `MyBrush` zasobu zdefiniowanego wcześniej. Jest to typowa technika, ale należy pamiętać, że zasoby są analizowane i wprowadzany do słownika zasobów, w kolejności, które posiadają. Zasoby są również żądane według kolejności znaleziony w słowniku, jeśli używasz [staticresource — rozszerzenie znaczników](staticresource-markup-extension.md) można odwoływać się do nich z w ramach innego zasobu. Upewnij się, wcześniej zdefiniowaną dowolnego zasobu, którego można odwołać się w kolekcji zasobów niż którym następnie wymagany jest tego zasobu. Jeśli to konieczne, można obejść kolejność strict utworzenie odwołania do zasobów przy użyciu [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md) aby zamiast tego należy odwoływać się do zasobów w czasie wykonywania, ale należy zwrócić uwagę, to dynamicresource — Metoda ma wpływ wydajności. Aby uzyskać więcej informacji, zobacz [zasoby XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](xaml-resources.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
