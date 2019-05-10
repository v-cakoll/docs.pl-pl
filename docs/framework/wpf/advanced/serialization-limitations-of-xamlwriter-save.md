---
title: Ograniczenia serializacji XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: bf752a5bd05d8a0601f3c1dcd53ab856315c0b84
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611764"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Ograniczenia serializacji XamlWriter.Save
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> Może służyć do serializacji zawartość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku. Istnieją jednak pewne ograniczenia istotne w dokładnie co to jest serializowana. W tym temacie opisano te ograniczenia i pewne ogólne zagadnienia.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Reprezentacja czasu wykonywania, nie czasu projektowania  
 Podstawowych założeń co to jest serializowany przez wywołanie <xref:System.Windows.Markup.XamlWriter.Save%2A> jest, że wynik będzie reprezentacja obiektu poddawanego serializacji w czasie wykonywania. Wiele właściwości czasu projektowania w oryginalnej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku może już zoptymalizowane pod kątem lub utraty do czasu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest ładowany jako obiekty w pamięci i nie są zachowywane podczas wywoływania <xref:System.Windows.Markup.XamlWriter.Save%2A> do serializacji. Zserializowany wynik jest skuteczne reprezentacja zbudowane drzewo logiczne aplikacji, ale nie oryginału [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który wytworzył. Te problemy stał się bardzo trudne w użyciu <xref:System.Windows.Markup.XamlWriter.Save%2A> serializacji w ramach obszerny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powierzchni projektowej.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializacja jest niezależna  
 Zserializowany danych wyjściowych <xref:System.Windows.Markup.XamlWriter.Save%2A> stanowi odrębną całość; wszystko, co jest serializowana znajduje się wewnątrz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jednostronicowej przy użyciu elementu z jednym elementem głównym, a nie odwołania zewnętrzne innych niż [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Na przykład jeśli strona odwołań do zasobów z zasobów aplikacji, pojawią się one tak, jakby były one składnika strony deserializowana.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Odwołania do rozszerzenia jest Wyłuskiwany.  
 Typowe odwołania do obiektów wykonanych przez różne formaty rozszerzenia znaczników, takich jak `StaticResource` lub `Binding`, będzie można usunąć odwołania w procesie serializacji. Zostały one już wyłuskiwany w czasie, które obiekty w pamięci zostały utworzone przez środowisko uruchomieniowe aplikacji i <xref:System.Windows.Markup.XamlWriter.Save%2A> logiki nie ponownie oryginalne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do przywrócenia tych odwołań do serializacji danych wyjściowych. Zawiesza się to potencjalnie w dowolnym z danymi lub zasobów uzyskane wartości wartość ostatnio używane przez reprezentacji środowiska wykonawczego z możliwością tylko ograniczony lub pośrednich do odróżnienia taka wartość od innych wartości ustawione lokalnie. Obrazy, również są serializowane jako odwołania do obiektu do obrazów występujących w projekcie, a nie jako oryginalnego odwołania do źródła utraty niezależnie od nazwy pliku lub [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pierwotnie odwoływano. Nawet zasoby zadeklarowane w obrębie tej samej stronie są widoczne Zserializowany do punktu, gdzie są przywoływane, a nie są zachowywane jako klucz kolekcji zasobów.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Obsługa zdarzeń jest nie są zachowywane  
 Podczas procedury obsługi zdarzeń, które są dodawane przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są serializowane, ich nie są zachowywane. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bez związanym z kodem (i również nie mechanizm powiązane x: Code) nie ma możliwości procedurach logiki czasu wykonywania serializacji. Ponieważ serializacji jest niezależna i ograniczone do drzewa logicznego, nie ma możliwości przechowywania procedury obsługi zdarzeń. W rezultacie atrybutach programu obsługi zdarzeń, zarówno dla samego atrybutu, jak i wartość ciągu, która nazywa programu obsługi są usuwane z danych wyjściowych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Realistyczne scenariusze użycia xamlwriter.Save  
 Ograniczenia wymienione w tym miejscu są dość znaczną, nadal istnieją kilka odpowiednie scenariusze użycia <xref:System.Windows.Markup.XamlWriter.Save%2A> do serializacji.  
  
- Wektor lub danych wyjściowych graficznego: Dane wyjściowe renderowanych obszar może służyć do odtworzenia tego samego wektor lub grafiki, gdy ponownie załadowany.  
  
- Rozbudowane dokumenty tekstowe i przepływ: Tekst i wszystkie element formatowania i elementu zawierania znajdujący się w nim zostaną zachowane w danych wyjściowych. Może to być przydatne w przypadku mechanizmy, które są w przybliżeniu funkcja Schowka.  
  
- Zachowywanie danych obiektu biznesowych: Jeśli są przechowywane dane w niestandardowych elementach, takich jak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane tak długo, jak obiekty firm wykonaj podstawowe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reguły, takie jak niestandardowe konstruktorów i konwersji wartości właściwości przez odwołanie, te obiekty firm mogą być perpetuated za pomocą serializacji.
