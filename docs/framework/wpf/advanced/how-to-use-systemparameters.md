---
title: 'Instrukcje: Użyj SystemParameters'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 00afc5c12ea9b83759361e9a3f175e91b4cbb10d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541667"
---
# <a name="how-to-use-systemparameters"></a>Instrukcje: Użyj SystemParameters
W tym przykładzie pokazano, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemParameters> do nadawania stylu lub dostosować przycisku.  
  
## <a name="example"></a>Przykład  
 Zasoby systemowe uwidocznić kilka ustawień systemu na podstawie zasobów, aby ułatwić tworzenie wizualizacji, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemParameters> jest klasą, który zawiera właściwości wartość parametru systemu i klucze zasobów, które wartości należy powiązać. Na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> jest <xref:System.Windows.SystemParameters> wartości właściwości i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> jest odpowiedni klucz zasobu.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemParameters> jako użycia właściwość statyczna lub odwołania do zasobu dynamicznego (wartością właściwości statycznej jako klucz). Użyj odwołania zasób dynamiczny, jeśli chcesz, aby wartość systemu opartego na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj odwołania statycznego. Klucze zasobu mają ten sufiks `Key` dołączana do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do wartości statycznej <xref:System.Windows.SystemParameters> do nadawania stylu i dostosowywania przycisku. W tym przykładzie znaczników przycisku o rozmiarach, stosując <xref:System.Windows.SystemParameters> wartości do przycisku.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Aby użyć wartości <xref:System.Windows.SystemParameters> w kodzie, nie trzeba używać odwołań statycznych lub dynamicznych zasobów odwołań. Zamiast tego należy użyć wartości <xref:System.Windows.SystemParameters> klasy. Mimo że właściwości klucza najwyraźniej są definiowane jako właściwości statycznej, zachowanie środowiska uruchomieniowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system spowoduje to ponowne ocenienie właściwości w czasie rzeczywistym i zostanie prawidłowo konto oparte na użytkownika zmiany wartości systemu. Poniższy przykład pokazuje, jak ustawić szerokość i wysokość przycisku przy użyciu <xref:System.Windows.SystemParameters> wartości.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.SystemParameters>
- [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [Używanie kluczy parametrów systemowych](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
