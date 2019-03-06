---
title: 'Instrukcje: Użyj kluczy parametrów systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: a71551c5d539d7009fb9a052c81928a009fc4c35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357199"
---
# <a name="how-to-use-system-parameters-keys"></a>Instrukcje: Użyj kluczy parametrów systemowych
Zasoby systemowe ujawnić różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemParameters> to klasa, która zawiera wartości parametrów systemu i klucze zasobów, które wartości należy powiązać — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metryki parametru systemu może służyć jako zasoby statyczne lub dynamiczne. Użyj dynamicznych zasobów, jeśli chcesz, aby metryki parametru na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj zasób statyczny.  
  
> [!NOTE]
>  Dynamiczne zasoby mają słowa kluczowego *klucz* dołączana do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamiczny parametr systemu do określania stylu i dostosowywania przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład przycisku o rozmiarach, przypisując <xref:System.Windows.SystemParameters> wartości szerokości i wysokości przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Zobacz także
- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemFonts](how-to-use-systemfonts.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
