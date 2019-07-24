---
title: Związane z kodem i XAML w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401610"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Związane z kodem i XAML w WPF
<a name="introduction"></a>Kod jest terminem używanym do opisania kodu, który jest dołączany do obiektów zdefiniowanych przez znacznik, gdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona jest skompilowana przy użyciu znaczników. W tym temacie opisano wymagania dotyczące kodu, a także alternatywny mechanizm kodu wbudowanego dla kodu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Ten temat zawiera następujące sekcje:  
  
- [Wymagania wstępne](#Prerequisites)  
  
- [Kod źródłowy i język XAML](#codebehind_and_the_xaml_language)  
  
- [Powiązane z kodem, procedury obsługi zdarzeń i częściowe wymagania klas w WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Ograniczenia kodu wbudowanego](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że użytkownik przeczytał [Omówienie XAML (WPF)](xaml-overview-wpf.md) i ma pewną podstawową wiedzę na temat środowiska CLR i programowania zorientowanego obiektowo.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Kod źródłowy i język XAML  
 Język XAML zawiera funkcje poziomu języka, które umożliwiają kojarzenie plików kodu z plikami znaczników, po stronie pliku znaczników. W każdym przypadku język XAML definiuje funkcje języka [X:Class dyrektywy](../../xaml-services/x-class-directive.md), [dyrektywy X:Subclass —](../../xaml-services/x-subclass-directive.md)i [dyrektywy x:ClassModifier —](../../xaml-services/x-classmodifier-directive.md). Dokładnie jak kod powinien być tworzony i jak zintegrować znaczniki i kod, nie jest częścią tego, co określa język XAML. Jest ona pozostała do struktur, takich jak WPF, aby określić, jak zintegrować kod, jak używać języka XAML w modelach aplikacji i programowania, a także akcji kompilacji lub innych obsługi wymaganych przez wszystkie te wymagania.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Powiązane z kodem, procedury obsługi zdarzeń i częściowe wymagania klas w WPF  
  
- Klasa częściowa musi pochodzić od typu, który wykonuje kopię zapasową elementu głównego.  
  
- Należy zauważyć, że pod domyślnym zachowaniem akcji kompilacji znaczników można pozostawić wartość pochodną pustą w definicji klasy częściowej po stronie kodu. Skompilowany wynik przyjmie, że typ kopii zapasowej elementu głównego strony będzie podstawą dla klasy częściowej, nawet jeśli nie zostanie określony. Nie jest to jednak najlepsze rozwiązanie polegające na tym zachowaniu.  
  
- Procedury obsługi zdarzeń zapisywane w kodzie muszą być metodami wystąpień i nie mogą być metodami statycznymi. Te metody muszą być zdefiniowane przez klasę częściową w przestrzeni nazw CLR identyfikowanej `x:Class`przez. Nie można zakwalifikować nazwy programu obsługi zdarzeń, aby nakazać [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorowi wyszukanie obsługi zdarzeń dla okablowania zdarzeń w innym zakresie klasy.  
  
- Program obsługi musi być zgodny z delegatem dla odpowiedniego zdarzenia w systemie typu zapasowego.  
  
- W przypadku języka Microsoft Visual Basic w konkretnym przypadku można użyć słowa kluczowego `Handles` specyficznego dla języka w celu skojarzenia programów obsługi z wystąpieniami i zdarzeniami w deklaracji procedury obsługi, zamiast dołączać obsługi z atrybutami w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak ta technika ma pewne ograniczenia, ponieważ `Handles` słowo kluczowe nie może obsługiwać wszystkich konkretnych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu zdarzeń, takich jak określone scenariusze zdarzeń kierowanych lub zdarzenia dołączone. Aby uzyskać szczegółowe informacje, zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:Code](../../xaml-services/x-code-intrinsic-xaml-type.md) jest elementem dyrektywy zdefiniowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Element `x:Code` dyrektywy może zawierać wbudowany kod programistyczny. Kod, który jest zdefiniowany w tekście, może współdziałać z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na tej samej stronie. Poniższy przykład ilustruje kod wbudowany C# . Zauważ, że kod znajduje się wewnątrz `x:Code` elementu i że kod musi być ujęty w `<CDATA[`... [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]aby wypróbować zawartość [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]dla programu, dzięki czemu procesor (interpretując schemat lub schemat) nie będzie próbować interpretować zawartości dosłownie jako. `]]>`  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Ograniczenia kodu wbudowanego  
 Należy rozważyć uniknięcie lub ograniczenie użycia kodu wbudowanego. W zakresie architektury i zasad kodowania, utrzymując rozdzielenie między adiustacją i kodem, utrzymuje znacznie więcej odrębnych ról projektanta i dewelopera. Na wyższym poziomie technicznym kod, który można napisać dla kodu wbudowanego może być niewygodna do zapisu, ponieważ zawsze piszesz do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wygenerowanej klasy częściowej i można używać tylko domyślnych mapowań przestrzeni nazw XML. Ponieważ nie można dodawać `using` instrukcji, należy w pełni kwalifikować wiele wywołań interfejsu API. Mapowania domyślne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obejmują większość, ale nie wszystkie przestrzenie nazw środowiska CLR, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] znajdują się w zestawach; trzeba będzie w pełni kwalifikować wywołania do typów i członków zawartych w innych przestrzeniach nazw środowiska CLR. Nie można również definiować niczego poza klasą częściową w kodzie wbudowanym, a wszystkie jednostki kodu użytkownika, do których się odwołuje, muszą istnieć jako element członkowski lub zmienna w wygenerowanej klasie częściowej. Inne funkcje programistyczne specyficzne dla języka, takie jak `#ifdef` makra lub zmienne globalne lub zmienne kompilacji, również są niedostępne. Aby uzyskać więcej informacji, zobacz [X:Code wewnętrzny typ XAML](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [x:Code, wewnętrzny typ XAML](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Kompilowanie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
