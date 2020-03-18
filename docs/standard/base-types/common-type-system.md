---
title: System typu wspólnego
description: Dowiedz się więcej o systemie typów w .NET.
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
ms.openlocfilehash: c574719da9b89b468b92b042e1f2b5b10fbe3c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400492"
---
# <a name="common-type-system"></a>System typu wspólnego
Wspólny system typów definiuje sposób, w jaki typy są deklarowane, używane i zarządzane w czasie wykonywania języka wspólnego, a także jest ważną częścią obsługi wykonywania integracji między językami. Wspólny system typów wykonuje następujące funkcje:  
  
- Ustanawia strukturę, która pomaga włączyć integrację między językami, bezpieczeństwo typów i wykonywanie kodu o wysokiej wydajności.  
  
- Udostępnia model obiektowy, który obsługuje pełną implementację wielu języków programowania.  
  
- Definiuje reguły, które języki muszą przestrzegać, co pomaga zapewnić, że obiekty napisane w różnych językach mogą współdziałać ze sobą.  
  
- Zawiera bibliotekę zawierającą pierwotne typy danych <xref:System.Boolean>(takie <xref:System.Char> <xref:System.Int32>jak <xref:System.UInt64>, <xref:System.Byte>, , , i ) używane podczas tworzenia aplikacji.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Typy w .NET](#types_in_the_net_framework)  
  
- [Definicje typu](#type_definitions)  
  
- [Elementy członkowskie typu](#type_members)  
  
- [Charakterystyka członków typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>
## <a name="types-in-net"></a>Typy w .NET  
 Wszystkie typy w .NET są typami wartości lub typami odwołań.  
  
 Typy wartości są typami danych, których obiekty są reprezentowane przez rzeczywistą wartość obiektu. Jeśli wystąpienie typu wartości jest przypisane do zmiennej, ta zmienna otrzymuje nową kopię wartości.  
  
 Typy odwołań są typami danych, których obiekty są reprezentowane przez odwołanie (podobne do wskaźnika) do rzeczywistej wartości obiektu. Jeśli typ odwołania jest przypisany do zmiennej, ta zmienna odwołuje się (wskazuje) wartość oryginalną. Nie jest wykonana żadna kopia.  
  
 Wspólny system typów w .NET obsługuje następujące pięć kategorii typów:  
  
- [Klasy](#Classes)  
  
- [Struktury](#Structures)  
  
- [Wyliczenia](#Enumerations)  
  
- [Interfejsy](#Interfaces)  
  
- [Delegaty](#Delegates)  
  
<a name="Classes"></a>
### <a name="classes"></a>Klasy  
 Klasa jest typem odwołania, który może być pochodną bezpośrednio z <xref:System.Object?displayProperty=nameWithType>innej klasy i który jest pochodną niejawnie z . Klasa definiuje operacje, które obiekt (który jest wystąpieniem klasy) może wykonywać (metody, zdarzenia lub właściwości) i dane, które zawiera obiekt (pola). Mimo że klasa zazwyczaj zawiera zarówno definicji i implementacji (w przeciwieństwie do interfejsów, na przykład, które zawierają tylko definicję bez implementacji), może mieć jeden lub więcej elementów członkowskich, które nie mają implementacji.  
  
 W poniższej tabeli opisano niektóre cechy, które może mieć klasa. Każdy język, który obsługuje program runtime zapewnia sposób, aby wskazać, że klasy lub elementu członkowskiego klasy ma jeden lub więcej z tych cech. Jednak poszczególne języki programowania, które są przeznaczone dla .NET może nie udostępnić wszystkie te cechy.  
  
|Charakterystyka|Opis|  
|--------------------|-----------------|  
|sealed|Określa, że nie można uzyskać innej klasy z tego typu.|  
|implements|Wskazuje, że klasa używa jednego lub więcej interfejsów, zapewniając implementacje elementów członkowskich interfejsu.|  
|abstract|Wskazuje, że nie można utworzyć wystąpienia klasy. Aby go użyć, należy wyprowadzić z niego inną klasę.|  
|Dziedziczy|Wskazuje, że wystąpień klasy mogą być używane w dowolnym miejscu klasy podstawowej jest określony. Klasa pochodna, która dziedziczy z klasy podstawowej można użyć implementacji wszystkich publicznych elementów członkowskich dostarczonych przez klasę podstawową lub klasy pochodnej można zastąpić implementacji publicznych elementów członkowskich z własnej implementacji.|  
|wywieziony lub niewywieziony|Wskazuje, czy klasa jest widoczna poza złożeniem, w którym jest zdefiniowana. Ta charakterystyka dotyczy tylko klas najwyższego poziomu, a nie klas zagnieżdżonych.|  
  
> [!NOTE]
> Klasa może być również zagnieżdżone w klasie nadrzędnej lub struktury. Klasy zagnieżdżone mają również właściwości elementów członkowskich. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](#NestedTypes).  
  
 Elementy członkowskie klasy, które nie mają implementacji są abstrakcyjne elementy członkowskie. Klasa, która ma jeden lub więcej abstrakcyjnych elementów członkowskich jest sama w sobie abstrakcyjne; nie można utworzyć nowych wystąpień. Niektóre języki, które są przeznaczone dla czasu wykonywania pozwalają oznaczyć klasę jako abstrakcyjne, nawet jeśli żaden z jej członków są abstrakcyjne. Klasę abstrakcyjną można użyć, aby zhermetyzować podstawowy zestaw funkcji, które klasy pochodne mogą dziedziczyć lub zastępować w razie potrzeby. Klasy, które nie są abstrakcyjne są określane jako konkretne klasy.  
  
 Klasa może zaimplementować dowolną liczbę interfejsów, ale może dziedziczyć tylko z jednej klasy podstawowej oprócz <xref:System.Object?displayProperty=nameWithType>, z którego wszystkie klasy dziedziczą niejawnie. Wszystkie klasy muszą mieć co najmniej jeden konstruktor, który inicjuje nowe wystąpienia klasy. Jeśli nie jawnie zdefiniować konstruktora, większość kompilatorów automatycznie zapewni konstruktora bezparametrów.  
  
<a name="Structures"></a>
### <a name="structures"></a>Struktury  
 Struktura jest typem wartości, który <xref:System.ValueType?displayProperty=nameWithType>wywodzi się <xref:System.Object?displayProperty=nameWithType>niejawnie z , który z kolei pochodzi od . Struktura jest bardzo przydatna do reprezentowania wartości, których wymagania dotyczące pamięci są małe, oraz dla przekazywania wartości jako parametrów według wartości do metod, które mają silnie typizowane parametry. W .NET wszystkie pierwotne typy<xref:System.Boolean>danych <xref:System.Byte> <xref:System.Char>( <xref:System.DateTime> <xref:System.Decimal>, <xref:System.Double> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, , , , , , , i ) są zdefiniowane jako struktury.  
  
 Podobnie jak klasy, struktury definiują zarówno dane (pola struktury), jak i operacje, które mogą być wykonywane na tych danych (metody struktury). Oznacza to, że można wywołać metody na struktury, w <xref:System.Object?displayProperty=nameWithType> tym <xref:System.ValueType?displayProperty=nameWithType> metody wirtualne zdefiniowane na i klas i wszelkie metody zdefiniowane na typ wartości, sam. Innymi słowy struktury mogą mieć pola, właściwości i zdarzenia, a także metody statyczne i niestatyczne. Można tworzyć wystąpienia struktur, przekazywać je jako parametry, przechowywać je jako zmienne lokalne lub przechowywać je w polu innego typu wartości lub typu odwołania. Struktury można również implementować interfejsy.  
  
 Typy wartości różnią się również od klas pod wieloma względami. Po pierwsze, mimo że <xref:System.ValueType?displayProperty=nameWithType>niejawnie dziedziczą z , nie mogą bezpośrednio dziedziczyć z dowolnego typu. Podobnie wszystkie typy wartości są zapieczętowane, co oznacza, że żaden inny typ nie może być pochodną. Nie wymagają one również konstruktorów.  
  
 Dla każdego typu wartości program runtime języka wspólnego dostarcza odpowiedni typ pudełkowy, który jest klasą, która ma ten sam stan i zachowanie co typ wartości. Wystąpienie typu wartości jest zapakowane, gdy jest przekazywana do metody, <xref:System.Object?displayProperty=nameWithType>która akceptuje parametr typu . Jest bez pudełka (oznacza to, że konwertowane z wystąpienia klasy z powrotem do wystąpienia typu wartości) podczas zwraca kontroli z wywołania metody, która akceptuje typ wartości jako parametr by-reference. Niektóre języki wymagają użycia specjalnej składni, gdy wymagany jest typ pudełkowy; inne osoby automatycznie używają typu pudełkowego, gdy jest on potrzebny. Podczas definiowania typu wartości definiujesz zarówno typ pudełkowy, jak i niespakowany.  
  
<a name="Enumerations"></a>
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenie (wyliczenie) jest typem <xref:System.Enum?displayProperty=nameWithType> wartości, który dziedziczy bezpośrednio z i który dostarcza alternatywne nazwy dla wartości podstawowego typu pierwotnego. Typ wyliczenia ma nazwę, typ bazowy, który musi być jednym z wbudowanych typów podpisanych <xref:System.Int32>lub <xref:System.UInt64>niepodpisanych liczb całkowitych (takich jak <xref:System.Byte>, lub ) i zestaw pól. Pola są statycznymi polami literału, z których każdy reprezentuje stałą. Tę samą wartość można przypisać do wielu pól. W takim przypadku należy oznaczyć jedną z wartości jako podstawową wartość wyliczenia dla konwersji odbicia i ciągu.  
  
 Wartość typu źródłowego można przypisać do wyliczenia i odwrotnie (w czasie wykonywania nie jest wymagany rzutowanie). Można utworzyć wystąpienie wyliczenia i wywołać <xref:System.Enum?displayProperty=nameWithType>metody , a także wszystkie metody zdefiniowane na typ podstawowy wyliczenia. Jednak niektóre języki mogą nie pozwolić na przekazanie wyliczenia jako parametr, gdy wymagane jest wystąpienie typu źródłowego (lub odwrotnie).  
  
 Następujące dodatkowe ograniczenia mają zastosowanie do wyliczeń:  
  
- Nie mogą definiować własnych metod.  
  
- Nie można zaimplementować interfejsów.  
  
- Nie można zdefiniować właściwości lub zdarzeń.  
  
- Nie mogą być ogólne, chyba że są one ogólne tylko dlatego, że są zagnieżdżone w typie rodzajowym. Oznacza to, że wyliczenie nie może mieć parametrów typu własnych.  
  
    > [!NOTE]
    > Typy zagnieżdżone (w tym wyliczenia) utworzone za pomocą języka Visual Basic, C# i C++ zawierają parametry typu wszystkich otaczających typów ogólnych i dlatego są ogólne, nawet jeśli nie mają własnych parametrów typu. Aby uzyskać więcej informacji, zobacz "Typy zagnieżdżone" w temacie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> odwołania.  
  
 Atrybut <xref:System.FlagsAttribute> oznacza specjalny rodzaj wyliczenia o nazwie pole bitowe. Sam program runtime nie rozróżnia tradycyjnych wyliczeń i pól bitowych, ale język może to zrobić. Po wprowadzeniu tego rozróżnienia operatory bitowe mogą być używane w polach bitowych, ale nie na wyliczeniach, do generowania wartości nienazwanych. Wyliczenia są zazwyczaj używane dla list unikatowych elementów, takich jak dni tygodnia, nazwy kraju lub regionu itd. Pola bitowe są zazwyczaj używane dla list jakości lub ilości, `Red And Big And Fast`które mogą wystąpić w połączeniu, takich jak .  
  
 W poniższym przykładzie pokazano, jak używać zarówno pól bitowych, jak i tradycyjnych wyliczeń.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>
### <a name="interfaces"></a>Interfejsy  
 Interfejs definiuje kontrakt, który określa relację "może zrobić" lub relację "ma". Interfejsy są często używane do implementowania funkcji, takich <xref:System.IComparable> jak <xref:System.IComparable%601> porównywanie i sortowanie <xref:System.IEquatable%601> (i interfejsy), testowanie równości (interfejs) lub wyliczanie elementów w kolekcji <xref:System.Collections.IEnumerable> (i <xref:System.Collections.Generic.IEnumerable%601> interfejsów). Interfejsy mogą mieć właściwości, metody i zdarzenia, z których wszystkie są abstrakcyjne elementy członkowskie; oznacza to, że chociaż interfejs definiuje elementy członkowskie i ich podpisy, pozostawia go do typu, który implementuje interfejs, aby zdefiniować funkcje każdego elementu członkowskiego interfejsu. Oznacza to, że każda klasa lub struktura, która implementuje interfejs musi dostarczyć definicje abstrakcyjnych elementów członkowskich zadeklarowanych w interfejsie. Interfejs może wymagać dowolnej klasy implementacji lub struktury, aby również zaimplementować jeden lub więcej innych interfejsów.  
  
 Następujące ograniczenia dotyczą interfejsów:  
  
- Interfejs można zadeklarować z dowolną dostępnością, ale wszystkie elementy członkowskie interfejsu muszą mieć publiczną dostępność.  
  
- Interfejsy nie można zdefiniować konstruktorów.  
  
- Interfejsy nie mogą definiować pól.  
  
- Interfejsy można zdefiniować tylko elementy członkowskie wystąpienia. Nie można zdefiniować statycznych elementów członkowskich.  
  
 Każdy język musi zawierać reguły mapowania implementacji do interfejsu, który wymaga elementu członkowskiego, ponieważ więcej niż jeden interfejs może zadeklarować element członkowski z tym samym podpisem, a te elementy członkowskie mogą mieć oddzielne implementacje.  
  
<a name="Delegates"></a>
### <a name="delegates"></a>Delegaty  
 Delegatów są typy odwołań, które służą do celu podobnego do wskaźników funkcji w języku C++. Są one używane dla programów obsługi zdarzeń i funkcji wywołania zwrotu w .NET. W przeciwieństwie do wskaźników funkcji delegatów są bezpieczne, weryfikowalne i typu bezpieczne. Typ delegata może reprezentować dowolną metodę wystąpienia lub metodę statyczną, która ma zgodny podpis.  
  
 Parametr delegata jest zgodny z odpowiednim parametrem metody, jeśli typ parametru delegata jest bardziej restrykcyjny niż typ parametru metody, ponieważ gwarantuje to, że argument przekazany pełnomocnikowi może być bezpiecznie przekazany do metody.  
  
 Podobnie zwracany typ delegata jest zgodny z zwracanym typem metody, jeśli zwracany typ metody jest bardziej restrykcyjny niż zwracany typ delegata, ponieważ gwarantuje to, że wartość zwracana metody może być bezpiecznie odlewana do powrotu typu delegata.  
  
 Na przykład delegat, który ma parametr <xref:System.Collections.IEnumerable> typu i <xref:System.Object> zwracany typ może reprezentować <xref:System.Object> metodę, która ma <xref:System.Collections.IEnumerable>parametr typu i zwracaną wartość typu . Aby uzyskać więcej informacji <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>i przykładowy kod, zobacz .  
  
 Mówi się, że delegat jest powiązany z metodą, którą reprezentuje. Oprócz powiązanego z metodą pełnomocnik może być powiązany z obiektem. Obiekt reprezentuje pierwszy parametr metody i jest przekazywany do metody za każdym razem, gdy delegat jest wywoływany. Jeśli metoda jest metodą wystąpienia, obiekt powiązany `this` jest`Me` przekazywany jako parametr niejawny (w języku Visual Basic); Jeśli metoda jest statyczna, obiekt jest przekazywany jako pierwszy formalny parametr metody, a podpis delegata musi być zgodny z pozostałymi parametrami. Aby uzyskać więcej informacji <xref:System.Delegate?displayProperty=nameWithType>i przykładowy kod, zobacz .  
  
 Wszyscy pełnomocnicy dziedziczą z <xref:System.MulticastDelegate?displayProperty=nameWithType>, który dziedziczy z <xref:System.Delegate?displayProperty=nameWithType>. Języki C#, Visual Basic i C++ nie zezwalają na dziedziczenie z tych typów. Zamiast tego zapewniają słowa kluczowe do deklarowania delegatów.  
  
 Ponieważ delegaci dziedziczą z <xref:System.MulticastDelegate>, delegat ma listę wywołań, która jest lista metod, które reprezentuje delegata i które są wykonywane po wywołaniu delegata. Wszystkie metody na liście otrzymują argumenty podane podczas wywoływania delegata.  
  
> [!NOTE]
> Wartość zwracana nie jest zdefiniowana dla pełnomocnika, który ma więcej niż jedną metodę na liście wywołania, nawet jeśli pełnomocnik ma typ zwracany.  
  
 W wielu przypadkach, takich jak metody wywołania wywołania, pełnomocnik reprezentuje tylko jedną metodę, a jedyne akcje, które należy podjąć, to tworzenie delegata i wywoływanie go.  
  
 W przypadku delegatów <xref:System.Delegate> reprezentujących wiele metod .NET <xref:System.MulticastDelegate> udostępnia metody klas i delegować do obsługi operacji, takich jak <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> dodawanie metody do listy <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> wywołania delegata (metoda), <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> usuwanie metody (metody) i uzyskiwanie listy wywołania (metoda).  
  
> [!NOTE]
> Nie jest konieczne użycie tych metod dla delegatów obsługi zdarzeń w językach C#, C++ i Visual Basic, ponieważ te języki zapewniają składnię dodawania i usuwania programów obsługi zdarzeń.  

<a name="type_definitions"></a>
## <a name="type-definitions"></a>Definicje typu  
 Definicja typu obejmuje następujące elementy:  
  
- Wszystkie atrybuty zdefiniowane na typie.  
  
- Dostępność typu (widoczność).  
  
- Nazwa typu.  
  
- Typ podstawowy typu.  
  
- Wszystkie interfejsy zaimplementowane przez typ.  
  
- Definicje dla każdego z elementów członkowskich typu.  
  
### <a name="attributes"></a>Atrybuty  
 Atrybuty zapewniają dodatkowe metadane zdefiniowane przez użytkownika. Najczęściej są one używane do przechowywania dodatkowych informacji o typie w jego zestawie lub do modyfikowania zachowania elementu członkowskiego typu w środowisku w czasie projektowania lub w czasie wykonywania.  
  
 Atrybuty są same klasy, które dziedziczą z <xref:System.Attribute?displayProperty=nameWithType>. Języki, które obsługują użycie atrybutów każdy ma własną składnię do stosowania atrybutów do elementu języka. Atrybuty mogą być stosowane do prawie każdego elementu języka; określone elementy, do których można zastosować atrybut, <xref:System.AttributeUsageAttribute> są definiowane przez, który jest stosowany do tej klasy atrybutu.  
  
### <a name="type-accessibility"></a>Wpisz ułatwienia dostępu  
 Wszystkie typy mają modyfikator, który reguluje ich dostępność z innych typów. W poniższej tabeli opisano accessibilities typu obsługiwane przez program runtime.  
  
|Ułatwienia dostępu|Opis|  
|-------------------|-----------------|  
|public|Typ jest dostępny dla wszystkich zestawów.|  
|zestaw|Typ jest dostępny tylko z jego zestawu.|  
  
 Dostępność typu zagnieżdżonego zależy od jego domeny ułatwień dostępu, która jest określana zarówno przez zadeklarowaną dostępność elementu członkowskiego, jak i domenę ułatwień dostępu typu natychmiast zawierającego. Jednak domena ułatwień dostępu typu zagnieżdżonego nie może przekraczać domeny zawierającej.  
  
 Domena ułatwień dostępu `M` zagnieżdżonego `P` elementu członkowskiego zadeklarowanego w `M` typie `T` w programie jest zdefiniowana w następujący sposób (odnotowując, że sam może być typem):  
  
- Jeśli zadeklarowana `M` dostępność `public`jest , `M` domena ułatwień `T`dostępu jest domeną ułatwień dostępu .  
  
- Jeśli zadeklarowana `M` dostępność `protected internal`jest , `M` domena ułatwień dostępu `T` jest przecięcie `P` domeny dostępności z tekstem `T` programu `P`i tekst programu dowolnego typu pochodzącego z zadeklarowanego na zewnątrz .  
  
- Jeśli zadeklarowana `M` dostępność `protected`jest , `M` domena ułatwień dostępu `T` jest przecięcie `T` domeny ułatwień `T`dostępu z tekstem programu i dowolnego typu pochodzącego z .  
  
- Jeśli zadeklarowana `M` dostępność `internal`jest , `M` domena ułatwień dostępu `T` jest przecięcie `P`domeny ułatwień dostępu z tekstem programu .  
  
- Jeśli zadeklarowana `M` dostępność `private`jest , `M` domena ułatwień `T`dostępu jest tekst programu .  
  
### <a name="type-names"></a>Nazwy typów  
 Wspólny system typów nakłada tylko dwa ograniczenia na nazwy:  
  
- Wszystkie nazwy są kodowane jako ciągi znaków Unicode (16-bitowych).  
  
- Nazwy nie mogą mieć osadzonej (16-bitowej) wartości 0x0000.  
  
 Jednak większość języków nakłada dodatkowe ograniczenia na nazwy typów. Wszystkie porównania są wykonywane na zasadzie bajt po bajcie i dlatego są uwzględniane wielkości liter i niezależne od ustawień regionalnych.  
  
 Mimo że typ może odwoływać się do typów z innych modułów i zestawów, typ musi być w pełni zdefiniowany w ramach jednego modułu .NET. (W zależności od obsługi kompilatora można go jednak podzielić na wiele plików kodu źródłowego). Nazwy typów muszą być unikatowe tylko w obszarze nazw. Aby w pełni zidentyfikować typ, nazwa typu musi być kwalifikowana przez obszar nazw, który zawiera implementację typu.  
  
### <a name="base-types-and-interfaces"></a>Typy podstawowe i interfejsy  
 Typ może dziedziczyć wartości i zachowania z innego typu. Wspólny system typów nie zezwala na dziedziczenie typów z więcej niż jednego typu podstawowego.  
  
 Typ można zaimplementować dowolną liczbę interfejsów. Aby zaimplementować interfejs, typ musi zaimplementować wszystkie wirtualne elementy członkowskie tego interfejsu. Metoda wirtualna może być implementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie.  

<a name="type_members"></a>
## <a name="type-members"></a>Składowe typu  
 Czas wykonywania umożliwia definiowanie elementów członkowskich typu, który określa zachowanie i stan typu. Elementy członkowskie typu są następujące:  
  
- [Pola](#Fields)  
  
- [Właściwości](#Properties)  
  
- [Metody](#Methods)  
  
- [Konstruktory](#Constructors)  
  
- [Zdarzenia](#Events)  
  
- [Typy zagnieżdżone](#NestedTypes)  
  
<a name="Fields"></a>
### <a name="fields"></a>Pola  
 Pole opisuje i zawiera część stanu typu. Pola mogą być dowolnego typu obsługiwane przez program runtime. Najczęściej pola są albo `private` `protected`lub , tak, że są one dostępne tylko z klasy lub z klasy pochodnej. Jeśli wartość pola można modyfikować spoza jego typu, akcesor zestawu właściwości jest zwykle używany. Publicznie widoczne pola są zwykle tylko do odczytu i mogą być dwojakiego rodzaju:  
  
- Stałe, których wartość jest przypisana w czasie projektowania. Są to statyczne elementy członkowskie klasy, chociaż nie `static` `Shared` są one zdefiniowane przy użyciu (w języku Visual Basic) słowa kluczowego.  
  
- Zmienne tylko do odczytu, których wartości można przypisać w konstruktorze klasy.  
  
 W poniższym przykładzie przedstawiono te dwa zastosowania pól tylko do odczytu.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>
### <a name="properties"></a>Właściwości  
 Właściwość nazywa wartość lub stan typu i definiuje metody uzyskiwania lub ustawiania wartości właściwości. Właściwości mogą być typy pierwotne, kolekcje typów pierwotnych, typy zdefiniowane przez użytkownika lub kolekcje typów zdefiniowanych przez użytkownika. Właściwości są często używane do zachowania interfejsu publicznego typu niezależnego od rzeczywistej reprezentacji typu. Dzięki temu właściwości odzwierciedlają wartości, które nie są bezpośrednio przechowywane w klasie (na przykład, gdy właściwość zwraca obliczoną wartość) lub do wykonywania sprawdzania poprawności przed wartości są przypisane do pól prywatnych. Poniższy przykład ilustruje ten ostatni wzorzec.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Oprócz dotym samej właściwości, język pośredni firmy Microsoft (MSIL) dla typu, który zawiera właściwość `get_`czytelną zawiera metodę *propertyname* i MSIL dla typu, który zawiera zapisywalną właściwość zawiera `set_`metodę *propertyname.*  
  
<a name="Methods"></a>
### <a name="methods"></a>Metody  
 Metoda opisuje operacje, które są dostępne na typ. Podpis metody określa dopuszczalne typy wszystkich jej parametrów i jego wartości zwracanej.  
  
 Chociaż większość metod zdefiniować dokładną liczbę parametrów wymaganych do wywołań metody, niektóre metody obsługują zmienną liczbę parametrów. Końcowy zadeklarowany parametr tych metod jest <xref:System.ParamArrayAttribute> oznaczony atrybutem. Kompilatory języka zazwyczaj zapewniają `params` słowo kluczowe, `ParamArray` takie jak w języku <xref:System.ParamArrayAttribute> C# i visual basic, który sprawia, że jawne użycie niepotrzebne.  
  
<a name="Constructors"></a>
### <a name="constructors"></a>Konstruktorów  
 Konstruktor jest specjalnym rodzajem metody, która tworzy nowe wystąpienia klasy lub struktury. Podobnie jak każda inna metoda konstruktora może zawierać parametry; jednak konstruktory nie mają wartości zwracanej `void`(oznacza to, że zwracają).  
  
 Jeśli kod źródłowy dla klasy nie jawnie zdefiniować konstruktora, kompilator zawiera konstruktora bezparametrowego. Jednak jeśli kod źródłowy dla klasy definiuje tylko sparametryzowane konstruktory, kompilatory Języka Visual Basic i C# nie generują konstruktora bezparametrów.  
  
 Jeśli kod źródłowy dla struktury definiuje konstruktorów, muszą być parametryzowane; struktura nie może zdefiniować konstruktora bezparametrów, a kompilatory nie generują konstruktorów bezparametrów dla struktur lub innych typów wartości. Wszystkie typy wartości mają niejawny konstruktor bezparametrów. Ten konstruktor jest implementowany przez program runtime języka wspólnego i inicjuje wszystkie pola struktury do ich wartości domyślnych.  
  
<a name="Events"></a>
### <a name="events"></a>Zdarzenia  
 Zdarzenie definiuje zdarzenie, na które można odpowiedzieć, i definiuje metody subskrybowania, cofania subskrypcji i podnoszenia zdarzenia. Zdarzenia są często używane do informowania innych typów zmian stanu. Aby uzyskać więcej informacji, zobacz [Wydarzenia](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>
### <a name="nested-types"></a>Zagnieżdżone typy  
 Typ zagnieżdżony jest typem, który jest członkiem innego typu. Typy zagnieżdżone powinny być ściśle powiązane z ich typem zawierającym i nie mogą być przydatne jako typ ogólnego przeznaczenia. Typy zagnieżdżone są przydatne, gdy typ deklarujący używa i tworzy wystąpienia typu zagnieżdżonego, a użycie typu zagnieżdżonego nie jest widoczne w publicznych elementów członkowskich.  
  
 Typy zagnieżdżone są mylące dla niektórych deweloperów i nie powinny być publicznie widoczne, chyba że istnieje istotny powód do widoczności. W dobrze zaprojektowanej bibliotece deweloperzy rzadko muszą używać typów zagnieżdżonych do tworzenia wystąpienia obiektów lub deklarowania zmiennych.  

<a name="characteristics_of_type_members"></a>
## <a name="characteristics-of-type-members"></a>Charakterystyka członków typu  
 Wspólny system typów umożliwia członkom typu różne cechy; jednak języki nie są wymagane do obsługi wszystkich tych cech. W poniższej tabeli opisano charakterystykę elementu członkowskiego.  
  
|Charakterystyka|Może mieć zastosowanie do|Opis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, właściwości i zdarzenia|Typ nie dostarcza implementacji metody. Typy, które dziedziczą lub implementują metody abstrakcyjne, muszą dostarczyć implementację dla metody. Jedynym wyjątkiem jest, gdy typ pochodny jest sam typu abstrakcyjnego. Wszystkie metody abstrakcyjne są wirtualne.|  
|prywatne, rodzinne, zgromadzeń, rodziny i montażystów, rodziny lub montażu lub|Wszystkie|Definiuje dostępność elementu członkowskiego:<br /><br /> private<br /> Dostępne tylko z tego samego typu co element członkowski lub w obrębie typu zagnieżdżonego.<br /><br /> rodzina<br /> Dostępne z tego samego typu co element członkowski i z typów pochodnych, które dziedziczą z niego.<br /><br /> zestaw<br /> Dostępne tylko w złożeniu, w którym zdefiniowano typ.<br /><br /> rodzina i montaż<br /> Dostępne tylko z typów, które kwalifikują się zarówno do rodziny, jak i do zestawu.<br /><br /> rodzina lub montaż<br /> Dostępne tylko z typów, które kwalifikują się do dostępu do rodziny lub zestawu.<br /><br /> public<br /> Dostępne z dowolnego typu.|  
|końcowe|Metody, właściwości i zdarzenia|Metoda wirtualna nie może zostać zastąpiona w typie pochodnym.|  
|tylko inicjowanie|Pola|Wartość może być inicjowana tylko i nie można jej zapisać po zainicjowaniu.|  
|Wystąpienie|Pola, metody, właściwości i zdarzenia|Jeśli element członkowski `static` nie jest oznaczony jako `Shared` (C# `virtual` i C++), (Visual Basic), (C# i C++) lub `Overridable` (Visual Basic), jest członkiem wystąpienia (nie ma słowa kluczowego wystąpienia). Będzie tyle kopii takich elementów członkowskich w pamięci, jak istnieją obiekty, które go używają.|  
|literal|Pola|Wartość przypisana do pola jest stałą wartością wbudowanego typu wartości, znaną w czasie kompilacji. Pola literału są czasami określane jako stałe.|  
|newslot lub zastąpić|Wszystkie|Definiuje sposób interakcji członka z dziedziczonymi członkami, które mają ten sam podpis:<br /><br /> Newslot<br /> Ukrywa dziedziczone elementy członkowskie, które mają ten sam podpis.<br /><br /> override<br /> Zastępuje definicję dziedziczonej metody wirtualnej.<br /><br /> Wartością domyślną jest newslot.|  
|static|Pola, metody, właściwości i zdarzenia|Element członkowski należy do typu, na którym jest zdefiniowany, a nie do określonego wystąpienia typu; element członkowski istnieje, nawet jeśli wystąpienie typu nie jest tworzony i jest współużytkowany przez wszystkie wystąpienia typu.|  
|virtual|Metody, właściwości i zdarzenia|Metoda może być implementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie. Jeśli używane jest wywołanie dynamiczne, typ wystąpienia, które sprawia, że wywołanie w czasie wykonywania (a nie typ znany w czasie kompilacji) określa, która implementacja metody jest wywoływana. Aby wywołać metodę wirtualną statycznie, zmienna może być rzutowania do typu, który używa żądanej wersji metody.|  
  
### <a name="overloading"></a>Przeciążenie  
 Każdy element członkowski typu ma unikatowy podpis. Podpisy metody składają się z nazwy metody i listy parametrów (kolejność i typy argumentów metody). Wiele metod o tej samej nazwie można zdefiniować w typie, o ile różnią się ich podpisy. Gdy zdefiniowano dwie lub więcej metod o tej samej nazwie, metoda jest określana jako przeciążona. Na przykład <xref:System.Char?displayProperty=nameWithType>w <xref:System.Char.IsDigit%2A> , metoda jest przeciążona. Jedna metoda <xref:System.Char>trwa . Druga metoda ma <xref:System.String> i <xref:System.Int32>.  
  
> [!NOTE]
> Typ zwracany nie jest uważany za część podpisu metody. Oznacza to, że metody nie mogą być przeciążone, jeśli różnią się tylko przez typ zwracany.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dziedziczenie, zastępowanie i ukrywanie elementów członkowskich  
 Typ pochodny dziedziczy wszystkie elementy członkowskie jego typu podstawowego; oznacza to, że te elementy członkowskie są zdefiniowane na i dostępne dla typu pochodnego. Zachowanie lub cechy dziedzicznych elementów członkowskich można modyfikować na dwa sposoby:  
  
- Typ pochodny można ukryć dziedziczony element członkowski, definiując nowy element członkowski z tym samym podpisem. Można to zrobić, aby wcześniej publiczny członek był prywatny lub aby zdefiniować `final`nowe zachowanie dla dziedziczonej metody oznaczonej jako .  
  
- Typ pochodny można zastąpić dziedziczonemetody wirtualnej. Metoda zastępowania zawiera nową definicję metody, która będzie wywoływana na podstawie typu wartości w czasie wykonywania, a nie typu zmiennej znanej w czasie kompilacji. Metoda może zastąpić metodę wirtualną tylko wtedy, gdy `final` metoda wirtualna nie jest oznaczona jako i nowa metoda jest co najmniej tak dostępna jak metoda wirtualna.  
  
## <a name="see-also"></a>Zobacz też

- [Przeglądarka interfejsu API .NET](/dotnet/api)
- [środowiska uruchomieniowe w trakcie wykonania](../../../docs/standard/clr.md)
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
