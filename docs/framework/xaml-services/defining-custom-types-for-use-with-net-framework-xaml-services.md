---
title: "Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7cce479c7c7a5f6c7112f08f1e15f3bc7e4d366
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML
Zdefiniuj niestandardowe typy obiektów biznesowych lub typów, które nie mają zależności na określonych platformach, brak niektórych najlepszych rozwiązań dotyczących XAML, możesz wykonać. Po wykonaniu tych rozwiązań usług .NET Framework XAML i jego czytników XAML i zapisywania XAML może odnajdywanie właściwości XAML danego typu i nadaj odpowiednie reprezentacja w strumień węzłów XAML, przy użyciu systemu typu XAML. W tym temacie opisano najlepsze rozwiązania dotyczące definicji typu, elementu członkowskiego definicje i przypisywanie CLR typów lub elementy członkowskie.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Konstruktor wzorców i definicji typu dla XAML  
 Aby można utworzyć wystąpienia jako elementu obiektu w języku XAML, niestandardowe klasy musi spełniać następujące wymagania:  
  
-   Niestandardowej klasy muszą być publiczne i musi uwidaczniać domyślnego (bezparametrowego) konstruktora publicznego. (Patrz poniżej sekcji, aby uzyskać informacje dotyczące struktury).  
  
-   Niestandardowej klasy nie może być klasą zagnieżdżoną. Nadmiarowe "kropka" w ścieżce pełnej nazwy sprawia, że dzielenia obszaru nazw klasy jest niejednoznaczne i koliduje z innymi funkcjami języka XAML, takie jak dołączone właściwości.  
  
 Jeśli obiekt można wdrożyć jako elementu obiektu, utworzony obiekt wypełnić formularzu elementu właściwości właściwości przyjmujących obiektu jako jego typ podstawowy.  
  
 Nadal można podać wartości obiektu dla typów, które nie spełniają tych kryteriów, jeśli włączysz konwertera wartości. Aby uzyskać więcej informacji, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury mogą zawsze być skonstruowany w XAML, zgodnie z definicją CLR. Jest to spowodowane kompilatora CLR niejawnie tworzy konstruktora domyślnego dla struktury. Ten konstruktor inicjuje wszystkich wartości właściwości do wartości domyślnych.  
  
 W niektórych przypadkach konstrukcji domyślne zachowanie dla struktury nie jest pożądane. Może to być spowodowane struktury jest przeznaczony do wypełniania wartościami oraz funkcja koncepcyjnie jako Unii. Jako Unii wartości zawartych w niej mogą być interpretacje wykluczają się wzajemnie, a w związku z tym żaden z jego właściwości nie jest do ustawienia. Na przykład struktury w słownictwa WPF <xref:System.Windows.GridLength>. Te struktury powinien implementować konwertera typów, aby wartości może zostać wyrażona w formie atrybutu, za pomocą Konwencji ciągu utworzyć inną interpretacje lub tryby wartości struktury. Struktura również powinny ujawniać podobne zachowanie dla konstrukcji kodu za pomocą konstruktora domyślnego z systemem innym niż.  
  
### <a name="interfaces"></a>Interfejsy  
 Interfejsy może służyć jako typów podstawowych elementów członkowskich. System typów języka XAML sprawdza listy można przypisać i oczekuje, że obiekt, który został dostarczony jako wartość można przypisać do interfejsu. Nie ma żadnych koncepcji jak interfejsu muszą być przedstawione jako typu XAML tak długo, jak można przypisać typu odpowiednich spełnia wymagania dotyczące konstrukcji języka XAML.  
  
