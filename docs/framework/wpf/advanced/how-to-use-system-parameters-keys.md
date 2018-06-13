---
title: Jak używać kluczy parametrów systemowych
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: c94719c8268cbbdadbe6805d531540e1f34ee5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544719"
---
# <a name="how-to-use-system-parameters-keys"></a>Jak używać kluczy parametrów systemowych
Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemParameters> jest klasa, która zawiera klucze zasobów, które powiązać wartości i wartości parametrów systemu — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metryki parametru systemu może służyć jako zasoby statyczne lub dynamiczne. Użyć zasobu dynamicznego, jeśli parametr metryki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.  
  
> [!NOTE]
>  Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej parametru systemu do nadawania stylu lub dostosowywanie przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład rozmiar przycisku przez przypisanie <xref:System.Windows.SystemParameters> wartości szerokości i wysokości przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Używanie elementu SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Używanie elementu SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
