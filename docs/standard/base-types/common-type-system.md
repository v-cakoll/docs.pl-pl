---
title: System typu wspólnego
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- type system
- common type system
- assemblies [.NET Framework], types
- reference types
- value types
- cross-language interoperability
- namespaces [.NET Framework], types
- types, about types
ms.assetid: 53c57c96-83e1-4ee3-9543-9ac832671a89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c8db725e25fe441c875a25cba97eb2090d4c071
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139465"
---
# <a name="common-type-system"></a>System typu wspólnego
Wspólny system typów definiuje, jak typy są deklarowane, używane i zarządzane w środowisko uruchomieniowe języka wspólnego, a ponadto jest ważną częścią obsługi integracji wielu języków. Wspólny system typów wykonuje następujące funkcje:  
  
-   Tworzy ramy, ułatwiająca włączenie integracji wielu języków, bezpieczeństwo typów i wykonywanie kodu o wysokiej wydajności.  
  
-   Zapewnia model obiektowy, obsługujący pełne wdrożenie wielu języków programowania.  
  
-   Definiuje reguły, których muszą przestrzegać języki, co pomaga zapewnić, że obiekty napisane w różnych językach mogą współdziałać ze sobą.  
  
-   Zawiera bibliotekę zawierającą pierwotne typy danych (takich jak <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, i <xref:System.UInt64>) używane w rozwoju aplikacji.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Typy na platformie .NET](#types_in_the_net_framework)  
  
-   [Definicje typu](#type_definitions)  
  
-   [Elementy członkowskie typu](#type_members)  
  
-   [Cechy typów członków](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy na platformie .NET  
 Wszystkie typy w .NET są typami wartości lub typami referencyjnymi.  
  
 Typy wartości są typy danych, w których obiekty są reprezentowane przez rzeczywistą wartość obiektu. Jeśli wystąpienie typu wartości jest przypisany do zmiennej, zmienna ta otrzymuje świeżą kopię wartości.  
  
 Typy odwołań są typami danych, w których obiekty są reprezentowane przez odniesienie (podobne do wskaźnika) do rzeczywistej wartości obiektu. Jeśli typ odwołania jest przypisany do zmiennej, ta zmienna odwołuje się (wskazuje) pierwotną wartość. Kopia nie jest wykonywana.  
  
 Wspólny system typów programu .NET obsługuje następujących pięć kategorii typów:  
  
-   [Klasy](#Classes)  
  
-   [Struktury](#Structures)  
  
-   [Wyliczenia](#Enumerations)  
  
-   [Interfejsy](#Interfaces)  
  
-   [Delegaci](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Klasy  
 Klasa jest typem odwołania, które może pochodzić bezpośrednio z innej klasy i niejawnie pochodzi od <xref:System.Object?displayProperty=nameWithType>. Klasa określa operacje, że obiekt (czyli wystąpienia klasy) może wykonać (metody, zdarzenia lub właściwości) i danych, które ten obiekt zawiera (pola). Chociaż klasa generalnie obejmuje definicję i implementację (w przeciwieństwie do interfejsów, na przykład, które zawierają tylko definicje, bez konieczności implementowania), może mieć jeden lub więcej elementów członkowskich, które nie mają implementacji.  
  
 W poniższej tabeli opisano niektóre właściwości, które może mieć klasy. Każdy język, który obsługuje środowisko wykonawcze zapewnia sposób, aby wskazać, że klasa lub członek klasy ma jedną lub więcej z tych cech. Jednak konkretnych językach programowania przeznaczonych .NET może nie udostępnić te cechy.  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|sealed|Określa, czy innej klasy nie może być pochodną tego typu.|  
|implements|Wskazuje, że klasa używa jednego lub więcej interfejsów przez dostarczenie implementacji członków interfejsów.|  
|abstract|Wskazuje, że nie można utworzyć wystąpienia klasy. Z niej korzystać, musi pochodzić z innej klasy, z niego.|  
|Inherits|Wskazuje, że wystąpienia klasy mogą być używane wszędzie tam, gdzie określono klasę bazową. Klasa pochodna, która dziedziczy z klasy bazowej można używać implementacji członków publicznych udostępnianej przez klasę bazową lub klasy pochodne mogą zastępować implementację członków publicznych własną implementację.|  
|wyeksportowane lub niewyeksportowane|Wskazuje, czy klasa jest widoczna spoza zestawu, w którym jest zdefiniowany. Cecha ta dotyczy tylko klas najwyższego poziomu i nie klas zagnieżdżonych.|  
  
> [!NOTE]
>  Klasa może być też zagnieżdżona w klasie nadrzędnej lub strukturze. Klasy zagnieżdżone mają również właściwości Członkowskie. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](#NestedTypes).  
  
 Elementy członkowskie klasy, które nie mają implementacji, są członkami abstrakcyjnymi. Klasa, która ma jeden lub więcej członków abstrakcyjnych sama jest abstrakcyjna; Nie można utworzyć nowych wystąpień. Niektóre języki przeznaczone dla środowiska uruchomieniowego pozwalają na oznacznie klasy jako abstrakcyjnej, nawet jeśli żaden z jej członków nie jest abstrakcyjna. Można użyć klasy abstrakcyjnej, jeśli chcesz hermetyzować podstawowy zestaw funkcji, które klasy pochodne mogą dziedziczony lub zastąpiony, gdy jest to konieczne. Klasy, które nie są abstrakcyjne, są nazywane konkretnych klas.  
  
 Klasa może implementować dowolną liczbę interfejsów, ale może dziedziczyć tylko z klasy bazowej, oprócz <xref:System.Object?displayProperty=nameWithType>, z której wszystkie klasy dziedziczą niejawnie. Wszystkie klasy muszą mieć co najmniej jednego konstruktora, który inicjuje nowe wystąpienia klasy. Jeśli użytkownik nie definiuje jawnie konstruktora, większość kompilatorów automatycznie dostarczy domyślnego (bezparametrowego) konstruktora.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura jest typem wartości, która niejawnie pochodzi od <xref:System.ValueType?displayProperty=nameWithType>, który z kolei pochodzi od <xref:System.Object?displayProperty=nameWithType>. Struktura jest bardzo przydatna do reprezentowania wartości, których wymagania pamięci są małe, a także do przekazywania wartości jako parametrów wg wartości do metod, które mają silnie typizowane parametry. Na platformie .NET, wszystkich typów danych pierwotnych (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64>) są definiowane jako struktury.  
  
 Jak klasy struktury definiują zarówno dane (pola struktury), jak i operacje, które mogą być wykonywane na tych danych (metody struktury). Oznacza to, że może wywoływać metody dla struktur, w tym wirtualne metody zdefiniowane w <xref:System.Object?displayProperty=nameWithType> i <xref:System.ValueType?displayProperty=nameWithType> klasy i wszelkie metody zdefiniowane dla samego typu wartości. Innymi słowy struktury mogą mieć pola, właściwości i zdarzenia, a także metody statyczne i Niestatyczne. Można utworzyć wystąpienia struktur, przekazać je jako parametry, przechowywać je jako zmienne lokalne lub przechowywać je w polu innego typu wartości lub odwołania do typu. Struktury mogą także implementować interfejsy.  
  
 Typy wartości różnią się także od klas w kilku aspektach. Po pierwsze, mimo że niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType>, bezpośrednio nie mogą dziedziczyć z dowolnego typu. Podobnie wszystkie typy wartości są zamknięte, co oznacza, że żaden inny typ mogą być uzyskane z nich. Również nie wymagają konstruktorów.  
  
 Dla każdego typu wartości środowisko uruchomieniowe języka wspólnego dostarcza odpowiedni typ spakowany, który jest klasa, która ma taki sam stan i zachowanie jak typ wartości. Wystąpienie typu wartości jest ramce, gdy jest przekazywany do metody, która akceptuje parametr typu <xref:System.Object?displayProperty=nameWithType>. Jest rozpakowywany (czyli przekonwertowany z wystąpienia klasy ponownie na wystąpienie typu wartości) gdy kontrola wraca z wywołania metody, które akceptuje typ wartości jako parametr według odwołania. Niektóre języki wymagają użycia specjalnej składni, gdy typ spakowany jest wymagana; inne automatycznie korzystają z typu spakowanego, kiedy jest potrzebny. Podczas definiowania typu wartości jest definiowany jest typ spakowany i typ rozpakowany.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenie (enum) jest typem wartości, który dziedziczy bezpośrednio z <xref:System.Enum?displayProperty=nameWithType> i dostarcza alternatywnych nazw dla wartości pierwotnych typu podstawowego. Typ wyliczenia ma nazwę, bazowy typ, który musi być jednym z typów wbudowanych podpisanych lub niepodpisanych liczb całkowitych (takie jak <xref:System.Byte>, <xref:System.Int32>, lub <xref:System.UInt64>), a zestaw pól. Pola są statyczne pola literal, z których każde reprezentuje stałą. Tę samą wartość można przypisać do wielu pól. W takim przypadku musisz oznaczyć jedną z wartości jako wartość wyliczenia podstawowego odbicia i konwersji ciągów.  
  
 Można przypisać wartość typu podstawowego do wyliczenia i odwrotnie (rzutowanie nie jest wymagane przez środowisko uruchomieniowe). Można utworzyć wystąpienie wyliczania i wywołać metodę <xref:System.Enum?displayProperty=nameWithType>, jak również wszelkie metody zdefiniowane w typie podstawowego wyliczenia. Jednak niektóre języki mogą nie pozwalają przekazać wyliczenia jako parametr, gdy wymagane jest wystąpienie bazowego typu (lub odwrotnie).  
  
 Do wyliczeń są stosowane następujące dodatkowe ograniczenia:  
  
-   Nie można ich definiować własnych metod.  
  
-   Nie mogą wdrażać interfejsów.  
  
-   Nie mogą określać właściwości ani zdarzeń.  
  
-   Nie może być ogólny, chyba że są rodzajowe tylko z powodu zagnieżdżenia wewnątrz typu rodzajowego. Oznacza to, że wyliczenie nie może mieć parametrów typu swój własny.  
  
    > [!NOTE]
    >  Zagnieżdżone typy (włącznie z wyliczeniami) utworzone za pomocą języka Visual Basic, C# i C++ zawierają parametry wszystkich otaczających typów ogólnych i dlatego są standardowe, nawet jeśli nie mają parametrów typu w swoich własnych. Aby uzyskać więcej informacji, zobacz "Zagnieżdżone typy" w <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> temat referencyjny.  
  
 <xref:System.FlagsAttribute> Atrybut oznacza specjalny rodzaj wyliczenia zwanego polem bitowym. Środowisko wykonawcze nie rozróżnia tradycyjnych wyliczeń i pól bitowych, ale język może to zrobić. Podczas tego rozróżnienia operatory bitowe może służyć w polach bitowych, ale nie w wyliczeniach do generowania nienazwanych wartości. Wyliczenia są zwykle używane dla list unikatowych elementów, takich jak dni tygodnia, kraj lub region nazwy i tak dalej. Pola bitowe są zwykle używane dla list jakości lub ilości, które mogą wystąpić w połączeniu, takich jak `Red And Big And Fast`.  
  
 Poniższy przykład pokazuje, jak używać zarówno w przypadku pól bitowych, jak i wyliczeń tradycyjnych.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Interfejsy  
 Interfejs definiuje kontrakt, który określa relację "może zrobić" lub "ma" relacji. Interfejsy często są używane do implementowania funkcji, takich jak porównywanie i sortowanie ( <xref:System.IComparable> i <xref:System.IComparable%601> interfejsów), testowanie dla równości ( <xref:System.IEquatable%601> interface), lub wyliczanie elementów w kolekcji ( <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601> interfejsów). Interfejsy mogą mieć właściwości, metody i zdarzenia, które są członkami abstrakcyjnymi; oznacza to, że chociaż interfejs definiuje członków i ich podpisy, pozostawia typowi implementującemu interfejs zdefiniowanie funkcji każdego członka interfejsu. Oznacza to, że klasy lub struktury, która implementuje interfejs musi dostarczyć definicje członków abstrakcyjnych zadeklarowanych w interfejsie. Interfejs może wymagać implementujące klasy lub struktury, aby także implementować jeden lub więcej interfejsów.  
  
 Do interfejsów są stosowane następujące ograniczenia:  
  
-   Interfejs może być zadeklarowany z dowolnym opcjami dostępu, ale członkowie interfejsu muszą mieć powszechnej dostępności.  
  
-   Interfejsy nie mogą definiować konstruktorów.  
  
-   Interfejsy nie mogą definiować pól.  
  
-   Interfejsy mogą definiować tylko członków wystąpień. Nie mogą określać elementów statycznych.  
  
 Każdy język musi zawierać reguły mapowania implementacja na interfejs który wymaga członka, ponieważ więcej niż jeden interfejs może zadeklarować członka o tym samym podpisie, a członkowie ci mogą mieć osobne implementacje.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegaty  
 Obiekty delegowane są typami odwołań, które służą celowi podobnemu do do wskaźników funkcji w języku C++. Są one używane w programach obsługi zdarzeń i funkcjach wywołania zwrotnego w programie .NET. W przeciwieństwie do wskaźników funkcji obiekty delegowane są bezpieczne i weryfikowalne i bezpieczeństwa typów. Typ obiektu delegowanego może reprezentować każdą metodę wystąpienia lub metodę statyczną, który ma zgodny podpis.  
  
 Parametru obiektu delegowanego jest zgodny z odpowiednim parametrem metody, jeśli typ parametru delegata jest bardziej restrykcyjny niż typ parametru metody, ponieważ gwarantuje to, że argument przekazany do obiektu delegowanego można bezpiecznie przekazać do Metoda.  
  
 Podobnie zwracany typ delegata jest zgodny z typem zwracanym metody, jeśli typ zwracany metody jest bardziej restrykcyjny niż typ zwracany obiektu delegowanego, ponieważ gwarantuje to, że wartość zwracana metody może być bezpiecznie umieszczona na zwracany typ e delegata.  
  
 Na przykład delegat, który ma parametr typu <xref:System.Collections.IEnumerable> i zwracanym typem <xref:System.Object> może reprezentować metodę, która ma parametr typu <xref:System.Object> oraz wartość zwracaną typu <xref:System.Collections.IEnumerable>. Aby uzyskać więcej informacji i przykładowy kod, zobacz <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Obiekt delegowany jest zobowiązany do metody, którą reprezentuje. Oprócz związania z metodą, obiekt delegowany może być powiązana z obiektem. Obiekt reprezentuje pierwszy parametr metody i jest przekazywany do metody, za każdym razem, gdy obiekt delegowany jest wywoływany. Jeśli metoda jest metodą wystąpienia, związany obiekt jest przekazywany jako niejawny `this` parametru (`Me` w języku Visual Basic); Jeśli metoda jest statyczna, obiekt jest przekazywany jako pierwszy formalny parametr metody i podpis delegata muszą być zgodne. pozostałych parametrów. Aby uzyskać więcej informacji i przykładowy kod, zobacz <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Wszystkie obiekty delegowane dziedziczą z <xref:System.MulticastDelegate?displayProperty=nameWithType>, który dziedziczy z <xref:System.Delegate?displayProperty=nameWithType>. Języki C#, Visual Basic i C++ nie umożliwiają dziedziczenia z tych typów. Zamiast tego zapewniają słowa kluczowe do deklarowania obiektów delegowanych.  
  
 Ponieważ obiekty delegowane dziedziczą z <xref:System.MulticastDelegate>, obiekt delegowany ma listę wywołań, czyli listę metod, które reprezentuje obiekt delegowany i są wykonywane, gdy obiekt delegowany jest wywoływany. Wszystkie metody na liście otrzymują argumenty dostarczane, gdy obiekt delegowany jest wywoływany.  
  
> [!NOTE]
>  Wartość zwracana nie jest zdefiniowany dla pełnomocnika, który ma więcej niż jedną metodę liście wywołania, nawet jeśli pełnomocnik ma typ zwracany.  
  
 W wielu przypadkach takie, jak przy użyciu metod wywołania zwrotnego, obiekt delegowany reprezentuje tylko jedną metodę i jedynymi czynnościami, które należy wykonać to utworzenie obiektu delegowanego i wywołanie go.  
  
 Dla obiektów delegowanych, które reprezentują wiele metod .NET zapewnia metody <xref:System.Delegate> i <xref:System.MulticastDelegate> delegować klasy do obsługi operacji, takich jak dodanie metody do listy wywołań obiektu delegowanego ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> metoda), usuwanie metody ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> metoda) i pobieranie listy wywołań ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> metody).  
  
> [!NOTE]
>  Nie jest niezbędne do korzystania z tych metod do delegatów obsługi zdarzeń w języku C#, C++ i Visual Basic, ponieważ te języki zapewniają składnię umożliwiającą Dodawanie i usuwanie programów obsługi zdarzeń.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definicje typów  
 Definicja typu obejmuje następujące funkcje:  
  
-   Wszelkie atrybuty zdefiniowane w typie.  
  
-   Typu (widoczność).  
  
-   Nazwa typu.  
  
-   Typ podstawowy typu.  
  
-   Wszystkie interfejsy implementowane przez typ.  
  
-   Definicje dla każdego członka typu.  
  
### <a name="attributes"></a>Atrybuty  
 Atrybuty zawierają dodatkowe metadane zdefiniowane przez użytkownika. Najczęściej są one używane do przechowywania dodatkowych informacji o typie w jego zestawie lub do zmodyfikowania zachowania członka typu w jednym środowisku czasu projektowania lub czasu wykonywania.  
  
 Atrybuty są same klasami, które dziedziczą z <xref:System.Attribute?displayProperty=nameWithType>. Języki, które obsługują używanie atrybutów mają własne składnie stosowania atrybutów do elementów języka. Atrybuty mogą być stosowane do niemal wszystkich elementów języka; określone elementy, których można zastosować atrybutu są definiowane przez <xref:System.AttributeUsageAttribute> mający zastosowanie do tej klasy atrybutu.  
  
### <a name="type-accessibility"></a>Dostępność typu  
 Wszystkie typy mają modyfikatory, które regulują ich dostępność z innych typów. W poniższej tabeli opisano możliwości dostępu do typów obsługiwane w czasie wykonywania.  
  
|Ułatwienia dostępu|Opis|  
|-------------------|-----------------|  
|public|Typ jest dostępny dla wszystkich zestawów.|  
|zestaw|Typ jest dostępny tylko w ramach własnego zestawu.|  
  
 Dostępność typu zagnieżdżonego zależy od jego domeny dostępności, która jest określona przez oba deklarowana dostępność metody elementu członkowskiego i domena dostępności typu zawierającego. Jednakże domena dostępności typu zagnieżdżonego nie może przekraczać tego dla typu zawierającej.  
  
 Domena dostępności członka zagnieżdżonego `M` zadeklarowane w typie `T` w programie `P` jest zdefiniowany następująco (biorąc pod uwagę, że `M` może być typem):  
  
-   Jeśli deklarowana dostępność metody `M` jest `public`, domena dostępności `M` jest domena dostępności `T`.  
  
-   Jeśli deklarowana dostępność metody `M` jest `protected internal`, domena dostępności `M` jest część wspólną domeny dostępności `T` tekstu programu `P` i tekstu programu o dowolnym typie pochodnych `T` zadeklarowaną poza tekstem `P`.  
  
-   Jeśli deklarowana dostępność metody `M` jest `protected`, domena dostępności `M` jest część wspólną domeny dostępności `T` tekstu programu `T` i dowolnego typu opracowane z `T`.  
  
-   Jeśli deklarowana dostępność metody `M` jest `internal`, domena dostępności `M` jest część wspólną domeny dostępności `T` tekstu programu `P`.  
  
-   Jeśli deklarowana dostępność metody `M` jest `private`, domena dostępności `M` znajduje się tekst program `T`.  
  
### <a name="type-names"></a>Nazwy typów  
 Wspólny system typów nakłada tylko dwa ograniczenia dotyczące nazw:  
  
-   Wszystkie nazwy są kodowane jako ciągi znaków Unicode, (16-bitowe).  
  
-   Nazwy nie są dozwolone w osadzonym wartości (16-bitowy) 0x0000.  
  
 Jednakże większość języków nakłada dodatkowe ograniczenia na nazwy typów. Wszystkie porównania są wykonywane na podstawie bajt po bajcie i dlatego jest rozróżniana wielkość liter i niezależne od ustawień regionalnych.  
  
 Chociaż typ może odwoływać do typów w innych modułach i zestawach, typem musi być całkowicie zdefiniowany w ramach jednego modułu .NET. (W zależności od obsługa kompilatora jednak go można podzielić na wiele plików kodu źródłowego.) Nazwy typów muszą być unikatowe tylko w obrębie przestrzeni nazw. Pełna identyfikacja typu, nazwa typu musi być kwalifikowana przez obszar nazw zawierający implementację typu.  
  
### <a name="base-types-and-interfaces"></a>Typy podstawowe i interfejsy  
 Typ może odziedziczyć wartości i zachowania innego typu. Wspólny system typów nie zezwala na typy odziedziczone z więcej niż jednego typu podstawowego.  
  
 Typ może implementować dowolną liczbę interfejsów. Aby zaimplementować interfejs, typ musi implementować wirtualnych członków interfejsu. Metoda wirtualna może być implementowana przez typ pochodny i może być wywołana statycznie lub dynamicznie.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Elementy członkowskie typu  
 Środowisko wykonawcze umożliwia zdefiniowanie członków typu, który określa zachowanie i stan typu. Elementy członkowskie typu są następujące:  
  
-   [Pola](#Fields)  
  
-   [Właściwości](#Properties)  
  
-   [Metody](#Methods)  
  
-   [Konstruktory](#Constructors)  
  
-   [Zdarzenia](#Events)  
  
-   [Zagnieżdżone typy](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pola  
 Pole opisuje i zawiera część stanu typu. Pola mogą być dowolnego typu obsługiwanego przez środowisko uruchomieniowe. Najczęściej pola są `private` lub `protected`, dzięki czemu są one dostępne tylko z w ramach klasy lub z klasy pochodnej. Jeśli wartość pola można modyfikować spoza jego typu, jest zazwyczaj używana metoda dostępu do zestawu właściwości. Pola udostępnione publicznie są zwykle tylko do odczytu i mogą być dwojakiego rodzaju:  
  
-   Stałe, których wartości są przypisywane w czasie projektowania. Są to statyczne elementy członkowskie klasy, chociaż nie zostały określone przy użyciu `static` (`Shared` w języku Visual Basic) słowa kluczowego.  
  
-   Zmienne tylko do odczytu, w których wartości można przypisać w konstruktorze klasy.  
  
 Poniższy przykład ilustruje te dwa sposoby użycia pól tylko do odczytu.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Właściwości  
 Właściwość nazywa wartość lub stan typu i definiuje metody uzyskiwania lub ustawiania wartości właściwości. Właściwości mogą być typami pierwotnymi, zbiorami typów pierwotnych, typami zdefiniowanymi przez użytkownika lub kolekcji typów zdefiniowanych przez użytkownika. Właściwości są często używane, aby zapobiec interfejsu publicznego typu niezależnie od rzeczywistej reprezentacji typu. Umożliwia to właściwościom odzwierciedlać wartości, które nie są przechowywane bezpośrednio w klasie (na przykład, gdy właściwość zwraca wartość wyliczoną) lub wykonanie sprawdzenia poprawności przed przypisaniem wartości do pól prywatnych. Poniższy przykład ilustruje ten drugi wzorzec.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Poza tym samą właściwość, obejmuje języka Microsoft intermediate language (MSIL) dla typu, który zawiera odczytywalną właściwość `get_` *propertyname* metody, a język MSIL dla typu, który zawiera zapisywalnego zawiera właściwości `set_` *propertyname* metody.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda opisuje operacje, które są dostępne wobec typu. Podpis metody określa dopuszczalne typy jej wszystkich parametrów i zwracanej wartości.  
  
 Chociaż większość metod określa dokładną liczbę parametrów wymaganych do wywoływania metod, niektóre metody obsługują zmienną liczbę parametrów. Ostateczny zadeklarowany parametr tych metod jest oznaczona atrybutem <xref:System.ParamArrayAttribute> atrybutu. Kompilatory języka zwykle zapewniają słowo kluczowe, takie jak `params` w języku C# i `ParamArray` w języku Visual Basic, który sprawia, że jawne użycie <xref:System.ParamArrayAttribute> niepotrzebne.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktorów  
 Konstruktor jest specjalnym rodzajem metody, która tworzy nowe wystąpienia klasy lub struktury. Podobnie jak każda inna metoda Konstruktor może zawierać parametry; jednak konstruktory nie mają wartości zwracanej (czyli zwracają `void`).  
  
 Jeśli kod źródłowy dla klasy nie definiuje jawnie konstruktora, kompilator zawiera domyślnego (bezparametrowego) konstruktora. Jednakże jeśli kod źródłowy dla klasy definiuje tylko konstruktory sparametryzowane, kompilatory języków Visual Basic i C# nie generują konstruktora bez parametrów.  
  
 Jeśli kod źródłowy dla struktury definiuje konstruktory, muszą być sparametryzowane; Struktura nie może definiować domyślnego (bezparametrowego) konstruktora, a kompilatory nie generują konstruktorów bez parametrów dla struktur ani innych typów wartości. Wszystkie typy wartości mają niejawnego domyślnego konstruktora. Ten konstruktor jest implementowany przez środowisko uruchomieniowe języka wspólnego i inicjalizuje wszystkie pola struktury do ich wartości domyślnych.  
  
<a name="Events"></a>   
### <a name="events"></a>Zdarzenia  
 Zdarzenie określa zdarzenie, które można zareagować i definiuje metody subskrypcja, anulowanie subskrypcji i wywoływania zdarzenia. Zdarzenia są często używane do informowania innych typów zmiany stanu. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Zagnieżdżone typy  
 Typ zagnieżdżony jest typ, który jest członkiem innego typu. Zagnieżdżone typy powinny być ściśle powiązane ich typem zawierającym i nie można ich używać jako typów ogólnego przeznaczenia. Zagnieżdżone typy są przydatne, gdy typ deklarujący używa i tworzy wystąpienia typu zagnieżdżonego, a użycie typu zagnieżdżonego nie jest widoczne w publicznych członkach.  
  
 Zagnieżdżone typy są mylące dla niektórych programistów i nie powinny być publicznie widoczne, chyba że istnieje istotny powód widoczności. W bibliotece dobrze zaprojektowanej deweloperzy rzadko powinni być zmuszeni do używania zagnieżdżonych typów do tworzenia wystąpień obiektów lub deklarowaniu zmiennych.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Cechy typów członków  
 Wspólny system typów umożliwia członkom typów posiadanie różnych cech; jednak języków nie są wymagane do obsługi wszystkich tych cech. W poniższej tabeli opisano charakterystyki składowych.  
  
|Cechy|Można zastosować do|Opis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, właściwości i zdarzenia|Typ nie dostarcza implementację metody. Typy, które dziedziczą lub implementują metody abstrakcyjne musi dostarczyć implementację metody. Jedynym wyjątkiem jest, gdy typ pochodny sam jest typem abstrakcyjnym. Wszystkie metody abstrakcyjne są wirtualne.|  
|prywatne, rodzina, zestawu, rodziny i zestawu, rodziny lub zestawu lub publicznego|Wszystkie|Definiuje dostępność członka:<br /><br /> private<br /> Dostępne tylko z w obrębie tego samego typu co członek lub w ramach typu zagnieżdżonego.<br /><br /> Rodzina<br /> Dostępny w obrębie tego samego typu jako elementu członkowskiego oraz z pochodnych typów dziedziczących od niego.<br /><br /> zestaw<br /> Dostępne tylko w zestawie, w którym typ jest zdefiniowany.<br /><br /> Rodzina i zestaw<br /> Dostępne tylko z typów, które kwalifikują się do dostępu rodzinę i zestaw.<br /><br /> Rodzina lub zestaw<br /> Dostępne tylko z typów, które kwalifikują się do dostępu Rodzina lub zestaw.<br /><br /> public<br /> Dostępne z dowolnego typu.|  
|końcowe|Metody, właściwości i zdarzenia|Nie można zastąpić metodę wirtualną w typie pochodnym.|  
|tylko do inicjowania|Pola|Wartość może być inicjowane tylko i nie może być zapisywana po zainicjowaniu.|  
|wystąpienia|Pola, metody, właściwości i zdarzenia|Jeżeli członek nie jest oznaczony jako `static` (C# i C++), `Shared` (Visual Basic), `virtual` (C# i C++) lub `Overridable` (Visual Basic), jest członkiem wystąpienia (istnieje żadne słowo kluczowe wystąpienia). Będzie tyle kopii takich elementów członkowskich w pamięci, ponieważ istnieją obiekty, które go używają.|  
|literal|Pola|Wartość przypisana do pola jest wartością stałą, znany w czasie kompilacji, o określonym wbudowanym typie wartości. Pola literałów są czasami określane jako stałe.|  
|nowe gniazdo lub zastąpienie|Wszystkie|Definiuje, jak członek współdziała z dziedziczonymi członkami, którzy mają taki sam podpis:<br /><br /> nowego gniazda<br /> Ukrywa dziedziczonych członków, które mają taki sam podpis.<br /><br /> override<br /> Zastępuje definicję odziedziczonej metody wirtualnej.<br /><br /> Wartość domyślna to newslot.|  
|static|Pola, metody, właściwości i zdarzenia|Element członkowski należy do typu, który jest zdefiniowany, nie do konkretnego wystąpienia typu; składowa istnieje, nawet jeśli nie jest tworzone wystąpienie typu i jest ona udostępniona wszystkim wystąpieniom typu.|  
|virtual|Metody, właściwości i zdarzenia|Metoda może być implementowana przez typ pochodny i może być wywołana statycznie lub dynamicznie. Jeśli jest używane wywołanie dynamiczne, Typ wystąpienia dokonujący wywołania w czasie wykonywania (a nie typ znany w czasie kompilacji) określa, która implementacja metody jest wywoływana. Aby wywołać metodę wirtualną statycznie, zmienna może być konieczne można rzutować na typ, który używa żądanej wersji metody.|  
  
### <a name="overloading"></a>Przeciążenie  
 Każdy członek typu ma unikatowy podpis. Podpisy metoda składają się z nazwy metody i listą parametrów (kolejności i typów argumentów metody). Tak długo, jak różnią się ich podpisy, można zdefiniować wiele metod o tej samej nazwie w ramach danego typu. Po zdefiniowaniu dwóch lub więcej metod o tej samej nazwie metoda jest nazywany uznawana za przeciążoną. Na przykład w <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> jest przeciążona metoda. Jedna metoda przyjmuje strukturę <xref:System.Char>. Inna metoda pobiera <xref:System.String> i <xref:System.Int32>.  
  
> [!NOTE]
>  Zwracany typ nie jest uznawane za część podpisu metody. Oznacza to nie mogą być przeciążone metody, jeśli różnią się tylko typem zwracanym.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dziedziczenie, zastępowanie i ukrywanie członków  
 Typ pochodny dziedziczy wszystkich członków typu podstawowego; oznacza to, że te elementy członkowskie są zdefiniowane w i dostępne dla typu pochodnego. Zachowanie lub jakość członków dziedziczonych można modyfikować na dwa sposoby:  
  
-   Typ pochodny może ukrywać dziedziczonego członka przez definiowanie nowego członka o tym samym podpisie. Może to zostać zrobione, Oznacz jako prywatne wcześniejszego członka publicznego lub zdefiniowania nowego zachowania metody dziedziczonej, który jest oznaczony jako `final`.  
  
-   Typ pochodny może zastąpić dziedziczoną metodę wirtualną. Metoda przesłaniania zawiera nową definicję metody, która będzie wywołana na podstawie typu wartości w czasie wykonywania, a nie typu zmiennej znanego w czasie kompilacji. Metoda może zastąpić metodę wirtualną tylko wtedy, gdy metoda wirtualna nie jest oznaczony jako `final` i nowa metoda jest co najmniej tak samo dostępna jak metoda wirtualna.  
  
## <a name="see-also"></a>Zobacz także

- [Przeglądarka interfejsu API .NET](/dotnet/api)  
- [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md)  
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