### <a name="factory-methods"></a>Metody fabryki  
 Fabryka metody są funkcją języka XAML 2009. Modyfikują zasady XAML, że obiekty muszą mieć domyślnych konstruktorów. W tym temacie nie opisano metody fabryki. Zobacz [x: factorymethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Wyliczenia mają zachowanie konwersji typu macierzystego języka XAML. Wyliczenie nazwy stałej określone w języku XAML są nazwy zostały rozstrzygnięte na typ podstawowy wyliczenia i zwracać wartość wyliczenia do zapisywania obiektów języka XAML.  
  
 XAML obsługuje użycie flagi stylu dla wyliczeń o <xref:System.FlagsAttribute> zastosowane. Aby uzyskać więcej informacji, zobacz [szczegółów w składni języka XAML](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([Szczegółów w składni języka XAML](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) jest przeznaczony dla odbiorców WPF, ale większość informacji w tym temacie ma zastosowanie w przypadku XAML, który nie jest specyficzne dla konkretnego framework implementującej.)  
  
## <a name="member-definitions"></a>Definicje elementu członkowskiego  
 Typów można zdefiniować elementów członkowskich do użycia w języku XAML. Istnieje możliwość dla typów, które definiują elementy członkowskie, które są użyteczne XAML, nawet jeśli tego typu nie jest używany XAML. Jest to możliwe z powodu dziedziczenia CLR. Tak długo, jak pewien typ, który dziedziczy element członkowski obsługuje XAML użycia jako typ, a element członkowski obsługuje użycie języka XAML dla jego typem podstawowym lub ma dostępne natywnej składni języka XAML, ten element członkowski jest użyteczne XAML.  
  
### <a name="properties"></a>Właściwości  
 Jeśli jako publiczny właściwość CLR za pomocą typowych CLR można zdefiniować właściwości `get` i `set` wzorce dostępu i odpowiednim języku temat zgłosić właściwość jako element członkowski o odpowiednie informacje przewidziane system typów języka XAML <xref:System.Xaml.XamlMember> właściwości, takie jak <xref:System.Xaml.XamlMember.IsReadPublic%2A> i <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Właściwości specyficzne dla można włączyć składni tekstu, stosując <xref:System.ComponentModel.TypeConverterAttribute>. Aby uzyskać więcej informacji, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 W przypadku braku składni tekstu lub natywnego konwersji XAML i w przypadku braku dalszych pośredni, takie jak użycie rozszerzenia znaczników, typ właściwości (<xref:System.Xaml.XamlMember.TargetType%2A> system typów XAML) musi mieć możliwość zwrócenia wystąpienia do zapisywania obiektów XAML, traktując t Typ docelowy jako typ CLR.  
  
 Jeśli przy użyciu języka XAML 2009, [x: Reference — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-reference-markup-extension.md) można używać do Podaj wartości, jeśli wcześniejsze rozważania nie są spełnione, to jednak jeden z problemem użycia niż problem definicji typu.  
  
### <a name="events"></a>Zdarzenia  
 Po zdefiniowaniu zdarzenia jako publiczne zdarzenie CLR system typów języka XAML zgłosić zdarzenie jako element członkowski o <xref:System.Xaml.XamlMember.IsEvent%2A> jako `true`. Dołączenie obsługi zdarzeń nie jest w zakresie funkcji usług .NET Framework XAML; To pole pozostanie do implementacji i określonej struktury.  
  
### <a name="methods"></a>Metody  
 Kodu wbudowanego dla metod nie jest możliwość XAML domyślna. W większości przypadków użytkownik nie należy bezpośrednio odwoływać metody członków z XAML i rolą metod w języku XAML jest tylko do zapewnienia obsługi określonych wzorców XAML. [x: factorymethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md) wyjątek.  
  
### <a name="fields"></a>Pola  
 Wytyczne dotyczące projektowania CLR zniechęcić niestatycznego pola. Dla pola statyczne, można uzyskać dostępu do wartości pola statycznego tylko za pomocą [x: Static — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-static-markup-extension.md); w takim przypadku nie przeprowadzasz jakieś szczególne w definicji CLR do udostępnienia polem [x: Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) użycia.  
  
## <a name="attachable-members"></a>Możliwe do dołączenia elementy członkowskie  
 Możliwe do dołączenia elementy członkowskie są widoczne w języku XAML za pomocą wzorca metody dostępu na typ definiujący. Definiowanie samego typu nie trzeba XAML w można używać jako obiekt. W rzeczywistości jest wspólnego wzorca do zadeklarowania klasy usługi, którego rola jest właścicielem dołączalny element członkowski i zaimplementować powiązane zachowania, ale obsługiwać żadnych innych funkcji, takich jak reprezentacja interfejsu użytkownika. Dla następujących sekcji, symbol zastępczy *PropertyName* reprezentuje nazwę Twojej dołączalny element członkowski. Ta nazwa musi być prawidłowa w [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Należy zachować ostrożność kolizji nazw od tych wzorców i innych metod typu. Jeśli istnieje element członkowski, który jest zgodny z wzorców, jego mogą być interpretowane jako ścieżka użycia dołączalny element członkowski przez procesor XAML nawet wtedy, gdy nie była z zamiarem.  
  
#### <a name="the-getpropertyname-accessor"></a>Metoda dostępu GetPropertyName  
 Podpis dla `Get` *PropertyName* akcesora musi być:  
  
 `public static object Get`*PropertyName* `(object` `target`  `)`  
  
-   `target` Obiektu można określić jako bardziej określonego typu w implementacji. Umożliwia to zakres użycia dołączalny element członkowski; użycia poza zakres zamierzone zgłosi Nieprawidłowe rzutowanie wyjątki, które są następnie udostępniane przez błąd analizy języka XAML. Nazwa parametru `target` nie jest wymagane, ale ma nazwę `target` przez Konwencję w większości wdrożeń.  
  
-   Wartość zwracana można określić jako bardziej określonego typu w implementacji.  
  
 Do obsługi <xref:System.ComponentModel.TypeConverter> składnię tekst włączone użycie atrybutu dołączalny element członkowski, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do `Get` *PropertyName* metody dostępu. Stosowanie do `get` zamiast `set` może wydawać się nonintuitive; jednak tę Konwencję może obsługiwać pojęcie o tylko do odczytu możliwe do dołączenia elementy członkowskie, które są do serializacji, co jest przydatne w scenariuszach projektanta.  
  
#### <a name="the-setpropertyname-accessor"></a>Metoda dostępu SetPropertyName  
 Podpis dla zestawu*PropertyName* akcesora musi być:  
  
 `public static void Set`*PropertyName* `(object` `target` `, object` `value`    `)`  
  
-   `target` Obiektu można określić jako bardziej określonego typu w implementacji, z tej samej logiki i konsekwencje zgodnie z opisem w poprzedniej sekcji.  
  
-   `value` Obiektu można określić jako bardziej określonego typu w implementacji.  
  
 Należy pamiętać, że wartość ta metoda jest danych wejściowych przesyłanych przez użycie języka XAML, zwykle w formie atrybutu. W formie atrybutu musi być konwertera wartości obsługę składni tekstu, a atrybut na `Get` *PropertyName* metody dostępu.  
  
### <a name="attachable-member-stores"></a>Dołączalny element członkowski magazynów  
 Metody dostępu nie są zwykle wystarczająco, aby podać sposób umieszcza wartości dołączalny element członkowski w wykres obiektu lub pobrać wartości z wykres obiektu i serializacji je poprawnie. Do tej funkcji `target` obiektów w poprzednim sygnatur dostępu musi być zdolny do przechowywania wartości. Mechanizm magazynu powinien być zgodny z zasadą dołączalny element członkowski, który jest możliwy do dołączenia do obiektów docelowych, gdzie dołączalny element członkowski nie jest na liście elementów członkowskich. Usługi XAML .NET framework zapewnia technikę implementacji dołączalny element członkowski przechowuje za pośrednictwem interfejsów API <xref:System.Xaml.IAttachedPropertyStore> i <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore>jest używana przez autorów XAML do wykrywania Implementacja magazynu i powinny być implementowane w typie, który jest `target` z metod dostępu. Statycznych <xref:System.Xaml.AttachablePropertyServices> interfejsów API są używane w treści metody dostępu i odwoływać się do dołączalny element członkowski przez jego <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atrybuty CLR związane z XAML  
 Przypisywanie poprawnie z typów, elementy członkowskie i zestawy ważne jest, aby raport informacji o systemie typu XAML do usług .NET Framework XAML. Ma to zastosowanie, jeśli zamierzasz typy sieci do użycia z systemami XAML, które bezpośrednio na podstawie czytników .NET Framework XAML Services XAML i zapisywania XAML lub zdefiniuj lub użyj przy użyciu języka XAML platforma, która jest oparta na tych czytników XAML i zapisywania XAML.  
  
 Lista każdego atrybutu związane z XAML, odpowiedniego dla pomocy technicznej XAML dla niestandardowych typów, zobacz [XAML-Related atrybuty CLR dotyczące niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Użycie  
 Użycie niestandardowych typów wymaga, że autor znacznika musi być zamapowany prefiks dla zestawu i przestrzeń nazw środowiska CLR, które zawierają typu niestandardowego. Ta procedura nie jest opisane w tym temacie.  
  
## <a name="access-level"></a>Poziom dostępu  
 XAML umożliwia ładowanie i utworzenia wystąpienia typów, które mają `internal` poziom dostępu. Ta funkcja jest dostępne, aby kod użytkownika Definiowanie własnych typów, a następnie utworzyć wystąpienia klas z kod znaczników, który jest również częścią tego samego zakresu kodu użytkownika.  
  
 Przykład z WPF jest zawsze, gdy kod użytkownika definiuje <xref:System.Windows.Controls.UserControl> służy jako sposób Refaktoryzuj zachowania interfejsu użytkownika, ale nie jako część wszystkie możliwe rozszerzenia mechanizm, który może być niejawnego od zadeklarowania klasy pomocnicze z `public` poziom dostępu. Takie <xref:System.Windows.Controls.UserControl> mogą być deklarowane z `internal` dostępu, jeśli kod zapasowego jest skompilowany w tym samym zestawie, z którego jest przywoływany jako typu XAML.  
  
 Dla aplikacji, która ładuje XAML w trybie pełnego zaufania i używa <xref:System.Xaml.XamlObjectWriter>, ładowania klas z `internal` poziom dostępu jest zawsze włączona.  
  
 Właściwości poziomu dostępu dla aplikacji, która ładuje XAML w częściowej relacji zaufania, można kontrolować przy użyciu <xref:System.Xaml.Permissions.XamlAccessLevel> interfejsu API. Ponadto mechanizmów opóźnienia (np. system szablonu WPF) musi mieć możliwość propagację poziomu uprawnień dostępu i zachowanie ich do ocen ostatecznego czasie wykonywania. jest obsługiwany wewnętrznie przez przekazanie <xref:System.Xaml.Permissions.XamlAccessLevel> informacji.  
  
### <a name="wpf-implementation"></a>Implementacja WPF  
 WPF XAML korzysta z modelu dostępu częściowego zaufania, której Jeśli BAML został załadowany w częściowej relacji zaufania, dostęp jest ograniczony do <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> dla zestawu, który jest źródłem BAML. W przypadku opóźnienia, używa WPF <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> jako mechanizm przekazywania informacji poziomu dostępu.  
  
 W terminologii WPF XAML *wewnętrzny typ* jest typem, który jest definiowana za pomocą tego samego zestawu, który obejmuje również odwołujący się XAML. Takiego typu mogą być mapowane za pośrednictwem przestrzeni nazw XAML, które celowo pomija zestawu = część mapowaniem, na przykład `xmlns:local="clr-namespace:WPFApplication1"`.  Jeśli BAML odwołuje się do wewnętrznego typu i że typ ma `internal` dostęp do poziomu, spowoduje to wygenerowanie `GeneratedInternalTypeHelper` klasy dla zestawu. Jeśli chcesz uniknąć `GeneratedInternalTypeHelper`, należy albo użyć `public` poziom, dostępu lub należy uwzględnić odpowiednich klas osobny zestaw i udostępnić tego zestawu zależnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [Usługi XAML](../../../docs/framework/xaml-services/index.md)
