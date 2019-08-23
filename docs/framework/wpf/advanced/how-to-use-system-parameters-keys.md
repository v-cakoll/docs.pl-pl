---
title: 'Instrukcje: Używanie kluczy parametrów systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918368"
---
# <a name="how-to-use-system-parameters-keys"></a>Instrukcje: Używanie kluczy parametrów systemowych
Zasoby systemowe uwidaczniają różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są spójne z ustawieniami systemowymi. <xref:System.Windows.SystemParameters>to Klasa, która zawiera zarówno wartości parametru systemowego, jak i klucze zasobów powiązane z wartościami — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metryki parametrów systemowych mogą służyć jako zasoby statyczne lub dynamiczne. Użyj zasobu dynamicznego, jeśli chcesz, aby Metryka parametru była aktualizowana automatycznie podczas uruchamiania aplikacji; w przeciwnym razie użyj zasobu statycznego.  
  
> [!NOTE]
> Zasoby dynamiczne mają *klucz* słowa kluczowego, który jest dołączany do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznych parametru systemu i używać ich do nadawania stylu lub dostosowywania przycisku. Ten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład zmienia rozmiar przycisku, przypisując <xref:System.Windows.SystemParameters> wartości do szerokości i wysokości przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemFonts](how-to-use-systemfonts.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
