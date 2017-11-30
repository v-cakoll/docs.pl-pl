---
title: "Jak używać kluczy czcionek systemowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18781e3d71b9b30352323081e6d938350c6e53d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-fonts-keys"></a>Jak używać kluczy czcionek systemowych
Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemFonts>jest klasa, która zawiera wartości czcionki systemu i zasobów systemowych czcionek powiązać wartości — na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Mierniki czcionki systemu może służyć jako zasoby statyczne lub dynamiczne. Użyć zasobu dynamicznego, jeśli Metryka czcionki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.  
  
> [!NOTE]
>  Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej czcionki systemu do nadawania stylu lub dostosowywanie przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład tworzy styl przycisku, który przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie obszar o pędzla systemu](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Użyj SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Użyj SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
