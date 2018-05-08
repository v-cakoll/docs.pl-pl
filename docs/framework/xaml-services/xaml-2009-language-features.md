---
title: XAML 2009— Funkcje językowe
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 5014891b4edfa062f16d2c4b97c4d162d014fcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-2009-language-features"></a>XAML 2009— Funkcje językowe
XAML 2009 jest skrócona termin nowe funkcje języka XAML, które rozszerzyć istniejącą specyfikacja języka XAML. XAML 2009 wprowadzono kilka nowych dyrektywy oraz elementów składowych. Obejmują one[x: Arguments — dyrektywa](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: factorymethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: typearguments — dyrektywa ](../../../docs/framework/xaml-services/x-typearguments-directive.md); i typy wbudowane dla wspólnych elementów podstawowych języka (na przykład `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Obsługa 2009 XAML w WPF i programu Visual Studio  
 Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, która nie jest skompilowany znaczników WPF. Aktualnie kompilacji znaczników XAML i BAML formę XAML nie obsługują słów kluczowych języka XAML 2009 i funkcje.  
  
 Należy zauważyć, że istniejące metody ładowania utracić XAML w WPF również możliwe zabezpieczeniami i dostępem ograniczeń typów CLR i system typów, które są bardziej restrykcyjne niż dla kompilacji znaczników XAML. Aby uzyskać więcej informacji, zobacz [zabezpieczeń (WPF)](../../../docs/framework/wpf/security-wpf.md) lub [strategii zabezpieczeń WPF - zabezpieczeń platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 wprowadza również dodatkowe funkcje, że zmodyfikuj poprzedniej 2006 XAML konstrukcji lub że modyfikowanie formularzy podstawowe znaczników.  
  
### <a name="xkey-as-an-object-element"></a>x: Key jako elementu obiektu  
 XAML 2009 może obsługiwać `x:Key` jako obiekt (właściwość elementu, który ma wartość elementu obiektu); jednak obsługiwane tylko XAML 2006 `x:Key` jako atrybut. Zobacz sekcję "XAML 2009" [dyrektywy x: Key](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns dla elementów właściwości  
 XAML 2009 definicje (xmlns) przestrzeni nazw XAML mogą być obsługiwane na elementy właściwości; XAML 2006 obsługuje jednak tylko definicje xmlns dla obiekt elementów.  
  
### <a name="event-attributes"></a>Atrybuty zdarzeń  
 Dla atrybutów, które bazują na zdarzenia XAML 2006 przyjęto założenie, że kompilację znaczników związane i przesyła zdarzenia, które kompilację znaczników. XAML 2009 obsługuje znaczników podobny rozszerzenie znaczników, który różni się okablowania zdarzeń do wykonywania analizy i załadowanie pliku XAML. Jednak aplikacje WPF XAML scenariusze i dla interfejsu użytkownika WPF zwykle nie należy używać tej możliwości. WPF i jego wdrożenie XAML 2006 używa kombinacji okablowania programu obsługi zdarzeń dla kierowane zdarzenia zdefiniowane na <xref:System.Windows.UIElement> poziomu i jego kompilatora znaczników krok znacznie jego przetwarzanie atrybutu zdarzeń. Kompilator znaczników przetwarza również wstępnie atrybuty zdarzenia znaleziono w języku XAML, gdzie akcje kompilacji zadeklarować służy kompilatora znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
