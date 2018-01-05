---
title: 'Porady: korzystanie z SystemParameters'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemparameters"></a>Porady: korzystanie z SystemParameters
W tym przykładzie pokazano, jak uzyskać dostęp i użyj właściwości <xref:System.Windows.SystemParameters> do nadawania stylu lub dostosowywanie przycisku.  
  
## <a name="example"></a>Przykład  
 Zasoby systemowe ujawnia niektóre ustawienia systemu zasobów, aby pomóc tworzyć elementy wizualne, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemParameters>jest klasa, która zawiera właściwości wartość parametru systemu i klucze zasobów, które powiązać wartości. Na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> jest <xref:System.Windows.SystemParameters> wartość właściwości i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> jest odpowiedni klucz zasobów.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemParameters> jako użycie statycznej właściwości lub odwołania do zasobów dynamicznych (o wartości właściwości statycznej jako klucz). Użyj odwołania zasobu dynamicznego, jeśli wartość system na podstawie automatycznie aktualizowane podczas aplikacji działa; w przeciwnym razie użyj odwołanie statyczne. Klucze zasobów przedrostkiem `Key` dołączonym do nazwy właściwości.  
  
 Poniższy przykład przedstawia sposób dostępu i statyczne wartości można używać <xref:System.Windows.SystemParameters> stylu lub dostosowanie przycisku. W tym przykładzie znaczników rozmiar przycisku przez zastosowanie <xref:System.Windows.SystemParameters> wartości do przycisku.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Aby użyć wartości <xref:System.Windows.SystemParameters> w kodzie, nie masz do użycia statycznego odwołania lub odwołania do zasobów dynamicznych. Użyj wartości <xref:System.Windows.SystemParameters> klasy. Mimo że właściwości niekluczowe pozornie są zdefiniowane jako właściwości statyczne, zachowanie środowiska uruchomieniowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system będzie obliczyć ponownie właściwości w czasie rzeczywistym, a zostanie prawidłowo konta użytkownika driven zmiany wartości systemu. Poniższy przykład przedstawia sposób ustawić szerokość i wysokość przycisku przy użyciu <xref:System.Windows.SystemParameters> wartości.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SystemParameters>  
 [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Używanie elementu SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Używanie kluczy parametrów systemowych](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
