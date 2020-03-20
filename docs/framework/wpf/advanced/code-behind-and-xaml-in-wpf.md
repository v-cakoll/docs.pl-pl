---
title: Kod-Behind i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145348"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Związane z kodem i XAML w WPF
<a name="introduction"></a>Code-behind jest terminem używanym do opisywania kodu, który jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] połączony z obiektami zdefiniowanymi znacznikami, gdy strona jest skompilowana znacznikami. W tym temacie opisano wymagania dotyczące kod-behind, jak również [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]alternatywny mechanizm kodu wbudowanego dla kodu w .  
  
 Ten temat zawiera następujące sekcje:  
  
- [Wymagania wstępne](#Prerequisites)  
  
- [Kod-Behind i język XAML](#codebehind_and_the_xaml_language)  
  
- [Wymagania dotyczące kodów, obsługi zdarzeń i częściowej klasy w programie WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Kod](#x_Code)  
  
- [Ograniczenia kodu wbudowanego](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że zapoznałeś się [z omówieniem XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) i masz podstawową wiedzę na temat programu CLR i programowania obiektowego.  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>Kod-Behind i język XAML  
 Język XAML zawiera funkcje na poziomie języka, które umożliwiają kojarzenie plików kodu z plikami znaczników od strony pliku znaczników. W szczególności język XAML definiuje funkcje języka [x:Class Directive](../../../desktop-wpf/xaml-services/xclass-directive.md), [x:Subclass Directive](../../../desktop-wpf/xaml-services/xsubclass-directive.md)i [x:ClassModifier Directive](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). Dokładnie, jak kod powinien być produkowany i jak zintegrować znaczników i kodu, nie jest częścią tego, co określa język XAML. Pozostaje do struktur, takich jak WPF, aby określić, jak zintegrować kod, jak używać XAML w aplikacji i modeli programowania i akcji kompilacji lub innej pomocy technicznej, która wymaga tego wszystkiego.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Wymagania dotyczące kodów, obsługi zdarzeń i częściowej klasy w programie WPF  
  
- Klasa częściowa musi pochodzić od typu, który wspiera element główny.  
  
- Należy zauważyć, że w domyślnym zachowaniu akcji kompilacji znaczników można pozostawić wynikowe puste w definicji klasy częściowej po stronie związanej z kodem. Skompilowany wynik przyjmie typ kopii katalogu głównego strony jako podstawa dla klasy częściowej, nawet jeśli nie została określona. Jednak poleganie na tym zachowaniu nie jest najlepszym rozwiązaniem.  
  
- Programy obsługi zdarzeń, które piszesz w kodzie posuwu musi być metody wystąpienia i nie mogą być metody statyczne. Metody te muszą być zdefiniowane przez klasę częściową `x:Class`w obszarze nazw CLR identyfikowaną przez . Nie można zakwalifikować nazwę programu obsługi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdarzeń, aby poinstruować procesora, aby wyszukać program obsługi zdarzeń dla okablowania zdarzeń w zakresie innej klasy.  
  
- Program obsługi musi być zgodny delegata dla odpowiedniego zdarzenia w systemie typu kopii zapasowej.  
  
- W szczególności w języku microsoft visual basic można `Handles` użyć słowa kluczowego specyficznego dla języka do skojarzenia programów obsługi z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]wystąpieniami i zdarzeniami w deklaracji obsługi, zamiast dołączania programów obsługi z atrybutami w programie . Jednak ta technika ma pewne `Handles` ograniczenia, ponieważ słowo kluczowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje wszystkich określonych funkcji systemu zdarzeń, takich jak niektóre scenariusze zdarzeń kierowanych lub dołączone zdarzenia. Aby uzyskać szczegółowe informacje, zobacz [Visual Basic i Obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:Kod  
 [x:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) jest elementem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dyrektywy zdefiniowanym w . Element `x:Code` dyrektywy może zawierać wbudowany kod programowania. Kod, który jest zdefiniowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] linii może wchodzić w interakcje z na tej samej stronie. Poniższy przykład ilustruje wbudowany kod języka C#. Należy zauważyć, że `x:Code` kod znajduje się wewnątrz elementu `<CDATA[`i że kod musi być otoczony przez ... `]]>` aby uniknąć zawartości dla XML, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tak aby procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (interpretujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schemat lub schemat) nie próbował interpretować zawartości dosłownie jako XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>Ograniczenia kodu wbudowanego  
 Należy rozważyć unikanie lub ograniczanie użycia kodu wbudowanego. Pod względem architektury i filozofii kodowania, utrzymanie separacji między znaczników i związane z kodem zachowuje projektanta i dewelopera role znacznie bardziej różne. Na poziomie bardziej technicznym kod, który piszesz dla kodu wbudowanego może być [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] niewygodne do zapisu, ponieważ są zawsze zapisywania w klasie częściowej generowane i można używać tylko domyślne mapowania obszaru nazw XML. Ponieważ nie `using` można dodać instrukcji, należy w pełni zakwalifikować wiele wywołań interfejsu API, które można wykonać. Domyślne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapowania obejmują większość, ale nie wszystkie obszary [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nazw CLR, które są obecne w zestawach; musisz w pełni zakwalifikować wywołania do typów i elementów członkowskich zawartych w innych przestrzeniach nazw CLR. Nie można również zdefiniować niczego poza klasy częściowej w kodzie wbudowanym i wszystkie jednostki kodu użytkownika, do których odwołuje się musi istnieć jako element członkowski lub zmienna w wygenerowanej klasie częściowej. Inne funkcje programowania specyficzne dla `#ifdef` języka, takie jak makra lub zmienne globalne lub zmienne kompilacji, również nie są dostępne. Aby uzyskać więcej informacji, zobacz [x:Kod intrinsic XAML Type](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code — Typ funkcji XAML](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Kompilowanie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
