---
title: Związane z kodem i XAML w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 09d4f010ca53c5e3d2d9dede172e7ae2102261b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="code-behind-and-xaml-in-wpf"></a>Związane z kodem i XAML w WPF
<a name="introduction"></a> CodeBehind to termin używany do opisania kod, który jest połączony z obiektów zdefiniowanych przez kod znaczników, gdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona jest skompilowana znaczników. W tym temacie opisano wymagania związane z kodem, a także mechanizm alternatywnych wbudowanego kodu dla kodu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Wymagania wstępne](#Prerequisites)  
  
-   [Związane z kodem i języka XAML](#codebehind_and_the_xaml_language)  
  
-   [Związane z kodem, program obsługi zdarzeń i wymagania częściowej klasy na platformie WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x: Code](#x_Code)  
  
-   [Ograniczenia kodu wbudowanego](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że znasz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) i mają pewne podstawową wiedzę na temat [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] i programowanie zorientowane obiektowo.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Związane z kodem i języka XAML  
 Języka XAML zawiera funkcje poziom języka, które umożliwiają skojarzenia plików kodu z pliki znaczników ze strony pliku znaczników. W szczególności języka XAML definiuje funkcje językowe [dyrektywy x: Class](../../../../docs/framework/xaml-services/x-class-directive.md), [dyrektywy x: Subclass](../../../../docs/framework/xaml-services/x-subclass-directive.md), i [x: classmodifier — dyrektywa](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). Dokładnie sposób będą tworzone kod i sposobu integracji znaczników i kodu, nie jest częścią określa języka XAML. Zostanie pozostawiony do struktury, takich jak WPF w celu ustalenia sposobu integracji kod, jak do użycia w aplikacji oraz modele programowania i kompilacji XAML akcje lub inne obsługuje który wszystkie wymagane.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Związane z kodem, program obsługi zdarzeń i wymagania częściowej klasy na platformie WPF  
  
-   Klasy częściowej musi pochodzić z typu, aby utworzyć kopię zapasową elementu głównego.  
  
-   Należy pamiętać, że w obszarze domyślne zachowanie akcji kompilacji kompilacji znaczników puste wyprowadzenia w definicji klasy częściowej po stronie związane z kodem. Wynik skompilowanych przyjmie głównego strony zapasowy typ jako podstawę do klasy częściowej nawet wtedy, gdy nie określono. Jednak zależne to zachowanie nie jest najlepszym rozwiązaniem.  
  
-   Obsługi zdarzeń zostanie zapisany w kodzie musi być wystąpieniem metody i nie może być metod statycznych. Te metody musi być zdefiniowana w klasie częściowej w przestrzeni nazw CLR identyfikowane przez `x:Class`. Nazwa programu obsługi zdarzeń, aby spowodować, żeby nie może kwalifikować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora do wyszukania programu obsługi zdarzeń dla połączeń zdarzeń w zakresie inną klasę.  
  
-   Program obsługi muszą być zgodne delegata zdarzenia odpowiedniego typu bazowego systemu.  
  
-   W przypadku języka Microsoft Visual Basic w szczególności można użyć określonego języka `Handles` — słowo kluczowe do skojarzenia z wystąpień i zdarzeń w deklaracji obsługi zamiast Dołączanie programów obsługi z atrybutów w obsługi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak ta metoda ma pewne ograniczenia, ponieważ `Handles` — słowo kluczowe nie może obsługiwać wszystkie z określonych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń, takie jak niektóre trasę scenariusze zdarzeń lub dołączone zdarzenia. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługi zdarzeń WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) jest zdefiniowany element dyrektywy w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. `x:Code` Dyrektywy elementu mogą zawierać wbudowanego kodu programowania. Kod, który zdefiniowano w tekście jest zakłócają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na tej samej stronie. Poniższy przykład przedstawia wbudowanego kodu C#. Należy zauważyć, że kod znajduje się wewnątrz `x:Code` elementu i że kod muszą być ujęte w `<CDATA[`... `]]>` ucieczki zawartości [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], dzięki czemu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora (interpretowanie albo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schematu) nie będzie próbował zinterpretować zawartości dosłownie jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Ograniczenia kodu wbudowanego  
 Należy rozważyć unikanie lub ograniczenie używania kodu wbudowanego. Pod względem architektury i kodowania zasady klas utrzymania rozdzielenie znaczników i kodu powiązanego przechowuje role projektanta i deweloperów bardziej distinct. Na poziom bardziej technicznych, pisania kodu wbudowanego kodu może być nieodpowiednich do zapisu, ponieważ zawsze pisania do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wygenerowane klasy częściowe i można używać tylko domyślne mapowania przestrzeni nazw XML. Ponieważ nie można dodać `using` instrukcje, użytkownik musi pełnej kwalifikacji wiele [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wywołania wprowadzone. Wartość domyślna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapowania zawierają najbardziej, ale nie wszystkie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzenie nazw, które znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawy; należy do pełnej kwalifikacji wywołania do typów i członków zawarte w innych przestrzeniach nazw CLR. Można także nie można zdefiniować niczego poza klasy częściowej w kodu wbudowanego i wszystkich jednostek kodu użytkownika, który odwołuje się musi istnieć jako element członkowski lub zmiennej w ramach wygenerowanej częściowej klasy. Inne funkcje specyficzne dla języka programowania, takich jak makra lub `#ifdef` przed zmienne globalne i zmienne kompilacji, również nie są dostępne. Aby uzyskać więcej informacji, zobacz [x: Code wewnętrznego typu XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code, wewnętrzny typ XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
