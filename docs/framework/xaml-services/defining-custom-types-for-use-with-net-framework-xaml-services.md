---
title: Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 672660f73e9e6faf25985a651290e979f9deb9f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492510"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML
Definiowanie typów niestandardowych, które są obiektami biznesowych lub typów, które nie są zależne od określonych platform, istnieją niektóre najlepsze rozwiązania dotyczące XAML, które możesz wykonać. Jeśli wykonujesz tych rozwiązań, usług programu .NET Framework XAML, a jego XAML czytników i składników zapisywania XAML może odnajdywać właściwości XAML danego typu i nadaj mu odpowiednią reprezentację w postaci strumienia węzłów XAML w systemie typu XAML. W tym temacie opisano najlepsze rozwiązania dotyczące definicji typu, definicje elementów członkowskich i przypisywanie CLR, typy lub członków.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Wzorce konstruktora i definicji typu dla XAML  
 Z myślą o uruchamianiu jako elementu obiektu w XAML, niestandardowej klasy musi spełniać następujące wymagania:  
  
-   Klasa niestandardowa musi być publiczna i musi uwidaczniać domyślnego (bezparametrowego) konstruktora publicznego. (Zobacz następujące sekcji uwag dotyczących struktury).  
  
-   Klasa niestandardowa nie może być klasą zagnieżdżoną. Dodatkowy "dot" w ścieżce pełnej nazwy sprawia, że dzielenie przestrzeń nazw klasy jest niejednoznaczne i zakłóca działanie innych funkcji XAML, takich jak dołączone właściwości.  
  
 Jeśli obiekt może być utworzone jako elementu obiektu, utworzony obiekt wypełnić formularz elementu właściwości wszystkich właściwości, które przyjmują obiektu jako ich typu podstawowego.  
  
 Nadal można podać obiekt wartości dla typów, które nie spełniają tych kryteriów, po włączeniu konwertera wartości. Aby uzyskać więcej informacji, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Struktury  
 Struktury mogą zawsze być zbudowane w XAML, zgodnie z definicją CLR. Jest to spowodowane kompilatora CLR niejawnie tworzy domyślny konstruktor dla struktury. Ten konstruktor inicjuje wszystkie wartości właściwości do wartości domyślnych.  
  
 W niektórych przypadkach domyślne zachowanie konstrukcji dla struktury nie jest pożądane. Być może struktura ma pod względem koncepcyjnym jako złożenie wypełnij wartości i funkcji. Jako Unii zawarte wartości mogą być interpretacji wzajemnie się wykluczają, a w związku z tym, czy żaden z jej właściwości można ustawić. Na przykład struktury w słownictwa WPF <xref:System.Windows.GridLength>. Te struktury powinny implementować konwertera typów, tak, aby wartości mogą być wyrażone w formie atrybutu przy użyciu konwencji ciągu, tworzone różne interpretacji lub tryby wartości struktury. Struktura również powinny ujawniać zachowanie podobne do tworzenia kodu za pośrednictwem konstruktora innych niż domyślne.  
  
### <a name="interfaces"></a>Interfejsy  
 Interfejsy mogą służyć jako typów podstawowych elementów członkowskich. System typów XAML sprawdza listy można przypisać i oczekuje, że obiekt, który jest dostarczana jako wartości można przypisać do interfejsu. Nie ma koncepcji jak interfejsu muszą być przedstawione jako typ XAML tak długo, jak odpowiedni typ można przypisać obsługuje wymagania konstrukcji XAML.  
  
