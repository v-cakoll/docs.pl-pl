---
title: Związane z kodem i XAML w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 6a47f5a93cb161c9a87df25403cc86247619cd81
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610531"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Związane z kodem i XAML w WPF
<a name="introduction"></a> Związane z kodem to termin używany do opisania kod, który jest sprzężony z obiektów zdefiniowanych przez kod znaczników, gdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona jest kompilowana do znaczników. W tym temacie opisano wymagania związane z kodem, a także mechanizm alternatywny wbudowanego kodu dla kodu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Ten temat zawiera następujące sekcje:  
  
- [Wymagania wstępne](#Prerequisites)  
  
- [Związane z kodem i języka XAML](#codebehind_and_the_xaml_language)  
  
- [Związane z kodem, program obsługi zdarzeń i klasy częściowej wymagania na platformie WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x: Code](#x_Code)  
  
- [Ograniczenia dotyczące kodu wbudowanego](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że użytkownik przeczytał [Przegląd XAML (WPF)](xaml-overview-wpf.md) i mają pewne podstawową wiedzę na temat [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] i programowanie zorientowane obiektowo.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Związane z kodem i języka XAML  
 Język XAML zawiera funkcje poziomu języka umożliwia kojarzenie pliki kodu z plikami znaczników, od strony pliku znaczników. W szczególności język XAML definiuje funkcje językowe [x: Class — dyrektywa](../../xaml-services/x-class-directive.md), [x: Subclass — dyrektywa](../../xaml-services/x-subclass-directive.md), i [x: classmodifier — dyrektywa](../../xaml-services/x-classmodifier-directive.md). Dokładnie jak kodu powinny być tworzone i sposobu integracji znaczników i kodu, nie jest częścią określa język XAML. Zostanie pozostawiony do struktur, takich jak WPF, aby określić, jak zintegrować kodu, w jaki sposób używać XAML w aplikacji i modele programowania i kompilacji akcje lub inne pomocy technicznej, wymaga to wszystko.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Związane z kodem, program obsługi zdarzeń i klasy częściowej wymagania na platformie WPF  
  
- Klasy częściowej musi pochodzić od typu, która będzie tworzyć kopię elementu głównego.  
  
- Należy pamiętać, że w obszarze domyślne zachowanie akcji kompilacji kompilacji znaczników puste tworzenia elementów pochodnych w definicji klasy częściowej stronie związanym z kodem. Wynik zakłada główny strony zapasowy typ jako podstawę do klasy częściowej, nawet jeśli nie określono. Jednakże opierając się na to zachowanie nie jest najlepszym rozwiązaniem.  
  
- Programy obsługi zdarzeń, napisany w związanym z kodem musi mieć metody wystąpień i nie może być metod statycznych. Te metody musi być zdefiniowany przez częściowe klasy w przestrzeni nazw CLR identyfikowane przez `x:Class`. Nie kwalifikujesz się do nazwy program obsługi zdarzeń w celu poinstruowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora do wyszukania program obsługi zdarzeń dla zdarzenia połączeń w zakresie innej klasy.  
  
- Program obsługi musi odpowiadać delegata odpowiedniego zdarzenia w systemie typów zapasowy.  
  
- W przypadku języka Microsoft Visual Basic w szczególności można użyć określonego języka `Handles` — słowo kluczowe, aby skojarzyć obsługi z wystąpień i zdarzenia w deklaracji program obsługi, zamiast dołączać obsługi za pomocą atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jednak ta technika mają pewne ograniczenia, ponieważ `Handles` — słowo kluczowe nie obsługuje wszystkich określonych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń, takie jak niektóre kierowane scenariuszy zdarzenia lub dołączone zdarzenia. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../xaml-services/x-code-intrinsic-xaml-type.md) element dyrektywy zdefiniowano [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. `x:Code` Dyrektywę element może zawierać wbudowany kod programowania. Kod, który jest zdefiniowany w tekście mogą wchodzić w interakcje z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na tej samej stronie. Poniższy przykład ilustruje wbudowanego kodu C#. Należy zauważyć, że kod znajduje się wewnątrz `x:Code` elementu i że kod musi być ujęte w `<CDATA[`... `]]>` jako znak ucieczki dla zawartości [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], dzięki czemu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora (interpretowanie albo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schematu lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schematu) nie będzie próbował nterpretowanie zawartości dosłownie jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Ograniczenia dotyczące kodu wbudowanego  
 Należy rozważyć unikanie lub ograniczenie używania kodu wbudowanego. Pod względem architektury i kodowania filozofia utrzymywanie separacji między znaczników i związane z kodem przechowuje role projektanta i deweloperów znacznie bardziej distinct. Na poziom bardziej technicznych, kodu napisanego dla kodu wbudowanego może być niewygodna do pisania, ponieważ zawsze pisania w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wygenerowane klasy częściowe i można używać tylko domyślne mapowania przestrzeni nazw XML. Ponieważ nie można dodać `using` instrukcji, muszą w pełni kwalifikujesz się do wielu wywołań interfejsu API, które wprowadzasz. Wartość domyślna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapowania zawierają najbardziej, ale nie wszystkie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzenie nazw, które znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawy; należy do pełnej kwalifikacji wywołania do typów i elementów członkowskich znajdujących się w innych przestrzeniach nazw środowiska CLR. Również nie można zdefiniować niczego poza częściowej klasy w kodzie wbudowane, a wszystkie jednostki kodu użytkownika, którego odwołujesz się musi istnieć jako członkowie lub zmiennej w generowanej klasie częściowej. Inne funkcje specyficzne dla języka programowania, takich jak makra lub `#ifdef` przed zmienne globalne i zmienne kompilacji, również nie są dostępne. Aby uzyskać więcej informacji, zobacz [x: Code, wewnętrzny typ XAML](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [x:Code, wewnętrzny typ XAML](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Kompilowanie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
