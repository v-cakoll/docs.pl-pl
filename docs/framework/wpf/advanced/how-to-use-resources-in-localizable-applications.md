---
title: "Jak użyć zasobów w zlokalizowanych aplikacjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d803989292e2fc6b0945c397df5ce32d318147fc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Jak użyć zasobów w zlokalizowanych aplikacjach
Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do innych kultur. W tym celu tekstu na przykład tytułów, podpisów, elementy listy i tak dalej ma ma zostać poddany translacji. Aby ułatwić tłumaczenia elementów, które ma zostać poddany translacji są zbierane w pliki zasobów. Zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) informacji na temat sposobu tworzenia pliku zasobu do lokalizacji. Aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji Lokalizowalny deweloperzy potrzebne do tworzenia zlokalizowania zasobów w ramach zestawu zasobów. Zestaw zasobów jest zlokalizowane w różnych językach, a kodem używa zarządzanie zasobami [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do załadowania. Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji jest plikiem projektu (.proj). W pliku projektu powinien znajdować się wszystkie zasoby, które są używane w aplikacji. Poniższy przykład kodu pokazuje to.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Aby użyć zasób w aplikacji, można utworzyć wystąpienia <xref:System.Resources.ResourceManager> i załadować zasobu, którego chcesz użyć. Poniżej pokazano, jak to zrobić.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
