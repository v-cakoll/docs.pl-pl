---
title: XAML 2009— Funkcje językowe
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 05f811cd0d95f7605963dae851430fb6bf0e9f7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938810"
---
# <a name="xaml-2009-language-features"></a>XAML 2009— Funkcje językowe
XAML 2009 jest terminem skrót dla nowych funkcji języka XAML, które rozszerzają istniejących specyfikacji języka XAML. XAML 2009 wprowadza kilka nowych dyrektyw i konstrukcji. Obejmują one [x: Arguments — dyrektywa](x-arguments-directive.md); [x: FactoryMethod — dyrektywa](x-factorymethod-directive.md); [x: Reference — rozszerzenie znaczników](x-reference-markup-extension.md); [x: typearguments — dyrektywa ](x-typearguments-directive.md); i typy wbudowane dla wspólnych elementów podstawowych języka (na przykład `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Obsługa 2009 XAML w WPF i programu Visual Studio  
 W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest kompilowana do znaczników WPF. XAML kompilowana do znaczników i formularz BAML XAML aktualnie nie obsługuje słowa kluczowe języka XAML 2009 oraz funkcje.  
  
 Należy zauważyć, że istniejące technik do ładowania luźne XAML w WPF również możliwych zabezpieczeniami i dostępem ograniczenia typy CLR i system typów, które są bardziej restrykcyjne niż XAML kompilowana do znaczników. Aby uzyskać więcej informacji, zobacz [zabezpieczenia (WPF)](../wpf/security-wpf.md) lub [strategia zabezpieczeń WPF - zabezpieczenia platformy](../wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 wprowadza również dodatkowe funkcje, zmodyfikuj poprzedniego 2006 XAML lub konstrukcji, które modyfikowanie formularzy znaczników podstawowych.  
  
### <a name="xkey-as-an-object-element"></a>x: Key, jako elementu obiektu  
 XAML 2009 może obsługiwać `x:Key` jako obiekt (właściwość element, który ma wartość elementu obiektu); jednak obsługiwana tylko XAML 2006 `x:Key` jako atrybut. Zobacz sekcję "XAML 2009" [x: Key — dyrektywa](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns dla właściwości elementów  
 XAML 2009 definicji przestrzeni nazw (xmlns) XAML mogą być obsługiwane na właściwości elementów; XAML 2006 obsługuje jednak tylko definicje xmlns elementów obiektu.  
  
### <a name="event-attributes"></a>Atrybuty zdarzeń  
 Atrybuty, które są oparte na obiektach zdarzeń XAML 2006 zakłada, że kompilacji znaczników jest zaangażowane i przesyła zdarzeń do kompilacji kodu znaczników. XAML 2009 obsługuje kod znaczników podobny rozszerzenie znaczników, który odracza okablowania zdarzeń aż do czasu wykonywania, analizowania i ładowanie XAML. Jednak aplikacje WPF i XAML scenariuszy dla WPF UI zazwyczaj nie należy używać tej funkcji. WPF i jego wdrożenie XAML 2006 używa kombinacji okablowania procedury obsługi zdarzeń dla zdarzenia trasowane zdefiniowany z numerem <xref:System.Windows.UIElement> poziom i jego kompilator znaczników krok znacznie jej przetwarzanie atrybutu zdarzeń. Kompilator znaczników również wstępnie przetwarza wszelkie atrybuty zdarzeń, w której akcje kompilacji zadeklarować, że używany jest kompilator znaczników XAML.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
