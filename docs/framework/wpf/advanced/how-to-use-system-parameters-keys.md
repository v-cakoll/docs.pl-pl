---
title: "Jak używać kluczy parametrów systemowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a>Jak używać kluczy parametrów systemowych
Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemParameters>jest klasa, która zawiera klucze zasobów, które powiązać wartości i wartości parametrów systemu — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metryki parametru systemu może służyć jako zasoby statyczne lub dynamiczne. Użyć zasobu dynamicznego, jeśli parametr metryki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.  
  
> [!NOTE]
>  Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej parametru systemu do nadawania stylu lub dostosowywanie przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład rozmiar przycisku przez przypisanie <xref:System.Windows.SystemParameters> wartości szerokości i wysokości przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie obszar o pędzla systemu](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Użyj SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Użyj SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
