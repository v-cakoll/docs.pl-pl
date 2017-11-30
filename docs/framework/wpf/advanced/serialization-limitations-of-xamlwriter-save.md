---
title: Ograniczenia serializacji XamlWriter.Save
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06033c6a753dd567f613f0b848e806dfa14ee77d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Ograniczenia serializacji XamlWriter.Save
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> Może służyć do serializacji zawartość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku. Istnieją pewne ważne ograniczenia dotyczące dokładnie co serializacji. W tym temacie opisano następujące ograniczenia oraz pewne ogólne zagadnienia.  
  
 
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Reprezentacja w czasie wykonywania, nie czasu projektowania  
 Co to jest serializowany przez wywołanie do podstawowych założeń <xref:System.Windows.Markup.XamlWriter.Save%2A> jest, że wynik będzie reprezentacja obiektu poddawanego serializacji w czasie wykonywania. Wiele właściwości czasu projektowania oryginału [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku może już zoptymalizowany lub utracone w czasie który [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest załadowany jako obiekty w pamięci i nie są zachowywane podczas wywoływania <xref:System.Windows.Markup.XamlWriter.Save%2A> do serializacji. Wynik serializacji jest skuteczne reprezentację skonstruowane drzewa logicznego aplikacji, ale nie oryginału [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który go utworzył. Te problemy stał się bardzo trudne do użycia <xref:System.Windows.Markup.XamlWriter.Save%2A> serializacji jako część obszerny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powierzchnię projektu.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializacja jest niezależne  
 Serializowane dane wyjściowe <xref:System.Windows.Markup.XamlWriter.Save%2A> stanowi całość; wszystko, co jest serializowany znajduje się wewnątrz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie, przy użyciu elementu z jednym elementem głównym, a nie odwołań zewnętrznych innych niż [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Na przykład jeśli stronie odwołuje się do zasobów z zasobami aplikacji, te będą wyświetlane, tak, jakby były składnika strony serializowana.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Odwołania do rozszerzenia jest Wyłuskiwany  
 Typowe odwołania do obiektów wprowadzone przez różne formaty rozszerzenia znaczników, takich jak `StaticResource` lub `Binding`, będzie można usunąć odwołania przez proces serializacji. Zostały one już wyłuskiwany w czasie obiektów w pamięci zostały utworzone przez środowisko uruchomieniowe aplikacji i <xref:System.Windows.Markup.XamlWriter.Save%2A> logiki nie ponownie oryginalnej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do przywrócenia takich odwołań do serializacji danych wyjściowych. Zawiesza się to potencjalnie w dowolnej z danymi lub zasobu uzyskać wartość ma być wartość ostatnio używanych przez reprezentacja czasu wykonywania tylko ograniczony lub pośredniego możliwość rozróżnienia takiej wartości z innych wartości ustawić lokalnie. Obrazy są również serializowane jako obiekt odwołania do obrazów, istniejących w projekcie, a nie jako oryginalnego źródła odniesienia, utraty niezależnie od nazwy pliku lub [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pierwotnie odwoływano. Nawet zasoby zadeklarowane w obrębie tej samej stronie są widoczne Zserializowany do punktu, w którym one pojawiały się odniesienia, zamiast został zachowany jako klucz kolekcji zasobów.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Obsługa zdarzeń jest nie są zachowywane  
 Podczas obsługi zdarzeń, które zostały dodane za pośrednictwem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są serializowane, ich nie są zachowywane. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bez kodu powiązanego (i również mechanizm pokrewne x: Code) nie ma możliwości szeregowania logiki procedurach środowiska wykonawczego. Serializacja jest niezależna i ograniczona do drzewa logicznego, nie istnieje żadne funkcje do przechowywania obsługi zdarzeń. W związku z tym atrybutów programu obsługi zdarzeń, zarówno atrybut sam, jak i wartości ciągu, których nazwy programu obsługi są usuwane z danych wyjściowych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Scenariusze realistyczne XAMLWriter.Save do użytku  
 Podczas gdy ograniczenia wymienione w tym miejscu jest dość znaczące, istnieją kilka scenariuszy odpowiednie dla przy użyciu <xref:System.Windows.Markup.XamlWriter.Save%2A> do serializacji.  
  
-   Wektor lub graficzne dane wyjściowe: dane wyjściowe renderowanych obszaru może służyć do odtworzenia tego samego wektor lub grafiki podczas załadowana ponownie.  
  
-   Sformatowanego tekstu i przepływu dokumentów: tekst i wszystkie elementu formatowania i elementu zawierania w niej jest zachowane w danych wyjściowych. Może to być przydatne w przypadku mechanizmy, które przybliżona funkcji Schowka.  
  
-   Zachowując dane obiektu biznesowe: Jeśli przechowywanych danych w niestandardowe elementy, takie jak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, tak długo, jak obiektów biznesowych należy wykonać podstawowe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reguł, takich jak niestandardowe konstruktory i konwersji wartości właściwości przez odwołanie, te obiekty firm mogą perpetuated za pomocą serializacji.
