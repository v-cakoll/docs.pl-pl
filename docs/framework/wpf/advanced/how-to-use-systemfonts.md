---
title: 'Porady: korzystanie z SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 305d0cf18db5dc96b2d3cde863cf4ba2ae8dbb96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544680"
---
# <a name="how-to-use-systemfonts"></a>Porady: korzystanie z SystemFonts
W tym przykładzie pokazano, jak korzystać z zasobów statycznej <xref:System.Windows.SystemFonts> klasy do nadawania stylu lub dostosowywanie przycisku.  
  
## <a name="example"></a>Przykład  
 Zasoby systemowe ujawnia kilka określić systemu wartości jako właściwości i zasoby w celu ułatwienia tworzenia elementów wizualnych, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemFonts> to klasa, która zawiera zarówno system czcionki wartości jako właściwości statycznych i właściwości, które odwołują się klucze zasobów, które mogą być używane do dostępu tych wartości dynamicznie w czasie wykonywania. Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> jest <xref:System.Windows.SystemFonts> wartości, i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiedni klucz zasobów.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemFonts> jako statycznej właściwości lub odwołania do zasobów dynamicznych (o wartości właściwości statycznej jako klucz). Odwołanie do zasobu dynamicznego należy użyć, jeśli Metryka czcionki mają być automatycznie aktualizowane podczas aplikacji działa; w przeciwnym razie użyj wartości statycznej odwołania.  
  
> [!NOTE]
>  Klucze zasobów mieć sufiks "Klucz" dołączony do nazwy właściwości.  
  
 Poniższy przykład przedstawia sposób dostępu i użycia właściwości <xref:System.Windows.SystemFonts> jako wartości statyczne do nadawania stylu lub dostosowywanie przycisku. W tym przykładzie znaczników przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba używać wartość statyczną lub odwołaniem zasobu dynamicznego. Zamiast tego użyj właściwości niekluczowe <xref:System.Windows.SystemFonts> klasy. Mimo że właściwości niekluczowe pozornie są zdefiniowane jako właściwości statyczne, zachowanie środowiska wykonawczego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługiwanych przez system będzie obliczyć ponownie właściwości w czasie rzeczywistym i zostanie prawidłowo konta użytkownika driven zmiany wartości systemu. Poniższy przykład przedstawia sposób określ ustawienia czcionki przycisku.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SystemFonts>  
 [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Używanie elementu SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Używanie kluczy czcionek systemowych](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [x:Static, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [DynamicResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
