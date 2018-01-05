---
title: "Właściwości zależności i ładowania XAML"
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
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9771aa05d029603a018e041644ff3e2018e26ca4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-loading-and-dependency-properties"></a>Właściwości zależności i ładowania XAML
Bieżący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonania jego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora jest z założenia pamiętać właściwości zależności. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Procesor używa metody system właściwości dla właściwości zależności podczas ładowania pliku binarnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i przetwarzania atrybutów, które są właściwości zależności. Pomija to skutecznie otoki właściwości. Po zaimplementowaniu właściwości niestandardowe zależności musi konta tego zachowania, a unikać umieszczania innego kodu w Twojej otoki właściwości innych niż metody systemu właściwości <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że zrozumieć właściwości zależności zarówno jako konsumenta i autora i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) i [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md). Należy również przeczytanie [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) i [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementacja modułu ładującego WPF XAML i wydajności  
 Ze względów implementacji jest praktyce mniej kosztowne zidentyfikować właściwości jako właściwość zależności i korzystać z systemu właściwości <xref:System.Windows.DependencyObject.SetValue%2A> metodę w celu ustawienia, a nie przy użyciu otoki właściwości i metody ustawiającej. Jest to spowodowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora musi rozpoznać cały obiekt modelu kodu zapasowy oparte tylko na wiedzy o typie i element członkowski relacje, które są wskazywane przez strukturę znaczników i różne ciągi.  
  
 Typ jest wyszukiwana przy użyciu kombinacji xmlns i atrybutów zestawu, ale Identyfikowanie członków, określania, które mogą obsługiwać ustawiany jako atrybutu, i rozwiązania, jakie typy obsługuje wartości właściwości w przeciwnym razie będzie wymagać szeroką gamę odbicia przy użyciu <xref:System.Reflection.PropertyInfo>. Ponieważ właściwości zależności dla danego typu są dostępne jako tabelę magazynu za pośrednictwem systemu właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonania jego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora korzysta z tej tabeli i ustala, że jakaś podanej właściwości *ABC* można ustawić wydajniej wywołując <xref:System.Windows.DependencyObject.SetValue%2A> na zawierający <xref:System.Windows.DependencyObject> typu przy użyciu identyfikatora właściwości zależności pochodnego *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Wpływ na właściwości niestandardowe zależności  
 Ponieważ bieżącego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zachowanie procesora ustawienie właściwości pomija otoki całkowicie, nie wolno umieszczać żadnych dodatkową logikę do definicji zestawu otoki dla Twojego właściwości niestandardowe zależności. Umieść takie logikę w definicji zestawu, a następnie logiki nie zostanie wykonany, gdy właściwość jest ustawiona [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , a nie w kodzie.  
  
 Podobnie, inne aspekty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, którą pobrać wartości właściwości z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przetwarzania również użycie <xref:System.Windows.DependencyObject.GetValue%2A> zamiast przy użyciu otoki. W związku z tym należy unikać także wszelkie dodatkowe implementacja `get` definicji poza <xref:System.Windows.DependencyObject.GetValue%2A> wywołania.  
  
 Poniższy przykład jest zalecane zależności definicji właściwości z otoki, której identyfikator właściwości jest przechowywana jako `public` `static` `readonly` pola i `get` i `set` żaden kod nie zawiera definicji poza metody systemu wymagana właściwość definiujące właściwości zależności kopii.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Właściwości zależności typu kolekcji](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Bezpieczne wzorce konstruktora dla obiektów DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
