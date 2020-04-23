---
title: XAML 2009— Funkcje językowe
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: e58e6757b88958bf8a3547c8a272c2e6298dcecb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071599"
---
# <a name="xaml-2009-language-features"></a>XAML 2009— Funkcje językowe
XAML 2009 to skrótowy termin dla nowych funkcji języka XAML, które rozszerzają istniejącą specyfikację języka XAML. XAML 2009 wprowadza kilka nowych dyrektyw i konstrukcji. Należą do nich [x:Arguments Dyrektywy;](xarguments-directive.md) [x:Dyrektywa FactoryMethod;](xfactorymethod-directive.md) [x:Rozszerzenie znaczników referencyjnych;](xreference-markup-extension.md) [x:Dyrektywa w sprawie argumentów za typem;](xtypearguments-directive.md) i wbudowanych typów dla pierwotnych języków wspólnych `x:Char`(na przykład ).

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Obsługa xaml 2009 w programach WPF i visual studio

W WPF WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest Skompilowany znaczników WPF. Markup-skompilowany XAML i BAML formie XAML obecnie nie obsługują XAML 2009 słowa kluczowe i funkcje języka.

Należy zauważyć, że istniejące techniki ładowania luźne XAML w WPF również możliwe ograniczenia zabezpieczeń i dostępu do typów CLR i systemu typów, które są bardziej restrykcyjne niż dla znaczników skompilowany XAML. Aby uzyskać więcej informacji, zobacz [Bezpieczeństwo (WPF)](../../framework/wpf/security-wpf.md) lub [WPF Security Strategy - Platform Security](../../framework/wpf/wpf-security-strategy-platform-security.md).

XAML 2009 wprowadza również dodatkowe funkcje, które modyfikują poprzednie konstrukcje XAML 2006 lub modyfikują podstawowe formularze znaczników.

### <a name="xkey-as-an-object-element"></a>x:Klucz jako element obiektu

XAML 2009 `x:Key` może obsługiwać jako obiekt (element właściwości, który ma wartość elementu obiektu); jednak XAML 2006 obsługiwane `x:Key` tylko jako atrybut. Zobacz sekcję "XAML 2009" [x:Key Directive](xkey-directive.md).

### <a name="xmlns-on-property-elements"></a>xmlns na elementach właściwości

XAML 2009 może obsługiwać definicje przestrzeni nazw XAML (xmlns) elementów właściwości; jednak XAML 2006 obsługuje tylko definicje xmlns na elementach obiektu.

### <a name="event-attributes"></a>Atrybuty zdarzeń

Dla atrybutów, które są wspierane przez zdarzenia, XAML 2006 zakłada, że kompilacja znaczników jest zaangażowany i przesyła zdarzenia do kompilacji znaczników. XAML 2009 obsługuje formularz znaczników, który przypomina rozszerzenie znaczników, który odracza okablowanie zdarzeń do czasu analizowania i ładowania xaml w czasie wykonywania. Jednak aplikacje WPF i scenariusze XAML dla WPF UI zazwyczaj nie używają tej możliwości. WPF WPF i jego XAML 2006 implementacji używa kombinacji okablowania obsługi zdarzeń dla routowanych zdarzeń zdefiniowanych na <xref:System.Windows.UIElement> poziomie i jego krok kompilatora znaczników dla większości jego przetwarzania atrybutów zdarzeń. Kompilator znaczników wstępnie przetwarza również wszystkie atrybuty zdarzeń znalezione w języku XAML, w którym akcje kompilacji deklarują, że używany jest kompilator znaczników.

## <a name="see-also"></a>Zobacz też

- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
