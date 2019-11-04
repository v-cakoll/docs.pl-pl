---
title: XAML 2009— Funkcje językowe
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: ac18be4732d223561d3a0afcef0e650587385822
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459893"
---
# <a name="xaml-2009-language-features"></a>XAML 2009— Funkcje językowe
XAML 2009 to skrócony termin dla nowych funkcji języka XAML, które poszerzają istniejącą specyfikację języka XAML. W języku XAML 2009 wprowadzono kilka nowych dyrektyw i konstrukcji. Obejmują one [dyrektywę x:arguments —](x-arguments-directive.md); [dyrektywa x:FactoryMethod](x-factorymethod-directive.md); [rozszerzenie znacznika x:Reference —](x-reference-markup-extension.md); [dyrektywa x:TypeArguments —](x-typearguments-directive.md); i typy wbudowane dla elementów podstawowych języka wspólnego (na przykład `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Obsługa języka XAML 2009 w WPF i Visual Studio  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko w przypadku języka XAML, który nie jest skompilowany w języku WPF. Skompilowane znaczniki XAML i forma BAML w języku XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
 Należy zauważyć, że istniejące techniki ładowania luźnego kodu XAML w WPF również mają możliwość zabezpieczenia i ograniczenia dostępu do typów CLR i systemu typów, które są bardziej restrykcyjne niż w przypadku kodu XAML skompilowanego przez adiustację. Aby uzyskać więcej informacji, zobacz [zabezpieczenia (WPF)](../wpf/security-wpf.md) lub [strategia zabezpieczeń WPF — zabezpieczenia platformy](../wpf/wpf-security-strategy-platform-security.md).  
  
 W języku XAML 2009 wprowadzono również dodatkowe funkcje, które modyfikują poprzednie konstrukcje języka XAML 2006 lub modyfikują podstawowe formularze znaczników.  
  
### <a name="xkey-as-an-object-element"></a>x:Key jako element obiektu  
 KOD XAML 2009 może obsługiwać `x:Key` jako obiekt (element właściwości, który ma wartość elementu obiektu); Jednak kod XAML 2006 jest obsługiwany tylko `x:Key` jako atrybut. Zobacz sekcję "XAML 2009" w [dyrektywie x:Key](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns dla elementów właściwości  
 KOD XAML 2009 może obsługiwać definicje przestrzeni nazw XAML (xmlns) w elementach właściwości. jednak XAML 2006 obsługuje tylko definicje xmlns dla elementów obiektu.  
  
### <a name="event-attributes"></a>Atrybuty zdarzenia  
 W przypadku atrybutów, które są obsługiwane przez zdarzenia, kod XAML 2006 zakłada, że kompilacja znaczników jest uwzględniana i przesyła zdarzenia do kompilacji adiustacji. Język XAML 2009 obsługuje formularz znaczników, który jest podobny do rozszerzenia znaczników, które określa okablowanie zdarzenia do momentu analizy i ładowania XAML. Jednak aplikacje WPF i scenariusze języka XAML dla interfejsu użytkownika WPF zwykle nie używają tej funkcji. Funkcja WPF i jej implementacja języka XAML 2006 używają kombinacji okablowania obsługi zdarzeń dla zdarzeń kierowanych zdefiniowanych na poziomie <xref:System.Windows.UIElement> i jego kroku kompilatora znaczników dla wielu jego przetwarzania atrybutów zdarzeń. Kompilator znaczników również wstępnie przetwarza wszystkie atrybuty zdarzeń Znalezione w języku XAML, w których akcje kompilacji deklarują, że kompilator znaczników jest używany.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
