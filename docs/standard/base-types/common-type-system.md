---
title: System typu wspólnego
description: Dowiedz się więcej o systemie typów w programie .NET.
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
ms.custom: seodec18
ms.openlocfilehash: 050b2c2b8b55bc79cf388ce7a8c197b14f3437d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934766"
---
# <a name="common-type-system"></a>System typu wspólnego
Wspólny system typów definiuje, w jaki sposób typy są zadeklarowane, używane i zarządzane w środowisku uruchomieniowym języka wspólnego, i jest również ważną częścią obsługi integracji wielu języków przez środowisko uruchomieniowe. Wspólny system typów wykonuje następujące funkcje:  
  
- Ustanawia strukturę ułatwiającą integrację między językami, bezpieczeństwo typów i wykonywanie kodu o wysokiej wydajności.  
  
- Oferuje model zorientowany obiektowo, który obsługuje kompletną implementację wielu języków programowania.  
  
- Definiuje reguły, które Języki muszą spełniać, co pomaga zapewnić, że obiekty w różnych językach mogą współistnieć ze sobą.  
  
- Udostępnia bibliotekę, która zawiera typy danych pierwotnych (takie jak <xref:System.Boolean> <xref:System.Char>, <xref:System.Byte> <xref:System.Int32>,, i <xref:System.UInt64>) używane podczas tworzenia aplikacji.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Typy w programie .NET](#types_in_the_net_framework)  
  
- [Definicje typu](#type_definitions)  
  
- [Elementy członkowskie typu](#type_members)  
  
- [Charakterystyka elementów członkowskich typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy w programie .NET  
 Wszystkie typy w .NET są typami wartości lub typami referencyjnymi.  
  
 Typy wartości są typami danych, których obiekty są reprezentowane przez rzeczywistą wartość obiektu. Jeśli wystąpienie typu wartości jest przypisane do zmiennej, ta zmienna otrzymuje świeżą kopię wartości.  
  
 Typy odwołań to typy danych, których obiekty są reprezentowane przez odwołanie (podobne do wskaźnika) do rzeczywistej wartości obiektu. Jeśli typ odwołania jest przypisany do zmiennej, ta zmienna odwołuje się do oryginalnej wartości. Nie wykonano żadnej kopii.  
  
 Wspólny system typów w programie .NET obsługuje następujące pięć kategorii typów:  
  
- [Klasy](#Classes)  
  
- [Struktury](#Structures)  
  
- [Wyliczenia](#Enumerations)  
  
- [Interfejsy](#Interfaces)  
  
- [Delegaty](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Klasy  
 Klasa jest typem referencyjnym, który może być pochodny bezpośrednio z innej klasy i która jest pochodną <xref:System.Object?displayProperty=nameWithType>niejawnie z elementu. Klasa definiuje operacje, które obiekt (który jest wystąpieniem klasy) może wykonać (metody, zdarzenia lub właściwości) i dane, które zawiera obiekt (pola). Chociaż Klasa zazwyczaj obejmuje zarówno definicję, jak i implementację (w przeciwieństwie do interfejsów, na przykład, które zawierają tylko definicje bez implementacji), może mieć co najmniej jednego członka, który nie ma implementacji.  
  
 W poniższej tabeli opisano niektóre cechy, które może mieć Klasa. Każdy język, który obsługuje środowisko uruchomieniowe, zapewnia sposób wskazujący, że Klasa lub członek klasy ma jedną lub więcej z tych cech. Jednak poszczególne Języki programowania, które są przeznaczone dla platformy .NET, mogą nie udostępniać wszystkich tych cech.  
  
|Charakterystyk|Opis|  
|--------------------|-----------------|  
|sealed|Określa, że nie można dziedziczyć innej klasy z tego typu.|  
|implements|Wskazuje, że Klasa używa jednego lub więcej interfejsów, dostarczając implementacje elementów członkowskich interfejsu.|  
|abstract|Wskazuje, że nie można utworzyć wystąpienia klasy. Aby go użyć, należy utworzyć inną klasę od niej.|  
|Inherits|Wskazuje, że wystąpienia klasy mogą być używane wszędzie tam, gdzie określona jest klasa bazowa. Klasa pochodna, która dziedziczy z klasy bazowej, może korzystać z implementacji wszelkich publicznych składowych dostarczonych przez klasę bazową lub Klasa pochodna może zastąpić implementację publicznych członków własnym implementacją.|  
|wyeksportowany lub nie wyeksportowany|Wskazuje, czy Klasa jest widoczna poza zestawem, w którym jest zdefiniowana. Ta cecha ma zastosowanie tylko do klas najwyższego poziomu, a nie do klas zagnieżdżonych.|  
  
> [!NOTE]
> Klasa może być również zagnieżdżona w klasie nadrzędnej lub strukturze. Klasy zagnieżdżone mają również charakterystykę elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](#NestedTypes).  
  
 Elementy członkowskie klasy, które nie mają implementacji, są abstrakcyjnymi elementami członkowskimi. Klasa, która ma co najmniej jeden abstrakcyjny element członkowski, jest sama abstrakcyjna; nie można utworzyć nowych wystąpień tego elementu. Niektóre języki, które są przeznaczone dla środowiska uruchomieniowego, umożliwiają oznaczenie klasy jako abstrakcyjnej, nawet jeśli żaden z jej elementów członkowskich nie jest abstrakcyjny. Klasy abstrakcyjnej można użyć do hermetyzacji podstawowego zestawu funkcji, które klasy pochodne mogą dziedziczyć lub przesłaniać w razie potrzeby. Klasy, które nie są abstrakcyjne, są nazywane klasami konkretnymi.  
  
 Klasa może implementować dowolną liczbę interfejsów, ale może dziedziczyć tylko po jednej klasie bazowej oprócz <xref:System.Object?displayProperty=nameWithType>, z której wszystkie klasy dziedziczą niejawnie. Wszystkie klasy muszą mieć co najmniej jeden Konstruktor, który inicjuje nowe wystąpienia klasy. Jeśli Konstruktor nie zostanie jawnie zdefiniowany, większość kompilatorów automatycznie udostępni konstruktora bez parametrów.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura jest typem wartości, który wynika niejawnie z <xref:System.ValueType?displayProperty=nameWithType>, który z kolei jest wyprowadzany <xref:System.Object?displayProperty=nameWithType>z. Struktura jest bardzo przydatna do reprezentowania wartości, których wymagania dotyczące pamięci są małe, oraz przekazywania wartości jako parametrów przez wartość do metod, które mają parametry o jednoznacznie określonym typie. W programie .NET wszystkie typy danych pierwotnych<xref:System.Boolean>( <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime> <xref:System.Double> ,,<xref:System.Int64>, <xref:System.Int16>, <xref:System.Int32> ,,,,,<xref:System.SByte> <xref:System.Single> <xref:System.Decimal> <xref:System.UInt16> ,<xref:System.UInt32>, i<xref:System.UInt64>) są zdefiniowane jako struktury.  
  
 Podobnie jak klasy, struktury definiują zarówno dane (pola struktury), jak i operacje, które mogą być wykonywane na tych danych (metody struktury). Oznacza to, że można wywołać metody dla struktur, w tym metody wirtualne zdefiniowane w <xref:System.Object?displayProperty=nameWithType> klasach i <xref:System.ValueType?displayProperty=nameWithType> i wszelkie metody zdefiniowane w samej typie wartości. Inaczej mówiąc, struktury mogą mieć pola, właściwości i zdarzenia, a także metody statyczne i niestatyczne. Można utworzyć wystąpienia struktur, przekazać je jako parametry, zapisać je jako zmienne lokalne lub zapisać je w polu innego typu wartości lub typu odwołania. Struktury mogą również implementować interfejsy.  
  
 Typy wartości różnią się także od klas w kilku aspektach. Po pierwsze, chociaż niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType>, nie mogą dziedziczyć bezpośrednio z dowolnego typu. Podobnie wszystkie typy wartości są zapieczętowane, co oznacza, że żaden inny typ nie może być uzyskany z nich. Nie wymagają również konstruktorów.  
  
 Dla każdego typu wartości środowisko uruchomieniowe języka wspólnego dostarcza odpowiedni typ opakowany, który jest klasą, która ma ten sam stan i zachowanie co typ wartości. Wystąpienie typu wartości jest opakowane, gdy zostanie przesłane do metody, która akceptuje parametr typu <xref:System.Object?displayProperty=nameWithType>. Jest on nieopakowany (czyli konwertowany z wystąpienia klasy z powrotem do wystąpienia typu wartości), gdy sterowanie zwraca z wywołania metody, które akceptuje typ wartości jako parametr przez odwołanie. Niektóre języki wymagają użycia specjalnej składni, gdy wymagany jest typ opakowany; inne osoby automatycznie używają typu opakowanego, gdy jest to konieczne. Podczas definiowania typu wartości, definiuje się zarówno opakowany, jak i nieopakowany typ.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenie (Wyliczenie) jest typem wartości, który dziedziczy bezpośrednio z <xref:System.Enum?displayProperty=nameWithType> i dostarcza alternatywne nazwy dla wartości podstawowego typu pierwotnego. Typ wyliczenia ma nazwę, typ podstawowy, który musi być jednym z wbudowanych typów liczb całkowitych ze znakiem lub bez znaku (takich jak <xref:System.Byte>, <xref:System.Int32>, lub <xref:System.UInt64>) i zestaw pól. Pola to statyczne pola literału, z których każdy reprezentuje stałą. Tę samą wartość można przypisać do wielu pól. W takim przypadku należy oznaczyć jedną z wartości jako podstawową wartość wyliczenia dla odbicia i konwersji ciągów.  
  
 Do wyliczenia i na odwrót można przypisać wartość typu podstawowego (w czasie wykonywania nie jest wymagane rzutowanie). Można utworzyć wystąpienie wyliczenia i wywołać metody <xref:System.Enum?displayProperty=nameWithType>, a także wszelkie metody zdefiniowane w typie podstawowym wyliczenia. Jednak niektóre języki mogą nie zezwalać na przekazywanie wyliczenia jako parametru, gdy wymagane jest wystąpienie typu podstawowego (lub odwrotnie).  
  
 Następujące dodatkowe ograniczenia dotyczą wyliczeń:  
  
- Nie mogą definiować własnych metod.  
  
- Nie mogą implementować interfejsów.  
  
- Nie mogą definiować właściwości ani zdarzeń.  
  
- Nie mogą one być ogólne, chyba że są ogólne tylko, ponieważ są zagnieżdżone w obrębie typu ogólnego. Oznacza to, że Wyliczenie nie może mieć własnych parametrów typu.  
  
    > [!NOTE]
    > Zagnieżdżone typy (w tym wyliczenia) utworzone za pomocą Visual Basic C#, i C++ obejmują parametry typu wszystkich otaczających typów ogólnych i dlatego są ogólne, nawet jeśli nie mają własnych parametrów typu. Aby uzyskać więcej informacji, zobacz "typy zagnieżdżone" w <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> temacie Reference.  
  
 Ten <xref:System.FlagsAttribute> atrybut oznacza specjalny rodzaj wyliczenia nazywany polem bitowym. Samo środowisko uruchomieniowe nie rozróżnia tradycyjnych wyliczeń i pól bitowych, ale język może to zrobić. Po wykonaniu tego rozróżnienia operatory bitowe mogą być używane w polach bitowych, ale nie w wyliczeniach, aby generować wartości nienazwanych. Wyliczenia są zwykle używane dla list unikatowych elementów, takich jak dni tygodnia, nazwy kraju lub regionu i tak dalej. Pola bitowe są zwykle używane dla list jakości lub ilości, które mogą wystąpić w połączeniu, takich jak `Red And Big And Fast`.  
  
 Poniższy przykład pokazuje, jak używać pól bitowych i tradycyjnych wyliczeń.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Interfejsy  
 Interfejs definiuje kontrakt, który określa relację "może być" lub "ma". Interfejsy są często używane do implementowania funkcji, takich jak porównywanie i sortowanie <xref:System.IComparable> ( <xref:System.IComparable%601> interfejsy i), <xref:System.IEquatable%601> testowanie pod kątem równości (interfejs) lub <xref:System.Collections.IEnumerable> wyliczanie elementów w kolekcji (i <xref:System.Collections.Generic.IEnumerable%601> interfejsy). Interfejsy mogą mieć właściwości, metody i zdarzenia, z których wszystkie są abstrakcyjnymi elementami członkowskimi; oznacza to, że chociaż interfejs definiuje elementy członkowskie i ich podpisy, opuszcza typ, który implementuje interfejs, aby zdefiniować funkcje każdego elementu członkowskiego interfejsu. Oznacza to, że każda klasa lub struktura implementująca interfejs musi podawać definicje dla abstrakcyjnych elementów członkowskich zadeklarowanych w interfejsie. Interfejs może wymagać dowolnej klasy lub struktury implementującej w celu zaimplementowania co najmniej jednego innego interfejsu.  
  
 Do interfejsów stosowane są następujące ograniczenia:  
  
- Interfejs można zadeklarować z dowolnym ułatwieniam dostępu, ale wszystkie elementy członkowskie interfejsu muszą mieć dostęp publiczny.  
  
- Interfejsy nie mogą definiować konstruktorów.  
  
- Interfejsy nie mogą definiować pól.  
  
- Interfejsy mogą definiować tylko elementy członkowskie wystąpień. Nie mogą definiować statycznych elementów członkowskich.  
  
 Każdy język musi dostarczyć reguły mapowania implementacji do interfejsu, który wymaga elementu członkowskiego, ponieważ więcej niż jeden interfejs może deklarować składową z tym samym podpisem, a te elementy członkowskie mogą mieć oddzielne implementacje.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegaty  
 Delegaty są typami odwołań, które służą do celów podobnych do wskaźników funkcji C++w. Są one używane na potrzeby obsługi zdarzeń i funkcji wywołania zwrotnego w programie .NET. W przeciwieństwie do wskaźników funkcji Delegaty są bezpieczne, sprawdzalne i typu bezpieczne. Typ delegata może reprezentować każdą metodę wystąpienia lub metodę statyczną, która ma zgodną sygnaturę.  
  
 Parametr delegata jest zgodny z odpowiadającym mu parametrem metody, jeśli typ parametru delegata jest bardziej restrykcyjny niż typ parametru metody, ponieważ gwarantuje to, że argument przesłany do delegata może być bezpiecznie przekazywać do Metoda.  
  
 Analogicznie, zwracany typ delegata jest zgodny z typem zwracanym metody, Jeśli zwracany typ metody jest bardziej restrykcyjny niż typ zwracany delegata, ponieważ gwarantuje to, że wartość zwracana metody może być bezpiecznie rzutowana na typ zwracany e delegata.  
  
 Na przykład delegat, który <xref:System.Collections.IEnumerable> ma parametr typu i zwracany <xref:System.Object> typ może reprezentować metodę, która ma parametr typu <xref:System.Object> i wartość zwracaną typu <xref:System.Collections.IEnumerable>. Aby uzyskać więcej informacji i przykładowy kod, <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>Zobacz.  
  
 Delegat jest określany jako powiązany z metodą, która reprezentuje. Oprócz powiązania z metodą delegata można powiązać z obiektem. Obiekt reprezentuje pierwszy parametr metody i jest przenoszona do metody za każdym razem, gdy obiekt delegowany jest wywoływany. Jeśli metoda jest metodą wystąpienia, obiekt powiązany jest przenoszona jako parametr niejawny `this` (`Me` w Visual Basic); Jeśli metoda jest statyczna, obiekt jest przenoszona jako pierwszy parametr formalny metody, a podpis delegata musi być zgodny Pozostałe parametry. Aby uzyskać więcej informacji i przykładowy kod, <xref:System.Delegate?displayProperty=nameWithType>Zobacz.  
  
 Wszyscy pełnomocnicy dziedziczą po elemencie <xref:System.MulticastDelegate?displayProperty=nameWithType>, który dziedziczy z. <xref:System.Delegate?displayProperty=nameWithType> Języki C#, Visual Basic i C++ nie zezwalają na dziedziczenie z tych typów. Zamiast tego dostarczają słowa kluczowe do deklarowania delegatów.  
  
 Ponieważ obiekty delegowane <xref:System.MulticastDelegate>dziedziczą z, delegat ma listę wywołań, która jest listą metod, które reprezentuje obiekt delegowany i są wykonywane, gdy obiekt delegowany jest wywoływany. Wszystkie metody na liście odbierają argumenty dostarczone, gdy obiekt delegowany jest wywoływany.  
  
> [!NOTE]
> Wartość zwracana nie jest zdefiniowana dla delegata, który ma więcej niż jedną metodę na liście wywołań, nawet jeśli delegat ma zwracany typ.  
  
 W wielu przypadkach, takich jak metody wywołania zwrotnego, delegat reprezentuje tylko jedną metodę, a jedyne akcje, które należy wykonać, tworzą delegata i wywołującego go.  
  
 W przypadku delegatów reprezentujących wiele metod platforma .NET udostępnia metody <xref:System.Delegate> i <xref:System.MulticastDelegate> klasy delegatów do obsługi operacji, takich jak dodawanie metody do listy wywołań delegata ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> Metoda), usuwanie metody ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> Metoda) i pobieranie listy wywołań ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> Metoda).  
  
> [!NOTE]
> Nie jest konieczne używanie tych metod w przypadku delegatów obsługi zdarzeń w C#, C++, i Visual Basic, ponieważ Języki te zawierają składnię do dodawania i usuwania programów obsługi zdarzeń.  

<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definicje typu  
 Definicja typu zawiera następujące elementy:  
  
- Wszystkie atrybuty zdefiniowane w typie.  
  
- Dostępność typu (widoczność).  
  
- Nazwa typu.  
  
- Typ podstawowy typu.  
  
- Wszystkie interfejsy zaimplementowane przez typ.  
  
- Definicje dla każdego elementu członkowskiego typu.  
  
### <a name="attributes"></a>Atrybuty  
 Atrybuty zapewniają dodatkowe metadane zdefiniowane przez użytkownika. Najczęściej są one używane do przechowywania dodatkowych informacji o typie w zestawie lub do modyfikacji zachowania elementu członkowskiego typu w środowisku czasu projektowania lub czasu wykonywania.  
  
 Atrybuty są same klas, które dziedziczą z <xref:System.Attribute?displayProperty=nameWithType>. Języki, które obsługują korzystanie z atrybutów, mają własną składnię stosowania atrybutów do elementu języka. Atrybuty mogą być stosowane do niemal dowolnego elementu języka; określone elementy, do których można zastosować atrybut <xref:System.AttributeUsageAttribute> , są definiowane przez, który jest stosowany do tej klasy atrybutu.  
  
### <a name="type-accessibility"></a>Ułatwienia dostępu typu  
 Wszystkie typy mają modyfikator, który reguluje dostępność z innych typów. W poniższej tabeli opisano typ podano obsługiwany przez środowisko uruchomieniowe.  
  
|Ułatwienia dostępu|Opis|  
|-------------------|-----------------|  
|public|Typ jest dostępny dla wszystkich zestawów.|  
|zestaw|Typ jest dostępny tylko w obrębie swojego zestawu.|  
  
 Dostępność typu zagnieżdżonego zależy od jego domeny dostępności, który jest określany przez zadeklarowaną dostępność elementu członkowskiego i domenę dostępności typu natychmiastowego. Jednak domena dostępności typu zagnieżdżonego nie może przekroczyć tego typu zawierającego.  
  
 Domena `M` dostępności zagnieżdżonej składowej zadeklarowanej w typie `T` w ramach programu `P` jest zdefiniowana w następujący sposób (zwracając uwagę, `M` że może to być typ):  
  
- Jeśli zadeklarowane ułatwienia dostępu `M` to `public` `M` , domena dostępności jest domeną `T`dostępności.  
  
- Jeśli zadeklarowane ułatwienia dostępu `M` to `protected internal` `M` , domena dostępności jest częścią wspólną domeny `T` `P` dostępności z tekstem programu i tekstem programu dowolnego typu pochodzącego od zadeklarowany `P`poza. `T`  
  
- Jeśli zadeklarowana dostępność elementu `M` to `protected` `M` , domena dostępności jest częścią wspólną domeny `T` `T` dostępności z tekstem programu i dowolnym typem pochodnym `T`.  
  
- Jeśli zadeklarowana dostępność elementu `M` to `internal` `M` , domena dostępności jest częścią wspólną domeny `T` `P`dostępności z tekstem programu.  
  
- Jeśli zadeklarowana dostępność elementu `M` to `private` `M` , domena dostępności jest tekstem `T`programu.  
  
### <a name="type-names"></a>Nazwy typów  
 Wspólny system typów nakłada tylko dwa ograniczenia dotyczące nazw:  
  
- Wszystkie nazwy są kodowane jako ciągi znaków Unicode (16-bitowych).  
  
- Nazwy nie mogą mieć osadzonej wartości (16-bitowej) 0x0000.  
  
 Jednak większość języków nakłada dodatkowe ograniczenia dotyczące nazw typów. Wszystkie porównania są wykonywane w oparciu o bajt po bajcie i dlatego są zależne od wielkości liter i dla ustawień regionalnych.  
  
 Chociaż typ może odwoływać się do typów z innych modułów i zestawów, typ musi być w pełni zdefiniowany w obrębie jednego modułu .NET. (W zależności od obsługi kompilatora można jednak podzielić je na wiele plików kodu źródłowego). Nazwy typów muszą być unikatowe tylko w obrębie przestrzeni nazw. Aby w pełni identyfikować typ, nazwa typu musi być kwalifikowana według przestrzeni nazw zawierającej implementację typu.  
  
### <a name="base-types-and-interfaces"></a>Typy podstawowe i interfejsy  
 Typ może dziedziczyć wartości i zachowania z innego typu. Wspólny system typów nie zezwala na dziedziczenie typów z więcej niż jednego typu podstawowego.  
  
 Typ może implementować dowolną liczbę interfejsów. Aby zaimplementować interfejs, typ musi implementować wszystkie wirtualne elementy członkowskie tego interfejsu. Metoda wirtualna może być implementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie.  

<a name="type_members"></a>   
## <a name="type-members"></a>Składowe typu  
 Środowisko uruchomieniowe umożliwia definiowanie elementów członkowskich typu, które określają zachowanie i stan typu. Elementy członkowskie typu są następujące:  
  
- [Pola](#Fields)  
  
- [Właściwości](#Properties)  
  
- [Metody](#Methods)  
  
- [Konstruktory](#Constructors)  
  
- [Zdarzenia](#Events)  
  
- [Typy zagnieżdżone](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pola  
 Pole opisuje i zawiera część stanu typu. Pola mogą być dowolnego typu obsługiwanego przez środowisko uruchomieniowe. Najczęściej są to pola `private` lub `protected`, dzięki czemu są dostępne tylko z poziomu klasy lub z klasy pochodnej. Jeśli wartość pola można zmodyfikować spoza jego typu, zwykle jest używana metoda dostępu do zestawu właściwości. Dostępne publicznie pola są zwykle tylko do odczytu i mogą być dwoma typami:  
  
- Stałe, których wartość jest przypisana w czasie projektowania. Są to statyczne elementy członkowskie klasy, chociaż nie są zdefiniowane za pomocą `static` słowa kluczowego (`Shared` w Visual Basic).  
  
- Zmienne tylko do odczytu, których wartości można przypisać w konstruktorze klasy.  
  
 Poniższy przykład ilustruje te dwa sposoby użycia pól tylko do odczytu.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Właściwości  
 Właściwość zawiera nazwę wartości lub stanu typu i definiuje metody pobierania lub ustawiania wartości właściwości. Właściwości mogą być typami pierwotnymi, kolekcjami typów pierwotnych, typami zdefiniowanymi przez użytkownika lub kolekcjami typów zdefiniowanych przez użytkownika. Właściwości są często używane, aby zachować publiczny interfejs typu niezależny od rzeczywistej reprezentacji typu. Dzięki temu właściwości mogą odzwierciedlać wartości, które nie są bezpośrednio przechowywane w klasie (na przykład gdy właściwość zwraca obliczoną wartość) lub aby przeprowadzić walidację przed przypisaniem wartości do pól prywatnych. Poniższy przykład ilustruje ten ostatni wzorzec.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Oprócz dołączania samej właściwości, język pośredni (MSIL) firmy Microsoft dla typu, który zawiera właściwość do odczytu, zawiera `get_`metodę *PropertyName* , a MSIL dla typu, który zawiera właściwość z możliwością zapisu, zawiera `set_` Metoda *PropertyName* .  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda opisuje operacje, które są dostępne dla tego typu. Sygnatura metody Określa dozwolone typy wszystkich jej parametrów i wartości zwracanej.  
  
 Chociaż większość metod definiuje dokładną liczbę parametrów wymaganych dla wywołań metod, niektóre metody obsługują zmienną liczbę parametrów. Końcowy zadeklarowany parametr tych metod jest oznaczony <xref:System.ParamArrayAttribute> atrybutem. Kompilatory języka zwykle dostarczają słowa kluczowego, takiego `params` jak C# w `ParamArray` i w <xref:System.ParamArrayAttribute> Visual Basic, co sprawia, że jawne użycie nie jest konieczne.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktorów  
 Konstruktor jest specjalnym rodzajem metody, która tworzy nowe wystąpienia klasy lub struktury. Podobnie jak w przypadku każdej innej metody, Konstruktor może zawierać parametry; jednak konstruktory nie mają zwracanych wartości (oznacza to, że `void`zwracają).  
  
 Jeśli kod źródłowy dla klasy nie definiuje jawnie konstruktora, kompilator zawiera konstruktora bez parametrów. Jeśli jednak kod źródłowy klasy definiuje tylko konstruktory sparametryzowane, Visual Basic i C# kompilatory nie generują konstruktora bez parametrów.  
  
 Jeśli kod źródłowy struktury definiuje konstruktory, muszą one być sparametryzowane; Struktura nie może definiować konstruktora bez parametrów, a kompilatory nie generują konstruktorów bezparametrów dla struktur lub innych typów wartości. Wszystkie typy wartości mają niejawny Konstruktor bez parametrów. Ten konstruktor jest implementowany przez środowisko uruchomieniowe języka wspólnego i inicjuje wszystkie pola struktury do ich wartości domyślnych.  
  
<a name="Events"></a>   
### <a name="events"></a>Zdarzenia  
 Zdarzenie definiuje zdarzenie, do którego można odpowiedzieć, i definiuje metody subskrybowania, anulowania subskrypcji i podnoszenia zdarzenia. Zdarzenia są często używane do informowania o zmianach stanu innego typu. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Zagnieżdżone typy  
 Typ zagnieżdżony jest typem, który jest elementem członkowskim innego typu. Zagnieżdżone typy powinny być ściśle sprzężone z ich typem zawierającym i nie mogą być przydatne jako typ ogólnego przeznaczenia. Zagnieżdżone typy są przydatne, gdy typ deklarujący używa i tworzy wystąpienia typu zagnieżdżonego, a użycie typu zagnieżdżonego nie jest ujawniane w publicznych składowych.  
  
 Zagnieżdżone typy są mylące dla niektórych deweloperów i nie powinny być publicznie widoczne, chyba że istnieje istotny powód widoczności. W dobrze zaprojektowanej bibliotece deweloperzy rzadko muszą używać zagnieżdżonych typów do tworzenia wystąpień obiektów lub deklarowania zmiennych.  

<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Charakterystyka elementów członkowskich typu  
 Wspólny system typów pozwala członkom typu mieć różne cechy; jednak języki nie są wymagane do obsługi wszystkich tych cech. W poniższej tabeli opisano charakterystyki elementu członkowskiego.  
  
|Charakterystyk|Może dotyczyć|Opis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, właściwości i zdarzenia|Typ nie dostarcza implementacji metody. Typy dziedziczące lub implementujące metody abstrakcyjne muszą dostarczać implementację metody. Jedyny wyjątek polega na tym, że typ pochodny jest własnym typem abstrakcyjnym. Wszystkie metody abstrakcyjne są wirtualne.|  
|prywatna, Rodzina, zestaw, Rodzina i zestaw, Rodzina lub zestaw lub publiczne|Wszystkie|Definiuje dostępność elementu członkowskiego:<br /><br /> private<br /> Dostępne tylko z tego samego typu co element członkowski lub w obrębie typu zagnieżdżonego.<br /><br /> rodziny<br /> Dostępne z tego samego typu co element członkowski oraz z typów pochodnych, które dziedziczą z niego.<br /><br /> zestaw<br /> Dostępne tylko w zestawie, w którym jest zdefiniowany typ.<br /><br /> Rodzina i zestaw<br /> Dostępne tylko z typów, które kwalifikują się do dostępu do rodziny i zestawu.<br /><br /> Rodzina lub zestaw<br /> Dostępne tylko z typów, które kwalifikują się do dostępu do rodziny lub zestawu.<br /><br /> public<br /> Dostępne z dowolnego typu.|  
|końcowe|Metody, właściwości i zdarzenia|Nie można zastąpić metody wirtualnej w typie pochodnym.|  
|tylko Inicjalizacja|Pola|Wartość może zostać zainicjowana i nie można jej zapisać po zainicjowaniu.|  
|instance|Pola, metody, właściwości i zdarzenia|Jeśli element członkowski nie jest oznaczony jako `static` (C# i C++), `Shared` (Visual Basic), `virtual` (C# i C++) lub `Overridable` (Visual Basic), jest to element członkowski wystąpienia (brak słowa kluczowego wystąpienia). Istnieje wiele kopii takich członków w pamięci, ponieważ istnieją obiekty, które go używają.|  
|literal|Pola|Wartość przypisana do pola to stała wartość, znana w czasie kompilacji, typu wartości wbudowanej. Pola literału są czasami określane jako stałe.|  
|NewSlot lub Przesłoń|Wszystkie|Definiuje sposób interakcji elementu członkowskiego z dziedziczonymi elementami członkowskimi, które mają taki sam podpis:<br /><br /> NewSlot<br /> Ukrywa dziedziczone elementy członkowskie, które mają taki sam podpis.<br /><br /> override<br /> Zastępuje definicję dziedziczonej metody wirtualnej.<br /><br /> Wartość domyślna to NewSlot.|  
|static|Pola, metody, właściwości i zdarzenia|Element członkowski należy do typu, który jest zdefiniowany w, a nie do określonego wystąpienia typu; element członkowski istnieje, nawet jeśli wystąpienie typu nie zostało utworzone i jest udostępniane między wszystkimi wystąpieniami tego typu.|  
|virtual|Metody, właściwości i zdarzenia|Metoda może być implementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie. W przypadku użycia wywołania dynamicznego typ wystąpienia, które wywołuje wywołanie w czasie wykonywania (a nie typ znany w czasie kompilacji) określa, która implementacja metody jest wywoływana. Aby wywołać metodę wirtualną statycznie, zmienna może być musiała być rzutowana na typ, który używa odpowiedniej wersji metody.|  
  
### <a name="overloading"></a>Przeciążenie  
 Każdy element członkowski typu ma unikatowy podpis. Sygnatury metod składają się z nazwy metody i listy parametrów (kolejność i typy argumentów metody). Wiele metod o tej samej nazwie można zdefiniować w obrębie typu, tak długo, jak ich podpisy różnią się. Gdy zdefiniowane są dwie lub więcej metod o tej samej nazwie, metoda jest określana jako przeciążona. Na przykład <xref:System.Char?displayProperty=nameWithType> <xref:System.Char.IsDigit%2A> , metoda jest przeciążona. Jedna metoda przyjmuje <xref:System.Char>. Druga metoda przyjmuje <xref:System.String> <xref:System.Int32>i.  
  
> [!NOTE]
> Zwracany typ nie jest uważany za część podpisu metody. Oznacza to, że metody nie mogą być przeciążone, jeśli różnią się tylko zwracanym typem.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dziedziczenie, zastępowanie i ukrywanie elementów członkowskich  
 Typ pochodny dziedziczy wszystkie elementy członkowskie jego typu podstawowego; oznacza to, że te składowe są zdefiniowane w, i dostępne dla, typ pochodny. Zachowanie lub jakość dziedziczonych elementów członkowskich można modyfikować na dwa sposoby:  
  
- Typ pochodny może ukryć Dziedziczony element członkowski przez zdefiniowanie nowego elementu członkowskiego o tej samej sygnaturze. Może to być zrobione, aby wcześniej publiczny element członkowski był prywatny lub definiować nowe zachowanie dla dziedziczonej metody, która jest oznaczona `final`jako.  
  
- Typ pochodny może przesłonić dziedziczonej metody wirtualnej. Metoda przesłaniania zapewnia nową definicję metody, która będzie wywoływana na podstawie typu wartości w czasie wykonywania, a nie typu zmiennej znanej w czasie kompilacji. Metoda może przesłonić metodę wirtualną tylko wtedy, gdy metoda wirtualna nie jest oznaczona `final` jako i Nowa metoda jest co najmniej równa dostępności jako metoda wirtualna.  
  
## <a name="see-also"></a>Zobacz także

- [Przeglądarka interfejsów API platformy .NET](/dotnet/api)
- [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md)
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
