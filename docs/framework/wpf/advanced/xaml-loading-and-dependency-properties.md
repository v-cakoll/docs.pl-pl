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
ms.openlocfilehash: 57c25297f995acd1ef307466258b5f4e03cc3098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459533"
---
# <a name="xaml-loading-and-dependency-properties"></a>Właściwości zależności i ładowania XAML
Bieżąca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja jej procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zależna od właściwości zależności. Procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa metod systemu właściwości dla właściwości zależności podczas ładowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] binarnych i atrybutów przetwarzania, które są właściwościami zależności. Pozwala to efektywnie ominąć otoki właściwości. Podczas implementowania niestandardowych właściwości zależności należy uwzględnić to zachowanie i należy unikać umieszczania jakichkolwiek innych kodów w otoki właściwości, poza metodami systemu właściwości <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że można zrozumieć właściwości zależności zarówno jako odbiorca, jak i autora, [jak i](dependency-properties-overview.md) [właściwości zależności niestandardowej](custom-dependency-properties.md). Należy również zapoznać się z szczegółowym [omówieniem XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) i [składnią języka XAML](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementacja modułu ładującego XAML WPF i wydajność  
 Ze względów związanych z implementacją jest obliczana tańszie, aby identyfikować właściwość jako właściwość zależności i uzyskać dostęp do metody <xref:System.Windows.DependencyObject.SetValue%2A> systemu właściwości w celu jej ustawienia, zamiast używać otoki właściwości i jej metody ustawiającej. Jest to spowodowane tym, że procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] musi wnioskować cały model obiektów kodu zapasowego na podstawie tylko znajomości typu i relacji elementów członkowskich, które są wskazywane przez strukturę znaczników i różne ciągi.  
  
 Typ jest wyszukiwany przez kombinację atrybutów xmlns i Assembly, ale identyfikują elementy członkowskie, określanie, które mogą obsługiwać ustawienie jako atrybut i rozpoznawanie typów, które obsługują wartości właściwości, w przeciwnym razie wymagają szerszego odbicia przy użyciu <xref:System.Reflection.PropertyInfo>. Ponieważ właściwości zależności danego typu są dostępne jako tabela magazynu za pośrednictwem systemu właściwości, implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używa tej tabeli i wnioskuje, że każda dana właściwość *ABC* może być bardziej efektywnie ustawiana przez Wywoływanie <xref:System.Windows.DependencyObject.SetValue%2A> na zawierającym <xref:System.Windows.DependencyObject> typ pochodny przy użyciu identyfikatora właściwości zależności *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Implikacje dla niestandardowych właściwości zależności  
 Ponieważ bieżąca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja działania procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla ustawienia właściwości pomija otoki całkowicie, nie należy umieszczać żadnej dodatkowej logiki w zestawach definicji otoki dla właściwości zależności niestandardowej. Jeśli ta logika zostanie umieszczona w definicji zestawu, logika nie zostanie wykonana, gdy właściwość zostanie ustawiona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a nie w kodzie.  
  
 Podobnie inne aspekty procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], które uzyskują wartości właściwości z przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] również używają <xref:System.Windows.DependencyObject.GetValue%2A> zamiast używania otoki. W związku z tym należy również unikać żadnej dodatkowej implementacji w definicji `get` poza wywołaniem <xref:System.Windows.DependencyObject.GetValue%2A>.  
  
 Poniższy przykład jest zalecaną definicją właściwości zależności z otokami, gdzie identyfikator właściwości jest przechowywany jako pole `public` `static` `readonly`, a definicje `get` i `set` nie zawierają kodu poza wymaganą właściwością Metody systemowe, które definiują właściwość zależności.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Właściwości zależności typu kolekcji](collection-type-dependency-properties.md)
- [Zabezpieczenia właściwości zależności](dependency-property-security.md)
- [Bezpieczne wzorce konstruktora dla obiektów DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
