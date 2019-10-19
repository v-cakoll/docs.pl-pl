---
title: Ograniczenia serializacji XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 0416b92a6264e6a8261355197b4ab2fa61f80ef2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582591"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Ograniczenia serializacji XamlWriter.Save
@No__t_0 interfejsu API może służyć do serializacji zawartości [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji jako pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Istnieją jednak pewne istotne ograniczenia w dokładnie tym, co jest serializowane. Te ograniczenia i niektóre ogólne zagadnienia zostały udokumentowane w tym temacie.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Reprezentacja czasu wykonywania, nie projektowania  
 Podstawowa stawka co jest serializowana przez wywołanie <xref:System.Windows.Markup.XamlWriter.Save%2A> polega na tym, że wynik będzie reprezentacją serializowanego obiektu w czasie wykonywania. Wiele właściwości czasu projektowania oryginalnego pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] można już zoptymalizować lub stracić przez czas, w którym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest załadowana jako obiekty w pamięci, i nie są zachowywane po wywołaniu <xref:System.Windows.Markup.XamlWriter.Save%2A> do serializacji. Serializowany wynik jest efektywną reprezentacją skonstruowanego drzewa logicznego aplikacji, ale niekoniecznie oryginalny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], który go wygenerował. Te problemy utrudniają używanie serializacji <xref:System.Windows.Markup.XamlWriter.Save%2A> w ramach rozbudowanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powierzchni projektowej.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializacja jest niezależna  
 Serializowane dane wyjściowe <xref:System.Windows.Markup.XamlWriter.Save%2A> są samodzielne; wszystko, co jest serializowane, znajduje się w obrębie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pojedynczej strony, z pojedynczym elementem głównym, i nie zawiera odwołań zewnętrznych innych niż identyfikatory URI. Na przykład, jeśli strona odwołuje się do zasobów z zasobów aplikacji, pojawi się tak, jakby były składnikiem serializowanej strony.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Odwołania do rozszerzeń są odwołujące się  
 Typowe odwołania do obiektów wykonywanych przez różne formaty rozszerzeń znaczników, takie jak `StaticResource` lub `Binding`, zostaną wydzielone przez proces serializacji. Zostały one już wykorzystane w chwili, gdy obiekty w pamięci zostały utworzone przez środowisko uruchomieniowe aplikacji, a logika <xref:System.Windows.Markup.XamlWriter.Save%2A> nie odwiedza oryginalny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w celu przywrócenia takich odwołań do serializowanych danych wyjściowych. Może to spowodować, że wszystkie wartości związane z danymi lub zasobami uzyskanymi jako wartość ostatnio używane przez reprezentację w czasie wykonywania, z ograniczoną lub pośrednią możliwością odróżnienia takiej wartości od innych ustawionych wartości. Obrazy są również serializowane jako odwołania do obiektów do obrazów, ponieważ istnieją w projekcie, a nie jako pierwotne odwołania do źródła, tracąc niezależnie do tego odwołanie do nazwy pliku lub identyfikatora URI. Nawet zasoby zadeklarowane na tej samej stronie są wyświetlane jako serializacji do punktu, w którym zostały przywołane, a nie zachowywane jako klucz kolekcji zasobów.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Obsługa zdarzeń nie jest zachowywana  
 Gdy programy obsługi zdarzeń dodawane za poorednictwem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są serializowane, nie są zachowywane. nie ma żadnego sposobu serializacji logiki proceduralnej środowiska uruchomieniowego, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bez kodu (i bez powiązanego mechanizmu x:Code). Ponieważ Serializacja jest samodzielna i ograniczona do drzewa logicznego, nie ma możliwości przechowywania obsługi zdarzeń. W związku z tym atrybuty programu obsługi zdarzeń, zarówno sam atrybut, jak i wartość ciągu, która nazywają procedurę obsługi, są usuwane z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] danych wyjściowych.  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Realistyczne scenariusze korzystania z XAMLWriter. Save  
 Chociaż ograniczenia wymienione w tym miejscu są dość znaczące, nadal istnieje kilka odpowiednich scenariuszy dla serializacji <xref:System.Windows.Markup.XamlWriter.Save%2A>.  
  
- Wektor lub graficzne wyjście: dane wyjściowe renderowanego obszaru mogą być używane do odtwarzania tego samego wektora lub grafiki po ponownym załadowaniu.  
  
- Teksty tekstu sformatowanego i przepływu: tekst i wszystkie elementy formatowania elementów i zawartych w nim elementów są zachowywane w danych wyjściowych. Może to być przydatne w przypadku mechanizmów, które mają przybliżoną funkcjonalność Schowka.  
  
- Zachowywanie danych obiektu biznesowego: Jeśli dane są przechowywane w niestandardowych elementach, takich jak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane, tak długo, jak obiekty biznesowe są zgodne z podstawowymi regułami [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], takimi jak udostępnianie niestandardowych konstruktorów i konwersja na wartości właściwości przez odwołanie, te firmy obiekty mogą być perpetuated przez serializację.
