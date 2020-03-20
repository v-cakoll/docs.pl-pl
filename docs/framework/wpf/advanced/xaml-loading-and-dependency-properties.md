---
title: Właściwości zależności i ładowania XAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186255"
---
# <a name="xaml-loading-and-dependency-properties"></a>Właściwości zależności i ładowania XAML
Bieżąca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jego procesora jest z natury zależność właściwości świadomy. Procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używa metod systemu właściwości dla właściwości właściwości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podczas ładowania atrybutów binarnych i przetwarzania, które są właściwości zależności. To skutecznie omija otoki właściwości. Podczas implementowania niestandardowych właściwości zależności, należy uwzględnić to zachowanie i należy unikać umieszczania innego <xref:System.Windows.DependencyObject.GetValue%2A> kodu <xref:System.Windows.DependencyObject.SetValue%2A>w otoce właściwości innych niż metody systemu właściwości i .  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są zrozumiałe zarówno jako konsument, jak i autor, oraz że można przeczytać [Omówienie właściwości zależności](dependency-properties-overview.md) i [właściwości zależności niestandardowych.](custom-dependency-properties.md) Należy również przeczytać [przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) i [składnię XAML w szczegółach](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementacja i wydajność modułu ładującego WPF XAML  
 Ze względu na implementację jest obliczeniowo tańsze do identyfikowania właściwości jako <xref:System.Windows.DependencyObject.SetValue%2A> właściwości zależności i dostęp do metody systemu właściwości, aby ją ustawić, a nie przy użyciu otoki właściwości i jej ustawiacza. Dzieje się [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tak, ponieważ procesor musi wywnioskować cały model obiektu kodu zapasowego na podstawie tylko znając relacje typu i elementu członkowskiego, które są wskazywane przez strukturę znaczników i różnych ciągów.  
  
 Typ jest wyszukany za pomocą kombinacji xmlns i atrybutów zestawu, ale identyfikowanie elementów członkowskich, określanie, które mogą być ustawione <xref:System.Reflection.PropertyInfo>jako atrybut, i rozwiązywanie typów, które obsługują wartości właściwości wymagałoby rozległego odbicia przy użyciu . Ponieważ właściwości zależności dla danego typu są dostępne jako tabela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] magazynu za [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pośrednictwem systemu właściwości, implementacja jego procesora używa tej tabeli <xref:System.Windows.DependencyObject.SetValue%2A> i wnioskuje, że dowolna dana właściwość *ABC* może być bardziej efektywnie ustawiona przez wywołanie <xref:System.Windows.DependencyObject> zawierającego typu pochodnego przy użyciu identyfikatora właściwości zależności *ABCProperty*.  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>Implikacje dla właściwości zależności niestandardowych  
 Ponieważ bieżąca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja zachowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora dla ustawienia właściwości całkowicie pomija otoki, nie należy umieszczać żadnych dodatkowych logiki w definicje zestawu otoki dla właściwości zależności niestandardowej. Jeśli umieścisz taką logikę w definicji zestawu, logika nie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zostanie wykonana, gdy właściwość jest ustawiona, a nie w kodzie.  
  
 Podobnie inne aspekty procesora, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] które uzyskują [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wartości <xref:System.Windows.DependencyObject.GetValue%2A> właściwości z przetwarzania również używać, a nie przy użyciu otoki. W związku z tym należy również `get` unikać wszelkie <xref:System.Windows.DependencyObject.GetValue%2A> dodatkowe implementacji w definicji poza wywołaniem.  
  
 Poniższy przykład jest zalecana definicja właściwości zależności z otoki, `public` `static` `readonly` gdzie identyfikator `get` właściwości `set` jest przechowywany jako pole i definicje i nie zawierają kodu poza niezbędne metody systemu właściwości, które definiują kopię zapasową właściwości zależności.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Właściwości zależności typu kolekcji](collection-type-dependency-properties.md)
- [Zabezpieczenie właściwości zależności](dependency-property-security.md)
- [Bezpieczne wzorce konstruktora DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
