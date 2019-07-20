---
title: Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: e563c0d7e5113d55d4b942fb1d175a64f5b71abc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364294"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML
Podczas definiowania typów niestandardowych, które są obiektami biznesowymi lub typy, które nie mają zależności od określonych platform, istnieją pewne najlepsze rozwiązania dotyczące języka XAML, które można wykonać. Jeśli przestrzegasz tych rozwiązań, .NET Framework usług XAML i ich czytników XAML i autorzy języka XAML mogą wykrywać cechy języka XAML typu i dawać odpowiednie reprezentację w strumieniu węzłów XAML przy użyciu systemu typów XAML. W tym temacie opisano najlepsze rozwiązania dotyczące definicji typów, definicji elementów członkowskich i przypisywania typów lub elementów członkowskich przez środowisko CLR.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Wzorce konstruktora i definicje typów dla języka XAML  
 Aby można było utworzyć wystąpienie jako element obiektu w języku XAML, Klasa niestandardowa musi spełniać następujące wymagania:  
  
- Klasa niestandardowa musi być publiczna i musi uwidaczniać domyślny konstruktor publiczny (bez parametrów). (Zobacz poniższą sekcję, aby poznać informacje o strukturach).  
  
- Klasa niestandardowa nie może być klasą zagnieżdżoną. Dodatkowy "kropka" w ścieżce pełnej nazwy sprawia, że podział przestrzeni nazw klasy jest niejednoznaczny i zakłóca inne funkcje języka XAML, takie jak dołączone właściwości.  
  
 Jeśli obiekt może być skonkretyzowany jako element obiektu, utworzony obiekt może wypełnić formularz elementu właściwości właściwości, które przyjmują obiekt jako ich typ podstawowy.  
  
 Można nadal podawać wartości obiektów dla typów, które nie spełniają tych kryteriów, w przypadku włączenia konwertera wartości. Aby uzyskać więcej informacji, zobacz [Typy konwerterów i rozszerzenia znaczników dla języka XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury są zawsze możliwe do skonstruowania w języku XAML według definicji środowiska CLR. Wynika to z faktu, że kompilator CLR niejawnie tworzy Konstruktor bez parametrów dla struktury. Ten konstruktor inicjuje wszystkie wartości właściwości do ich wartości domyślnych.  
  
 W niektórych przypadkach domyślne zachowanie konstrukcji dla struktury nie jest pożądane. Może to być spowodowane tym, że struktura jest przeznaczona do wypełnienia wartości i funkcji koncepcyjnie jako Unia. W związku z tym zawarte wartości mogą mieć wzajemnie wykluczające się interpretacje i dlatego żadna z jej właściwości nie jest settable. Przykładem takiej struktury w słownictwie WPF jest <xref:System.Windows.GridLength>. Struktury te powinny implementować konwerter typów, aby wartości można wyrazić w postaci atrybutu, przy użyciu konwencji ciągów, które tworzą różne interpretacje lub tryby wartości struktury. Struktura powinna również ujawniać podobne zachowanie konstrukcji kodu za pomocą konstruktora bez parametrów.  
  
### <a name="interfaces"></a>Interfejsy  
 Interfejsy mogą być używane jako podstawowe typy elementów członkowskich. System typu XAML sprawdza listę umożliwiającą przypisanie i oczekuje, że obiekt, który jest dostarczony jako wartość, może być przypisany do interfejsu. Nie ma koncepcji, w jaki sposób interfejs musi być przedstawiony jako typ XAML, o ile odpowiedni typ możliwy do przypisania obsługuje wymagania konstrukcyjne języka XAML.  
  
### <a name="factory-methods"></a>Metody fabryki  
 Metody fabryki są funkcją języka XAML 2009. Modyfikują zasady języka XAML, które obiekty muszą mieć konstruktory bez parametrów. Metody fabryki nie są udokumentowane w tym temacie. Zobacz [X:FactoryMethod dyrektywy](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Wyliczenia mają zachowanie konwersji typu natywnego XAML. Stałe wyliczenia określone w języku XAML są rozpoznawane względem bazowego typu wyliczenia i zwracają wartość wyliczenia do składnika zapisywania obiektów XAML.  
  
 Język XAML obsługuje użycie stylu flag dla wyliczeń z <xref:System.FlagsAttribute> zastosowaniem. Aby uzyskać więcej informacji, zobacz [Szczegóły składni języka XAML](../wpf/advanced/xaml-syntax-in-detail.md). ([Szczegółowe informacje o składni języka XAML](../wpf/advanced/xaml-syntax-in-detail.md) są zapisywane dla odbiorców WPF, ale większość informacji w tym temacie dotyczy języka XAML, który nie jest specyficzny dla konkretnej struktury implementującej).  
  
## <a name="member-definitions"></a>Definicje elementów członkowskich  
 Typy mogą definiować członków do użycia XAML. Jest możliwe dla typów, które definiują elementy członkowskie, które są użyteczne do użycia w języku XAML, nawet jeśli dany typ nie jest do użycia w języku XAML. Jest to możliwe z powodu dziedziczenia CLR. Tak długo, jak jakiś typ, który dziedziczy składową, obsługuje użycie języka XAML jako typ, a element członkowski obsługuje użycie języka XAML dla jego typu podstawowego lub ma dostępną natywną składnię XAML, ten element członkowski jest używany do użycia w języku XAML.  
  
### <a name="properties"></a>Właściwości  
 Jeśli zdefiniujesz właściwości jako publiczną właściwość środowiska CLR przy użyciu typowych `get` wzorców `set` CLR i akcesora oraz odpowiednie sformułowanie dotyczące języka, system typu XAML może zgłosić właściwość jako element członkowski z odpowiednimi informacjami podanymi dla Właściwości, takie jak <xref:System.Xaml.XamlMember.IsReadPublic%2A> i <xref:System.Xaml.XamlMember.IsWritePublic%2A>. <xref:System.Xaml.XamlMember>  
  
 Określone właściwości mogą umożliwić składnię tekstu przez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute>. Aby uzyskać więcej informacji, zobacz [Typy konwerterów i rozszerzenia znaczników dla języka XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 W przypadku braku składni tekstowej lub natywnej konwersji XAML i braku dalszych pośrednich, takich jak użycie rozszerzenia znaczników, typ właściwości (<xref:System.Xaml.XamlMember.TargetType%2A> w systemie typu XAML) musi być w stanie zwracać wystąpienie do modułu zapisywania obiektów XAML przez podtraktowanie t Typ Arget jako typ CLR.  
  
 W przypadku korzystania z języka XAML 2009, [rozszerzenie znacznika x:Reference —](x-reference-markup-extension.md) może służyć do zapewnienia wartości, jeśli poprzednie zagadnienia nie są spełnione; Jednak jest to większa liczba problemów z użyciem niż w przypadku błędu definicji typu.  
  
### <a name="events"></a>Zdarzenia  
 W przypadku definiowania zdarzeń jako publicznego zdarzenia środowiska CLR System typu XAML może zgłosić zdarzenie jako element członkowski za pomocą <xref:System.Xaml.XamlMember.IsEvent%2A> jako. `true` Obsługa zdarzeń nie należy do zakresu .NET Framework możliwości usług XAML. jest to pozostało do określonych platform i implementacji.  
  
### <a name="methods"></a>Metody  
 Kod wbudowany dla metod nie jest domyślną funkcją języka XAML. W większości przypadków nie można bezpośrednio odwoływać się do elementów członkowskich metody z XAML, a rola metod w języku XAML ma tylko zapewnić obsługę określonych wzorców XAML. [X:FactoryMethod dyrektywa](x-factorymethod-directive.md) to wyjątek.  
  
### <a name="fields"></a>Pola  
 Wskazówki dotyczące projektowania środowiska CLR uniemożliwiają Niestatyczne pola. W przypadku pól statycznych można uzyskać dostęp do wartości pól statycznych tylko za poorednictwem [rozszerzenia znacznika x:static —](x-static-markup-extension.md). w takim przypadku nie są wykonywane żadne specjalne definicje środowiska CLR w celu udostępnienia pola do użycia [x:static —](x-static-markup-extension.md) .  
  
## <a name="attachable-members"></a>Możliwe do dołączenia elementy członkowskie  
 Możliwe do dołączenia elementy członkowskie są ujawniane w języku XAML za pomocą wzorca metody dostępu w typie definiującym. Sam typ definiujący nie musi być używany w języku XAML jako obiekt. W rzeczywistości typowym wzorcem jest zadeklarowanie klasy usług, której rola jest własnością dołączonego elementu członkowskiego i implementuje powiązane zachowania, ale nie obsługuje żadnej innej funkcji, takiej jak reprezentacja interfejsu użytkownika. W poniższych sekcjach, funkcja *PropertyName* zastępuje nazwę dołączonego elementu członkowskiego. Ta nazwa musi być prawidłowa w [gramatycename języka XAML](xamlname-grammar.md).  
  
 Należy zachować ostrożność w przypadku kolizji nazw między tymi wzorcami a innymi metodami typu. Jeśli element członkowski istnieje, który jest zgodny z jednym z wzorców, może być interpretowany jako możliwe do dołączenia użycie składowej przez procesor XAML nawet wtedy, gdy nie było to zamierzone.  
  
#### <a name="the-getpropertyname-accessor"></a>Metoda dostępu GetPropertyName  
 Sygnaturą `Get`metody dostępu *PropertyName* musi być:  
  
 `public static object Get`Funkcja *PropertyName* `(object``target`  `)`  
  
- `target` Obiekt może być określony jako bardziej konkretny typ w implementacji. Służy do określania zakresu użycia dołączalnego elementu członkowskiego; użycie poza zamierzonym zakresem spowoduje zgłoszenie nieprawidłowych wyjątków rzutowania, które są następnie nadane przez błąd analizy XAML. Nazwa `target` parametru nie jest wymagana, ale jest nazywana `target` Konwencją w większości implementacji.  
  
- Wartość zwracana może być określona jako bardziej konkretny typ w implementacji.  
  
 Aby zapewnić obsługę <xref:System.ComponentModel.TypeConverter> składni tekstu włączonego dla atrybutu użycie elementu członkowskiego, który można dołączyć <xref:System.ComponentModel.TypeConverterAttribute> , Zastosuj `Get`do metody dostępu *PropertyName* . Zastosowanie do `get` nie `set` może wydawać się Nieintuicyjny; Jednakże ta konwencja może obsługiwać koncepcję możliwych do dołączalnych elementów członkowskich, które są możliwe do serializacji, co jest przydatne w scenariuszach projektanta.  
  
#### <a name="the-setpropertyname-accessor"></a>Metoda dostępu setPropertyName  
 Sygnaturą dla zestawu metody dostępu*PropertyName* musi być:  
  
 `public static void Set`Funkcja *PropertyName* `(object``target` `, object``value`    `)`  
  
- `target` Obiekt może być określony jako bardziej konkretny typ w implementacji, z tą samą logiką i konsekwencjami, zgodnie z opisem w poprzedniej sekcji.  
  
- `value` Obiekt może być określony jako bardziej konkretny typ w implementacji.  
  
 Należy pamiętać, że wartość tej metody jest wartością wejściową pochodzącą z użycia XAML, zazwyczaj w formie atrybutu. Z poziomu formularza atrybutu musi być obsługa konwertera wartości dla składni tekstu i atrybut `Get`metody dostępu *PropertyName* .  
  
### <a name="attachable-member-stores"></a>Możliwe do dołączenia magazyny elementów członkowskich  
 Metody dostępu są zwykle zbyt małe, aby zapewnić sposób umieszczania wartości elementów członkowskich do dołączenia do grafu obiektów lub pobierania wartości z grafu obiektów i prawidłowego serializacji. Aby zapewnić tę funkcjonalność, `target` obiekty w poprzednich sygnaturach dostępu muszą mieć możliwość przechowywania wartości. Mechanizm magazynu powinien być zgodny z zasadą dołączalną składową, która jest dołączana do elementów docelowych, gdzie Dołączalny element członkowski nie znajduje się na liście elementów członkowskich. .NET Framework usługi XAML udostępniają technikę implementacji dla dołączanych magazynów elementów <xref:System.Xaml.IAttachedPropertyStore> członkowskich <xref:System.Xaml.AttachablePropertyServices>za pomocą interfejsów API i. <xref:System.Xaml.IAttachedPropertyStore>jest używana przez moduły zapisujące XAML do odnajdywania implementacji sklepu i powinna zostać wdrożona na typ, który jest `target` obiektem metod dostępu. Statyczne <xref:System.Xaml.AttachablePropertyServices> interfejsy API są używane w treści metod dostępu i odwołują się do dołączonego elementu członkowskiego <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atrybuty CLR związane z XAML  
 Prawidłowe przypisanie typów, elementów członkowskich i zestawów jest ważne w celu raportowania informacji o systemie typu XAML do .NET Framework usług XAML. Jest to istotne w przypadku, gdy zamierzasz korzystać z typów używanych z systemami XAML, które są bezpośrednio oparte na .NET Framework czytnikach XAML usług XAML i autorzy języka XAML, lub jeśli zdefiniujesz platformę wykorzystującą XAML lub korzystającą z nich, która jest oparta na tych czytnikach XAML i autorzy języka XAML.  
  
 Aby zapoznać się z listą każdego atrybutu związanego z XAML, który jest istotny dla obsługi języka XAML dla typów niestandardowych, zobacz atrybuty CLR związane z językiem XAML [dla niestandardowych typów i bibliotek](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Użycie  
 Użycie typów niestandardowych wymaga, aby autor znacznika musiał zmapować prefiks dla przestrzeni nazw zestawu i środowiska CLR, który zawiera typ niestandardowy. Ta procedura nie jest udokumentowana w tym temacie.  
  
## <a name="access-level"></a>Poziom dostępu  
 Język XAML zapewnia metodę ładowania i tworzenia wystąpienia typów, które mają `internal` poziom dostępu. Ta funkcja jest dostarczana, aby kod użytkownika mógł definiować własne typy, a następnie tworzyć wystąpienia tych klas z znaczników, które są również częścią tego samego zakresu kodu użytkownika.  
  
 Przykładem z platformy WPF jest każdy kod <xref:System.Windows.Controls.UserControl> użytkownika, który jest przeznaczony do refaktoryzacji zachowania interfejsu użytkownika, ale nie jako część dowolnego możliwego mechanizmu rozszerzenia, który może być implikowany przez zadeklarowanie klasy pomocniczej z `public` poziomem dostępu. Taka a <xref:System.Windows.Controls.UserControl> może być zadeklarowana `internal` z dostępem, jeśli kod zapasowy jest kompilowany do tego samego zestawu, z którego jest przywoływany jako typ XAML.  
  
 W przypadku aplikacji ładującej kod XAML w ramach pełnego zaufania <xref:System.Xaml.XamlObjectWriter>i używania, ładowanie `internal` klas z poziomem dostępu jest zawsze włączone.  
  
 W przypadku aplikacji ładującej kod XAML w obszarze częściowej relacji zaufania można kontrolować charakterystykę poziomu dostępu za <xref:System.Xaml.Permissions.XamlAccessLevel> pomocą interfejsu API. Ponadto mechanizmy odroczenia (takie jak system szablonów WPF) muszą być w stanie propagować wszelkie uprawnienia poziomu dostępu i zachować je na potrzeby oceny czasu wykonywania. jest to obsługiwane wewnętrznie przez przekazanie <xref:System.Xaml.Permissions.XamlAccessLevel> informacji.  
  
### <a name="wpf-implementation"></a>Implementacja WPF  
 W języku XAML WPF jest stosowany model dostępu częściowego zaufania, w którym w przypadku załadowania BAML w ramach częściowej relacji zaufania dostęp jest ograniczony do <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> zestawu, który jest źródłem BAML. W przypadku odroczenia, <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> WPF używa jako mechanizmu przekazywania informacji o poziomie dostępu.  
  
 W terminologii języka XAML WPF, *Typ wewnętrzny* jest typem, który jest zdefiniowany przez ten sam zestaw, który zawiera również odwołanie XAML. Taki typ może być mapowany za pomocą przestrzeni nazw XAML, która celowo pomija zestaw = część mapowania, na przykład `xmlns:local="clr-namespace:WPFApplication1"`.  Jeśli BAML odwołuje się do typu wewnętrznego i ten `internal` typ ma poziom dostępu, `GeneratedInternalTypeHelper` generuje klasę dla zestawu. Jeśli chcesz uniknąć `GeneratedInternalTypeHelper`, musisz użyć poziomu dostępu lub w `public` miarę jak należy zastosować odpowiednią klasę do oddzielnego zestawu i uczynić ten zestaw zależny.  
  
## <a name="see-also"></a>Zobacz także

- [Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [Usługi XAML](index.md)