### <a name="factory-methods"></a>Metodami Factory  
 Metodami Factory są funkcją XAML 2009. Zasada XAML, że obiekty muszą mieć konstruktory domyślne mogą modyfikować. W tym temacie nie opisano metodach fabryki. Zobacz [x: FactoryMethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Wyliczenia mają zachowanie konwersji typu natywnego XAML. Nazwy stałe wyliczeń, określone w XAML zostaną rozwiązane przed podstawowym typem wyliczenia, a następnie wróć na wartość wyliczenia do zapisywania obiektu XAML.  
  
 XAML obsługuje użycie flagi stylu dla wyliczeń ze <xref:System.FlagsAttribute> stosowane. Aby uzyskać więcej informacji, zobacz [składnia XAML w szczegółów](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([Szczegółów w składni XAML](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) jest przeznaczony dla odbiorców WPF, ale większość informacji w tym temacie jest odpowiednie dla XAML, które nie są specyficzne dla określonej struktury implementującej.)  
  
## <a name="member-definitions"></a>Definicje elementów członkowskich  
 Typy można zdefiniować elementy członkowskie do użycia XAML. Istnieje możliwość dla typów, które definiują elementy członkowskie, które są użyteczne XAML, nawet jeśli nie jest XAML można używać tego konkretnego typu. Jest to możliwe z powodu dziedziczenia CLR. Tak długo, jak pewnego typu, który dziedziczy element członkowski obsługuje XAML użycia jako typ, a element członkowski obsługuje użycia XAML dla jego typu podstawowego lub ma dostępne natywnej składni XAML, ten element członkowski jest użyteczne XAML.  
  
### <a name="properties"></a>Właściwości  
 Możesz zdefiniować właściwości jako właściwość publiczna CLR przy użyciu typowego CLR `get` i `set` wzorce dostępu i odpowiednim języku temat zgłosić właściwość jako element członkowski o odpowiednie informacje przewidziane systemie typu XAML <xref:System.Xaml.XamlMember> właściwości, takie jak <xref:System.Xaml.XamlMember.IsReadPublic%2A> i <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Określone właściwości, można włączyć składni tekstu, stosując <xref:System.ComponentModel.TypeConverterAttribute>. Aby uzyskać więcej informacji, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 W przypadku braku składni tekstu lub natywnych konwersji XAML i w przypadku braku dalszych pośredniego, takich jak użycie rozszerzenia znaczników, typ właściwości (<xref:System.Xaml.XamlMember.TargetType%2A> system typów XAML) musi mieć możliwość zwrócenia wystąpienia do zapisywania obiektów XAML, traktując t Typ docelowy jako typ CLR.  
  
 Jeśli przy użyciu XAML 2009 r. [x: Reference — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-reference-markup-extension.md) może służyć do Podaj wartości, jeśli poprzednie zagadnienia nie są spełnione; dotyczy to jednak jeden problem użycia, niż problem definicji typu.  
  
### <a name="events"></a>Zdarzenia  
 Jeśli zdefiniujesz zdarzenia jako publiczne zdarzenie środowiska CLR, systemie typu XAML zgłosić zdarzenia jako element członkowski o <xref:System.Xaml.XamlMember.IsEvent%2A> jako `true`. Dołączenie procedury obsługi zdarzeń nie jest w zakresie możliwości usług programu .NET Framework XAML; To pole pozostanie do określonej struktury i implementacji.  
  
### <a name="methods"></a>Metody  
 Wbudowany kod dla metody nie jest to domyślna funkcja XAML. W większości przypadków użytkownik nie należy bezpośrednio odwoływać członkowie metody z XAML, a rola metod w XAML jest tylko do zapewnienia obsługi określonych wzorców XAML. [x: FactoryMethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md) jest wyjątek.  
  
### <a name="fields"></a>Pola  
 Wytyczne dotyczące projektowania CLR zniechęcić niestatycznego pola. W przypadku pól statycznych, można uzyskać dostęp wartości pól statycznych tylko za pośrednictwem [x: Static — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-static-markup-extension.md); w takim przypadku nie wykonujesz jakieś szczególne w definicji CLR, aby ujawnić pola dla [x: Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) użycia.  
  
## <a name="attachable-members"></a>Można dołączyć elementy członkowskie  
 Można dołączyć elementy członkowskie są ujawniane XAML przy użyciu wzorca metody dostępu na typ definiujący. Typ definiujący sam nie trzeba XAML mogą być używane jako obiekt. W rzeczywistości jest wspólny wzorzec do deklarowania klasy usługi, którego rola jest właścicielem można dołączyć elementu członkowskiego i zaimplementować zachowania powiązane, ale obsługiwać żadnych innych funkcji, takich jak reprezentacja interfejsu użytkownika. Dla następujących sekcji, a symbol zastępczy *PropertyName* reprezentuje nazwę usługi można dołączyć elementu członkowskiego. Tej nazwy muszą być prawidłowe w [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Należy zachować ostrożność kolizji nazw między te wzorce i innych metod typu. Jeśli istnieje element członkowski, który jest zgodny z jednym z wzorców, jego może być interpretowana jako ścieżki użycie można dołączyć elementu członkowskiego przez procesor XAML nawet wtedy, gdy nie było zamiaru.  
  
#### <a name="the-getpropertyname-accessor"></a>Akcesor GetPropertyName  
 Podpis dla `Get` *PropertyName* metody dostępu muszą być:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` Obiektu może być określony jako bardziej specyficznego typu w danej implementacji. Umożliwia to zakres użycia usługi można dołączyć elementu członkowskiego; użycia spoza zakresu zamierzony zgłosi Nieprawidłowe rzutowanie wyjątki, które następnie są udostępniane przez błąd analizy XAML. Nazwa parametru `target` nie jest to wymagane, ale nosi nazwę `target` zgodnie z Konwencją w większości implementacji.  
  
-   Zwracana wartość można określić jako bardziej określonego typu w danej implementacji.  
  
 Do obsługi <xref:System.ComponentModel.TypeConverter> składnia tekstu włączone użycie atrybutu można dołączyć elementu członkowskiego, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do `Get` *PropertyName* metody dostępu. Stosowanie do `get` zamiast `set` może wydawać się nonintuitive; jednak ta Konwencja obsługuje pojęcie tylko do odczytu można dołączyć elementy członkowskie, które można serializować, która jest przydatne w scenariuszach projektanta.  
  
#### <a name="the-setpropertyname-accessor"></a>Akcesor SetPropertyName  
 Podpis dla zestawu*PropertyName* metody dostępu muszą być:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` Obiektu można określić jako bardziej specyficznego typu w danej implementacji, z tej samej logiki i konsekwencje zgodnie z opisem w poprzedniej sekcji.  
  
-   `value` Obiektu może być określony jako bardziej specyficznego typu w danej implementacji.  
  
 Pamiętaj, że wartość ta metoda ma dane wejściowe, pochodzące z użycia XAML, zwykle w formie atrybutu. Za pomocą formularza atrybutu musi być konwertera wartości obsługę składni tekstu i atrybutu na `Get` *PropertyName* metody dostępu.  
  
### <a name="attachable-member-stores"></a>Można dołączyć magazynów elementu członkowskiego  
 Metody dostępu zwykle nie są wystarczająco, aby stanowić sposób, aby umieścić wartości można dołączyć elementu członkowskiego grafu obiektów lub pobrać wartości z wykresu obiektu i serializacji je poprawnie. Do tej funkcji `target` obiektów w poprzednich podpisach dostępu musi być zdolny do przechowywania wartości. Mechanizm magazynu powinny być zgodne z zasadą można dołączyć elementu członkowskiego, który można dołączyć do celów, gdzie można dołączyć elementu członkowskiego nie jest na liście elementów członkowskich jest element członkowski. .NET framework XAML Services zapewnia techniki implementacji można dołączyć elementu członkowskiego są przechowywane przy użyciu interfejsów API <xref:System.Xaml.IAttachedPropertyStore> i <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> jest używana przez autorów XAML do wykrywania Implementacja magazynu i powinny zostać wdrożone na typ, który jest `target` z metod dostępu. Statyczne <xref:System.Xaml.AttachablePropertyServices> interfejsy API są używane w treści metody dostępu i dotyczą można dołączyć elementu członkowskiego przez jego <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atrybuty CLR związane z XAML  
 Poprawnie przypisywanie swoje typy, członków i zestawy ważne jest, aby raport informacje o systemie typu XAML do usług programu .NET Framework XAML. Może to być istotne, jeśli zamierzasz typów do użycia w systemach XAML, które opierają się bezpośrednio na .NET Framework XAML Services XAML czytników i składników zapisywania XAML lub zdefiniuj, lub użyj framework przy użyciu XAML, który jest oparty na tych XAML czytników i składników zapisywania XAML.  
  
 Lista każdego atrybutu związane z XAML, odpowiednią obsługę XAML typów niestandardowych, zobacz [XAML-Related atrybuty CLR dla niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Użycie  
 Użycie niestandardowych typów wymaga, że autor znaczników musi być mapowane prefiks dla zestawu i przestrzeń nazw środowiska CLR, które zawierają typ niestandardowy. Ta procedura nie jest opisane w tym temacie.  
  
## <a name="access-level"></a>Poziom dostępu  
 XAML udostępnia środki do obciążenia i tworzenie wystąpień typów, które mają `internal` poziom dostępu. Ta funkcja jest dostępna, dzięki czemu kod użytkownika mogą definiować własne typy i, tworzy tych klas z kod znaczników, który jest również częścią tego samego zakresu kodu użytkownika.  
  
 Przykładem z WPF jest zawsze wtedy, gdy kod użytkownika definiuje <xref:System.Windows.Controls.UserControl> służy jako sposób Refaktoryzuj zachowania interfejsu użytkownika, ale nie w ramach dowolnego mechanizmu możliwe rozszerzenia, który może wynikać z od zadeklarowania klasy pomocnicze z `public` poziom dostępu. Takie <xref:System.Windows.Controls.UserControl> mogą być deklarowane przy użyciu `internal` dostęp, jeśli kod zapasowy jest kompilowany do tego samego zestawu, z którego odwołuje się do pisania XAML.  
  
 Dla aplikacji, która ładuje XAML w trybie pełnego zaufania i używa <xref:System.Xaml.XamlObjectWriter>, trwa ładowanie klas `internal` poziom dostępu jest zawsze włączona.  
  
 Właściwości poziomu dostępu dla aplikacji, która ładuje XAML w częściowej relacji zaufania, można kontrolować za pomocą <xref:System.Xaml.Permissions.XamlAccessLevel> interfejsu API. Ponadto mechanizmów opóźnienia (np. system szablonu WPF) musi mieć możliwość Propagacja żadnych uprawnień na poziomie dostępu i zachowanie ich do ostatecznej wykonywania ocen. jest to obsługiwane wewnętrznie przez przekazanie <xref:System.Xaml.Permissions.XamlAccessLevel> informacji.  
  
### <a name="wpf-implementation"></a>Implementacji WPF  
 WPF XAML korzysta z modelu dostępu częściowego zaufania, w którym Jeśli BAML jest ładowany w częściowej relacji zaufania, dostęp jest ograniczony do <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> dla zestawu, który jest źródłem BAML. W przypadku opóźnienia, używa WPF <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> jako mechanizm przekazywania informacje o poziomie dostępu.  
  
 W terminologii WPF XAML *wewnętrzny typ* to typ, który jest definiowany przez tego samego zestawu, który również uwzględnia odwołujący się XAML. Za pomocą przestrzeni nazw XAML, które celowo pomija zestawu można zamapować taki typ = fragment mapowania, na przykład `xmlns:local="clr-namespace:WPFApplication1"`.  Jeśli BAML odwołuje się do typu wewnętrznego i typ ma `internal` uzyskać dostęp do poziomu, spowoduje to wygenerowanie `GeneratedInternalTypeHelper` klasy dla zestawu. Jeśli chcesz uniknąć `GeneratedInternalTypeHelper`, należy albo użyć `public` uzyskać dostęp do poziomu, lub należy wziąć pod uwagę odpowiednich klas w osobnym zestawie i udostępnić tego zestawu zależnego.  
  
## <a name="see-also"></a>Zobacz także
- [Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [Usługi XAML](../../../docs/framework/xaml-services/index.md)
