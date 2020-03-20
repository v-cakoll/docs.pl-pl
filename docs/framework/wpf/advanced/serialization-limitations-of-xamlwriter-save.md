---
title: Ograniczenia serializacji XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174371"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Ograniczenia serializacji XamlWriter.Save
Interfejs <xref:System.Windows.Markup.XamlWriter.Save%2A> API może służyć do serializacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] aplikacji jako pliku. Istnieją jednak pewne znaczące ograniczenia w dokładnie to, co jest serializowane. Te ograniczenia i niektóre ogólne zagadnienia są udokumentowane w tym temacie.  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>Reprezentacja w czasie wykonywania, a nie reprezentacja czasu projektowania  
 Podstawową filozofią tego, co jest <xref:System.Windows.Markup.XamlWriter.Save%2A> serializowane przez wywołanie jest to, że wynik będzie reprezentacja obiektu serializowane, w czasie wykonywania. Wiele właściwości czasu projektowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oryginalnego pliku może być już zoptymalizowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub utracone przez czas, który jest ładowany jako obiekty w pamięci i nie są zachowywane podczas wywoływania <xref:System.Windows.Markup.XamlWriter.Save%2A> serializacji. Wynik serializowany jest skuteczną reprezentacją skonstruowanego drzewa logicznego aplikacji, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ale niekoniecznie oryginalnego, który ją wyprodukował. Te problemy sprawiają, że <xref:System.Windows.Markup.XamlWriter.Save%2A> bardzo trudno jest używać [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] serializacji jako części obszernej powierzchni projektowej.  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>Serializacja jest niezależna  
 Serializowane dane <xref:System.Windows.Markup.XamlWriter.Save%2A> wyjściowe są samodzielne; wszystko, co jest serializowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zawarte wewnątrz jednej strony, z jednym elementem głównym i nie ma odniesień zewnętrznych innych niż identyfikatory URI. Na przykład jeśli strona odwołuje się do zasobów z zasobów aplikacji, będą one wyświetlane tak, jakby były one składnikiem strony serializowane.  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>Odwołania do rozszerzenia są wyłuskiwane  
 Typowe odwołania do obiektów dokonywanych przez różne formaty rozszerzeń znaczników, takie jak `StaticResource` lub `Binding`, będą wyłuskiwane przez proces serializacji. Zostały one już wyłuskiwane w czasie, gdy obiekty w pamięci <xref:System.Windows.Markup.XamlWriter.Save%2A> zostały utworzone przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] środowisko wykonawcze aplikacji, a logika nie ponownie oryginał, aby przywrócić takie odwołania do danych wyjściowych serializowanych. To potencjalnie zawiesza wszelkie databound lub zasób uzyskana wartość jest wartość ostatnio używana przez reprezentację w czasie wykonywania, tylko ograniczoną lub pośrednią możliwość odróżnienia takiej wartości od innych wartości ustawionych lokalnie. Obrazy są również serializowane jako odwołania do obiektów do obrazów, które istnieją w projekcie, a nie jako oryginalne odwołania źródłowe, tracąc dowolną nazwę pliku lub identyfikator URI pierwotnie odwołuje. Nawet zasoby zadeklarowane w tej samej stronie są postrzegane serializowane do punktu, do którego się odwoływano, a nie są zachowywane jako klucz kolekcji zasobów.  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>Obsługa zdarzeń nie jest zachowywana  
 Gdy programy obsługi zdarzeń, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] które są dodawane za pośrednictwem są serializowane, nie są zachowywane. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bez kodu w tyle (a także bez powiązanego mechanizmu x:Code) nie ma możliwości serializacji logiki proceduralnej środowiska uruchomieniowego. Ponieważ serializacja jest niezależna i ograniczona do drzewa logicznego, nie ma możliwości przechowywania programów obsługi zdarzeń. W rezultacie atrybuty obsługi zdarzeń, zarówno sam atrybut, jak i wartość ciągu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]który nazywa program obsługi, są usuwane z danych wyjściowych.  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Realistyczne scenariusze użycia XAMLWriter.Save  
 Chociaż ograniczenia wymienione w tym miejscu są dość istotne, <xref:System.Windows.Markup.XamlWriter.Save%2A> nadal istnieje kilka odpowiednich scenariuszy do użycia do serializacji.  
  
- Dane wyjściowe wektorowe lub graficzne: Dane wyjściowe renderowanego obszaru mogą być używane do odtworzenia tego samego wektora lub grafiki po ponownym załadowaniu.  
  
- Tekst sformatowy i dokumenty przepływu: Formatowanie tekstu i całego elementu oraz hermetyzacja elementów w nim są zachowywane w danych wyjściowych. Może to być przydatne w przypadku mechanizmów przybliżać funkcjonalność schowka.  
  
- Zachowywanie danych obiektów biznesowych: Jeśli dane są przechowywane w elementach niestandardowych, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] takich jak dane XML, o ile obiekty biznesowe są zgodne z podstawowymi regułami, takimi jak dostarczanie konstruktorów niestandardowych i konwersja dla wartości właściwości według odwołań, te obiekty biznesowe mogą być utrwalane przez serializację.
