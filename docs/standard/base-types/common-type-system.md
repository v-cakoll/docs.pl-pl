---
title: System typu wspólnego
description: Dowiedz się więcej o systemie typu w .NET.
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
ms.openlocfilehash: ec078ea89befedd26ce205c724193935dd08b82a
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523955"
---
# <a name="common-type-system"></a>System typów wspólnych

System typu typ typ definiuje, jak typy są deklarowane, używane i zarządzane w czasie wykonywania języka wspólnego, a także jest ważną częścią środowiska wykonawczego obsługi integracji między językami. System typu common spełnia następujące funkcje:  
  
- Ustanawia strukturę, która pomaga włączyć integrację między językami, bezpieczeństwo typu i wykonywanie kodu o wysokiej wydajności.  
  
- Udostępnia model obiektowy, który obsługuje pełną implementację wielu języków programowania.  
  
- Definiuje reguły, które języki muszą przestrzegać, co pomaga zapewnić, że obiekty napisane w różnych językach mogą współdziałać ze sobą.  
  
- Udostępnia bibliotekę zawierającą podstawowe typy danych <xref:System.Boolean> <xref:System.Byte>(takie <xref:System.Int32>jak <xref:System.UInt64>, <xref:System.Char>, , i ) używane w tworzeniu aplikacji.
  
## <a name="types-in-net"></a>Typy w .NET

 Wszystkie typy w .NET są typami wartości lub typami odwołań.  
  
 Typy wartości to typy danych, których obiekty są reprezentowane przez rzeczywistą wartość obiektu. Jeśli do zmiennej przypisane jest wystąpienie typu wartości, zmienna ta otrzymuje nową kopię wartości.  
  
 Typy odwołań to typy danych, których obiekty są reprezentowane przez odwołanie (podobne do wskaźnika) do rzeczywistej wartości obiektu. Jeśli typ odwołania jest przypisany do zmiennej, ta zmienna odwołuje się (wskazuje na) oryginalną wartość. Nie jest wykonana żadna kopia.  
  
 Wspólny system typów w .NET obsługuje następujące pięć kategorii typów:  
  
- [Klasy](#classes)  
  
- [Struktury](#structures)  
  
- [Wyliczenia](#enumerations)  
  
- [Interfejsy](#interfaces)  
  
- [Delegaty](#delegates)  
  
### <a name="classes"></a>Klasy

 Klasa jest typem odwołania, który może pochodzić bezpośrednio z innej klasy <xref:System.Object?displayProperty=nameWithType>i który jest pochodną niejawnie z . Klasa definiuje operacje, które obiekt (który jest wystąpieniem klasy) może wykonywać (metody, zdarzenia lub właściwości) i dane, które zawiera obiekt (pola). Chociaż klasa zazwyczaj zawiera zarówno definicji i implementacji (w przeciwieństwie do interfejsów, na przykład, które zawierają tylko definicji bez implementacji), może mieć jeden lub więcej elementów członkowskich, które nie mają implementacji.  
  
 W poniższej tabeli opisano niektóre cechy, które klasa może mieć. Każdy język, który obsługuje środowisko uruchomieniowe umożliwia wskazanie, że element członkowski klasy lub klasy ma jedną lub więcej z tych cech. Jednak poszczególne języki programowania, które są przeznaczone .NET może nie udostępnić wszystkie te cechy.  
  
|Charakterystyka|Opis|  
|--------------------|-----------------|  
|sealed|Określa, że nie można wyprowadzić innej klasy z tego typu.|  
|implements|Wskazuje, że klasa używa jednego lub więcej interfejsów, zapewniając implementacje elementów członkowskich interfejsu.|  
|abstract|Wskazuje, że nie można utworzyć wystąpienia klasy. Aby go użyć, należy wyprowadzić z niego inną klasę.|  
|Dziedziczy|Wskazuje, że wystąpienia klasy mogą być używane w dowolnym miejscu, w dowolnym miejscu określono klasę podstawową. Klasa pochodna, która dziedziczy z klasy podstawowej można użyć implementacji wszelkich elementów członkowskich publicznych dostarczonych przez klasę podstawową lub klasy pochodnej można zastąpić implementacji elementów członkowskich publicznych z własnej implementacji.|  
|eksportowane lub nie wywożone|Wskazuje, czy klasa jest widoczna poza zestawem, w którym jest zdefiniowana. Ta cecha dotyczy tylko klas najwyższego poziomu, a nie klas zagnieżdżonych.|  
  
> [!NOTE]
> Klasa może być również zagnieżdżona w klasie nadrzędnej lub strukturze. Klasy zagnieżdżone mają również cechy członkowskie. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](#nested-types).  
  
 Elementy członkowskie klasy, które nie mają implementacji są abstrakcyjne elementy członkowskie. Klasa, która ma jeden lub więcej abstrakcyjnych elementów członkowskich jest sama abstrakcyjna; nie można utworzyć nowych wystąpień. Niektóre języki, które są przeznaczone dla środowiska wykonawczego pozwalają oznaczyć klasę jako abstrakcyjną, nawet jeśli żaden z jej elementów członkowskich są abstrakcyjne. Klasy abstrakcyjnej można użyć, gdy chcesz hermetyzować podstawowy zestaw funkcji, które klasy pochodne mogą dziedziczyć lub zastępować w razie potrzeby. Klasy, które nie są abstrakcyjne są określane jako konkretne klasy.  
  
 Klasa może implementować dowolną liczbę interfejsów, ale może dziedziczyć <xref:System.Object?displayProperty=nameWithType>tylko z jednej klasy podstawowej oprócz , z którego wszystkie klasy dziedziczą niejawnie. Wszystkie klasy muszą mieć co najmniej jeden konstruktor, który inicjuje nowe wystąpienia klasy. Jeśli nie zostanie jawnie zdefiniować konstruktora, większość kompilatorów automatycznie dostarczy konstruktora bez parametrów.  
  
### <a name="structures"></a>Struktury

 Struktura jest typem wartości, który <xref:System.ValueType?displayProperty=nameWithType>wywodzi się niejawnie z , który z kolei pochodzi od <xref:System.Object?displayProperty=nameWithType>. Struktura jest bardzo przydatna do reprezentowania wartości, których wymagania dotyczące pamięci są małe, oraz do przekazywania wartości jako parametrów według wartości do metod, które mają silnie wpisane parametry. W .NET wszystkie pierwotne typy <xref:System.Char>danych <xref:System.DateTime> <xref:System.Decimal>( <xref:System.Double><xref:System.Boolean> <xref:System.Byte>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, , <xref:System.Int16>, , , , , , , , , i ) są definiowane jako struktury.  
  
 Podobnie jak klasy, struktury definiują zarówno dane (pola struktury), jak i operacje, które mogą być wykonywane na tych danych (metody struktury). Oznacza to, że można wywołać metody na strukturach, w tym wirtualne metody zdefiniowane na <xref:System.Object?displayProperty=nameWithType> i <xref:System.ValueType?displayProperty=nameWithType> klasy i wszelkie metody zdefiniowane na sam typ wartości. Innymi słowy struktury mogą mieć pola, właściwości i zdarzenia, a także metody statyczne i niestatyczne. Można tworzyć wystąpienia struktur, przekazywać je jako parametry, przechowywać je jako zmienne lokalne lub przechowywać je w polu innego typu wartości lub typu odwołania. Struktury można również implementować interfejsy.  
  
 Typy wartości różnią się również od klas pod kilkoma względami. Po pierwsze, chociaż niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType>, nie mogą bezpośrednio dziedziczyć z dowolnego typu. Podobnie wszystkie typy wartości są zapieczętowane, co oznacza, że żaden inny typ nie może być pochodzący z nich. Nie wymagają one również konstruktorów.  
  
 Dla każdego typu wartości środowisko uruchomieniowe języka wspólnego dostarcza odpowiedni typ pudełkowy, który jest klasą, która ma ten sam stan i zachowanie jako typ wartości. Wystąpienie typu wartości jest zapakowane, gdy jest przekazywane do metody, <xref:System.Object?displayProperty=nameWithType>która akceptuje parametr typu . Jest rozpakowany (czyli przekonwertowany z wystąpienia klasy z powrotem na wystąpienie typu wartości), gdy formant zwraca z wywołania metody, która akceptuje typ wartości jako parametr by-reference. Niektóre języki wymagają użycia specjalnej składni, gdy wymagany jest typ pudełkowy; inne automatycznie używają typu pudełkowego, gdy jest to potrzebne. Podczas definiowania typu wartości definiuje się zarówno typ pudełkowy, jak i bez zapakowany.  
  
### <a name="enumerations"></a>Wyliczenia

 Wyliczenie jest typem wartości, który <xref:System.Enum?displayProperty=nameWithType> dziedziczy bezpośrednio z i który dostarcza alternatywnych nazw dla wartości typu pierwotnego podstawowej. Typ wyliczenia ma nazwę, typ podstawowy, który musi być jednym z wbudowanych podpisanych lub <xref:System.Byte> <xref:System.Int32>niepodpisanych typów liczby całkowitej (np. , lub <xref:System.UInt64>) i zestaw pól. Pola są statycznymi dosłowne pola, z których każdy reprezentuje stałą. Tę samą wartość można przypisać do wielu pól. W takim przypadku należy oznaczyć jedną z wartości jako podstawową wartość wyliczenia dla odbicia i konwersji ciągów.  
  
 Można przypisać wartość typu źródłowego do wyliczenia i odwrotnie (nie rzutowanie jest wymagane przez środowisko wykonawcze). Można utworzyć wystąpienie wyliczenia i wywołać <xref:System.Enum?displayProperty=nameWithType>metody , a także wszelkie metody zdefiniowane na typie podstawowym wyliczenia. Jednak niektóre języki mogą nie pozwolić na przekazanie wyliczenia jako parametru, gdy wymagane jest wystąpienie typu źródłowego (lub odwrotnie).  
  
 Następujące dodatkowe ograniczenia mają zastosowanie do wyliczenia:  
  
- Nie mogą definiować własnych metod.  
  
- Nie można zaimplementować interfejsów.  
  
- Nie można zdefiniować właściwości lub zdarzeń.  
  
- Nie mogą być ogólne, chyba że są one ogólne tylko dlatego, że są zagnieżdżone w typie ogólnym. Oznacza to, że wyliczenie nie może mieć własnych parametrów typu.  
  
    > [!NOTE]
    > Typy zagnieżdżone (w tym wyliczenia) utworzone za pomocą języka Visual Basic, C#, i C++ zawierają parametry typu wszystkich otaczających typów ogólnych i dlatego są ogólne, nawet jeśli nie mają własnych parametrów typu. Aby uzyskać więcej informacji, zobacz "Typy zagnieżdżone" w temacie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> odwołania.  
  
 Atrybut <xref:System.FlagsAttribute> oznacza specjalny rodzaj wyliczenia o nazwie pole bitowe. Sam środowisko uruchomieniowe nie rozróżnia tradycyjnych wyliczeń i pól bitowych, ale twój język może to zrobić. Po dokonaniu tego rozróżnienia operatory bitowe mogą być używane w polach bitowych, ale nie w wyliczeniach do generowania wartości bez nazwy. Wyliczenia są zwykle używane dla list unikatowych elementów, takich jak dni tygodnia, nazwy kraju lub regionu i tak dalej. Pola bitowe są zwykle używane dla list jakości lub ilości, `Red And Big And Fast`które mogą wystąpić w połączeniu, takich jak .  
  
 W poniższym przykładzie pokazano, jak używać zarówno pól bitowych, jak i tradycyjnych wyliczeń.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  

### <a name="interfaces"></a>Interfejsy

 Interfejs definiuje kontrakt, który określa relację "można zrobić" lub relację "ma" . Interfejsy są często używane do implementowania funkcji, takich <xref:System.IComparable> jak <xref:System.IComparable%601> porównywanie i sortowanie <xref:System.IEquatable%601> (i interfejsy), testowanie równości <xref:System.Collections.IEnumerable> (interfejs) lub wyliczanie elementów w kolekcji (i <xref:System.Collections.Generic.IEnumerable%601> interfejsów). Interfejsy mogą mieć właściwości, metody i zdarzenia, z których wszystkie są abstrakcyjnymi członkami; oznacza to, że chociaż interfejs definiuje członków i ich podpisy, pozostawia go do typu, który implementuje interfejs do definiowania funkcji każdego elementu członkowskiego interfejsu. Oznacza to, że każda klasa lub struktura, która implementuje interfejs musi dostarczyć definicje dla abstrakcyjnych elementów członkowskich zadeklarowanych w interfejsie. Interfejs może wymagać dowolnej klasy lub struktury implementującej, aby również zaimplementować jeden lub więcej innych interfejsów.  
  
 Do interfejsów obowiązują następujące ograniczenia:  
  
- Interfejs można zadeklarować z dowolnej ułatwień dostępu, ale elementy członkowskie interfejsu muszą mieć dostępność publiczną.  
  
- Interfejsy nie można zdefiniować konstruktorów.  
  
- Interfejsy nie mogą definiować pól.  
  
- Interfejsy można zdefiniować tylko elementy członkowskie wystąpienia. Nie mogą definiować statycznych elementów członkowskich.  
  
 Każdy język musi zawierać reguły mapowania implementacji do interfejsu, który wymaga elementu członkowskiego, ponieważ więcej niż jeden interfejs może zadeklarować element członkowski z tym samym podpisem, a te elementy członkowskie mogą mieć oddzielne implementacje.  

### <a name="delegates"></a>Delegaty

 Delegaty są typy odwołań, które służą cel podobny do wskaźników funkcji w języku C++. Są one używane do obsługi zdarzeń i funkcji wywołania zwrotnego w .NET. W przeciwieństwie do wskaźników funkcji, delegatów są bezpieczne, weryfikowalne i typu bezpieczne. Typ delegata może reprezentować dowolną metodę wystąpienia lub metodę statyczną, która ma zgodny podpis.  
  
 Parametr delegata jest zgodny z odpowiednim parametrem metody, jeśli typ parametru delegata jest bardziej restrykcyjny niż typ parametru metody, ponieważ gwarantuje to, że argument przekazany delegatowi może być bezpiecznie przekazany do metody.  
  
 Podobnie typ zwracany delegata jest zgodny z typem zwracania metody, jeśli typ zwracany metody jest bardziej restrykcyjny niż typ zwracany delegata, ponieważ gwarantuje to, że zwracana wartość metody może być bezpiecznie rzutowana do typu zwracanego delegata.  
  
 Na przykład delegat, który ma <xref:System.Collections.IEnumerable> parametr typu i <xref:System.Object> typ zwracany może reprezentować <xref:System.Object> metodę, która <xref:System.Collections.IEnumerable>ma parametr typu i zwracaną wartość typu . Aby uzyskać więcej informacji <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>i przykładowy kod, zobacz .  
  
 Delegat jest powiedział, że jest powiązany z metodą, która reprezentuje. Oprócz powiązanych z metodą, delegat może być powiązany z obiektem. Obiekt reprezentuje pierwszy parametr metody i jest przekazywany do metody za każdym razem, gdy jest wywoływany delegat. Jeśli metoda jest metodą wystąpienia, obiekt powiązany `this` jest`Me` przekazywany jako parametr niejawny (w języku Visual Basic); Jeśli metoda jest statyczna, obiekt jest przekazywany jako pierwszy formalny parametr metody, a podpis delegata musi być zgodny z pozostałymi parametrami. Aby uzyskać więcej informacji <xref:System.Delegate?displayProperty=nameWithType>i przykładowy kod, zobacz .  
  
 Wszyscy delegaci dziedziczą <xref:System.MulticastDelegate?displayProperty=nameWithType> <xref:System.Delegate?displayProperty=nameWithType>po , który dziedziczy po . Języki C#, Visual Basic i C++ nie zezwalają na dziedziczenie z tych typów. Zamiast tego zapewniają słowa kluczowe do deklarowania delegatów.  
  
 Ponieważ delegaci dziedziczą z <xref:System.MulticastDelegate>, delegat ma listę wywołania, która jest listą metod, które reprezentuje delegata i które są wykonywane podczas wywoływania pełnomocnika. Wszystkie metody na liście otrzymują argumenty podane podczas wywoływania pełnomocnika.  
  
> [!NOTE]
> Zwracana wartość nie jest zdefiniowana dla pełnomocnika, który ma więcej niż jedną metodę na liście wywołania, nawet jeśli pełnomocnik ma typ zwracany.  
  
 W wielu przypadkach, takich jak z metody wywołania zwrotnego delegat reprezentuje tylko jedną metodę, a tylko akcje, które należy podjąć są tworzenie delegata i wywoływanie go.  
  
 <xref:System.Delegate> Dla delegatów, które reprezentują wiele metod.NET <xref:System.MulticastDelegate> udostępnia metody i delegata klas do obsługi operacji, takich <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> jak dodawanie metody do <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> listy wywołania delegata (metoda), <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> usuwanie metody (metoda) i uzyskanie listy wywołania (metoda).  
  
> [!NOTE]
> Nie jest konieczne użycie tych metod dla delegatów obsługi zdarzeń w językach C#, C++ i Visual Basic, ponieważ te języki zapewniają składnię do dodawania i usuwania programów obsługi zdarzeń.  

## <a name="type-definitions"></a>Definicje typów

 Definicja typu obejmuje następujące elementy:  
  
- Wszelkie atrybuty zdefiniowane w typie.  
  
- Dostępność typu (widoczność).  
  
- Nazwa typu.  
  
- Typ podstawowy typu.  
  
- Wszelkie interfejsy zaimplementowane przez typ.  
  
- Definicje dla każdego z członków typu.  
  
### <a name="attributes"></a>Atrybuty  
 Atrybuty zapewniają dodatkowe metadane zdefiniowane przez użytkownika. Najczęściej są one używane do przechowywania dodatkowych informacji o typie w jego zestawie lub do modyfikowania zachowania elementu członkowskiego typu w środowisku czasu projektowania lub środowiska wykonywania.  
  
 Atrybuty to same <xref:System.Attribute?displayProperty=nameWithType>klasy, które dziedziczą po . Języki, które obsługują użycie atrybutów każdy mają własną składnię stosowania atrybutów do elementu języka. Atrybuty mogą być stosowane do prawie każdego elementu języka; określone elementy, do których można zastosować atrybut są <xref:System.AttributeUsageAttribute> definiowane przez który jest stosowany do tej klasy atrybutu.  
  
### <a name="type-accessibility"></a>Typ ułatwień dostępu  
 Wszystkie typy mają modyfikator, który reguluje ich dostępność z innych typów. W poniższej tabeli opisano możliwości dostępu do typów obsługiwane przez środowisko wykonawcze.  
  
|Ułatwienia dostępu|Opis|  
|-------------------|-----------------|  
|public|Typ jest dostępny dla wszystkich zestawów.|  
|zestaw|Typ jest dostępny tylko z poziomu jego zestawu.|  
  
 Dostępność typu zagnieżdżonego zależy od jego domeny ułatwień dostępu, która jest określana zarówno przez zadeklarowaną dostępność elementu członkowskiego, jak i domenę ułatwień dostępu typu bezpośrednio zawierającego. Jednak domena ułatwień dostępu typu zagnieżdżonego nie może przekraczać domeny typu zawierającego.  
  
 Domena ułatwień dostępu `M` zagnieżdżonego `P` elementu członkowskiego zadeklarowanego `M` w typie `T` w programie jest zdefiniowana w następujący sposób (zauważając, że może to być typ):  
  
- Jeśli deklarowana `M` dostępność `public`jest , `M` domeną ułatwień `T`dostępu jest domena ułatwień dostępu .  
  
- Jeśli deklarowana `M` dostępność `protected internal`jest , `M` domeną ułatwień dostępu `T` jest przecięcie domeny ułatwień dostępu z tekstem programu `P` i tekstem programu dowolnego typu uzyskanym z `T` zadeklarowanego poza programem `P`.  
  
- Jeśli deklarowana `M` dostępność `protected`jest , `M` domeną ułatwień dostępu `T` jest przecięcie domeny ułatwień dostępu z tekstem programu `T` i dowolnym typem pochodzącym z `T`.  
  
- Jeśli deklarowana `M` dostępność `internal`jest , `M` domeną ułatwień dostępu `T` jest przecięcie domeny ułatwień dostępu z tekstem programu `P`.  
  
- Jeśli deklarowana `M` dostępność `private`jest , `M` domeną ułatwień `T`dostępu jest tekst programu .  
  
### <a name="type-names"></a>Nazwy typów  
 System typów wspólnych nakłada tylko dwa ograniczenia na nazwy:  
  
- Wszystkie nazwy są kodowane jako ciągi znaków Unicode (16-bitowych).  
  
- Nazwy nie mogą mieć osadzonej (16-bitowej) wartości 0x0000.  
  
 Jednak większość języków nakłada dodatkowe ograniczenia na nazwy typów. Wszystkie porównania są wykonywane na podstawie bajt po bajcie i dlatego są zależne od wielkości liter i ustawień regionalnych.  
  
 Chociaż typ może odwoływać się do typów z innych modułów i zestawów, typ musi być w pełni zdefiniowany w ramach jednego modułu .NET. (W zależności od obsługi kompilatora można go jednak podzielić na wiele plików kodu źródłowego). Nazwy typów muszą być unikatowe tylko w obszarze nazw. Aby w pełni zidentyfikować typ, nazwa typu musi być kwalifikowana przez obszar nazw, który zawiera implementację typu.  
  
### <a name="base-types-and-interfaces"></a>Typy bazowe i interfejsy  
 Typ może dziedziczyć wartości i zachowania z innego typu. System typów typowych nie zezwala na dziedziczenie typów z więcej niż jednego typu podstawowego.  
  
 Typ można zaimplementować dowolną liczbę interfejsów. Aby zaimplementować interfejs, typ musi implementować wszystkie wirtualne elementy członkowskie tego interfejsu. Metoda wirtualna może być zaimplementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie.  

## <a name="type-members"></a>Typ elementy członkowskie

 Środowisko wykonawcze umożliwia definiowanie elementów członkowskich typu, który określa zachowanie i stan typu. Elementy członkowskie typu są następujące:  
  
- [Pola](#fields)  
  
- [Właściwości](#properties)  
  
- [Metody](#methods)  
  
- [Konstruktorów](#constructors)  
  
- [Zdarzenia](#events)  
  
- [Typy zagnieżdżone](#nested-types)  

### <a name="fields"></a>Pola

 Pole opisuje i zawiera część stanu typu. Pola mogą być dowolnego typu obsługiwane przez środowisko wykonawcze. Najczęściej pola są albo `private` lub `protected`, tak, że są one dostępne tylko z wewnątrz klasy lub z klasy pochodnej. Jeśli wartość pola można zmodyfikować spoza jego typu, zazwyczaj używany jest akcesor zestawu właściwości. Pola publicznie eksponowane są zwykle tylko do odczytu i mogą mieć dwa typy:  
  
- Stałe, których wartość jest przypisana w czasie projektowania. Są to statyczne elementy członkowskie klasy, chociaż `static` nie`Shared` są definiowane przy użyciu słowa kluczowego (w języku Visual Basic).  
  
- Zmienne tylko do odczytu, których wartości można przypisać w konstruktorze klasy.  
  
 Poniższy przykład ilustruje te dwa użycia pól tylko do odczytu.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  

### <a name="properties"></a>Właściwości

 Właściwość nazywa wartość lub stan typu i definiuje metody uzyskiwania lub ustawiania wartości właściwości. Właściwości mogą być typami pierwotnymi, kolekcjami typów pierwotnych, typami zdefiniowanymi przez użytkownika lub kolekcjami typów zdefiniowanych przez użytkownika. Właściwości są często używane do utrzymania interfejsu publicznego typu niezależne od rzeczywistej reprezentacji typu. Dzięki temu właściwości odzwierciedlać wartości, które nie są bezpośrednio przechowywane w klasie (na przykład, gdy właściwość zwraca obliczoną wartość) lub do wykonywania sprawdzania poprawności przed wartości są przypisane do pól prywatnych. Poniższy przykład ilustruje ten ostatni wzorzec.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Oprócz włączenia samej właściwości, języka pośredniego firmy Microsoft (MSIL) dla typu, który zawiera `get_`właściwość czytelną zawiera metodę *propertyname,* `set_`a MSIL dla typu, który zawiera właściwość zapisywalną zawiera metodę *propertyname.*  

### <a name="methods"></a>Metody

 Metoda opisuje operacje, które są dostępne dla typu. Podpis metody określa dopuszczalne typy wszystkich jej parametrów i jego wartość zwracaną.  
  
 Chociaż większość metod definiuje dokładną liczbę parametrów wymaganych dla wywołań metod, niektóre metody obsługują zmienną liczbę parametrów. Końcowy zadeklarowany parametr tych metod <xref:System.ParamArrayAttribute> jest oznaczony atrybutem. Kompilatory języka zazwyczaj zapewniają słowo `params` kluczowe, `ParamArray` takie jak w języku C# i visual basic, który sprawia, że jawne użycie niepotrzebne. <xref:System.ParamArrayAttribute>  

### <a name="constructors"></a>Konstruktorów

 Konstruktor jest specjalnym rodzajem metody, która tworzy nowe wystąpienia klasy lub struktury. Jak każda inna metoda, konstruktor może zawierać parametry; jednak konstruktory nie mają wartości zwracanej (oznacza to, że zwracają). `void`  
  
 Jeśli kod źródłowy dla klasy nie jawnie zdefiniować konstruktora, kompilator zawiera konstruktora bez parametrów. Jeśli jednak kod źródłowy dla klasy definiuje tylko parametryzowane konstruktory, kompilatory Języka Visual Basic i C# nie generują konstruktora bez parametrów.  
  
 Jeśli kod źródłowy dla struktury definiuje konstruktory, muszą być parametryzowane; struktura nie może zdefiniować konstruktora bez parametrów, a kompilatory nie generują konstruktorów bez parametrów dla struktur lub innych typów wartości. Wszystkie typy wartości mają niejawną konstruktora bez parametrów. Ten konstruktor jest implementowany przez środowisko uruchomieniowe języka wspólnego i inicjuje wszystkie pola struktury do ich wartości domyślnych.  

### <a name="events"></a>Zdarzenia

 Zdarzenie definiuje zdarzenie, na które można odpowiedzieć, i definiuje metody subskrybowania, anulowania subskrypcji i wywoływania zdarzenia. Zdarzenia są często używane do informowania innych typów zmian stanu. Aby uzyskać więcej informacji, zobacz [Zdarzenia](../../../docs/standard/events/index.md).  

### <a name="nested-types"></a>Typy zagnieżdżone

 Typ zagnieżdżony jest typem, który jest elementem członkowskim innego typu. Typy zagnieżdżone powinny być ściśle powiązane z ich typem zawierającym i nie mogą być przydatne jako typ ogólnego przeznaczenia. Typy zagnieżdżone są przydatne, gdy typ deklarujący używa i tworzy wystąpienia typu zagnieżdżonego, a użycie typu zagnieżdżonego nie jest widoczne w elementach publicznych.  
  
 Typy zagnieżdżone są mylące dla niektórych deweloperów i nie powinny być publicznie widoczne, chyba że istnieje istotny powód do widoczności. W dobrze zaprojektowanej bibliotece deweloperzy rzadko powinni używać typów zagnieżdżonych do tworzenia wystąpienia obiektów lub deklarowania zmiennych.  

## <a name="characteristics-of-type-members"></a>Charakterystyka elementów członkowskich typu

 System typu typpowszechniany może mieć różne cechy; jednak języki nie są wymagane do obsługi wszystkich tych cech. W poniższej tabeli opisano charakterystyki elementu członkowskiego.  
  
|Charakterystyka|Może odnosić się do|Opis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, właściwości i zdarzenia|Typ nie dostarcza implementacji metody. Typy, które dziedziczą lub implementują metody abstrakcyjne, muszą dostarczać implementację dla tej metody. Jedynym wyjątkiem jest, gdy typ pochodny jest sam typ abstrakcyjny. Wszystkie metody abstrakcyjne są wirtualne.|  
|prywatne, rodzinne, zgromadzenia, rodziny i zgromadzenia, rodziny lub zgromadzenia lub|Wszystkie|Definiuje dostępność elementu członkowskiego:<br /><br /> private<br /> Dostępne tylko z tego samego typu co element członkowski lub w obrębie typu zagnieżdżonego.<br /><br /> rodzina<br /> Dostępne z tego samego typu co element członkowski i z typów pochodnych, które dziedziczą z niego.<br /><br /> zestaw<br /> Dostępne tylko w złożeniu, w którym typ jest zdefiniowany.<br /><br /> rodzina i montaż<br /> Dostępne tylko z typów, które kwalifikują się do dostępu rodziny i zestawu.<br /><br /> rodzina lub montaż<br /> Dostępne tylko z typów, które kwalifikują się do dostępu rodziny lub zestawu.<br /><br /> public<br /> Dostępne z dowolnego typu.|  
|końcowe|Metody, właściwości i zdarzenia|Nie można zastąpić metody wirtualnej w typie pochodnym.|  
|tylko do inicjowania|Pola|Wartość może być zainicjowana tylko i nie może być zapisywana po inicjalizacji.|  
|Wystąpienie|Pola, metody, właściwości i zdarzenia|Jeśli element członkowski `static` nie jest oznaczony jako `Shared` (C# `virtual` i C++), (Visual `Overridable` Basic), (C# i C++) lub (Visual Basic), jest członkiem wystąpienia (nie ma słowa kluczowego wystąpienia). Będzie tyle kopii takich członków w pamięci, jak istnieją obiekty, które go używają.|  
|literal|Pola|Wartość przypisana do pola jest stałą wartością, znaną w czasie kompilacji, typu wbudowanej wartości. Pola dosłowne są czasami określane jako stałe.|  
|newslot lub zastąpić|Wszystkie|Określa, jak członek wchodzi w interakcję z odziedziczonymi członkami, którzy mają ten sam podpis:<br /><br /> Newslot<br /> Ukrywa odziedziczone elementy członkowskie, które mają ten sam podpis.<br /><br /> override<br /> Zastępuje definicję dziedziczonej metody wirtualnej.<br /><br /> Domyślnie jest newslot.|  
|static|Pola, metody, właściwości i zdarzenia|Element członkowski należy do typu, który jest zdefiniowany na, a nie do określonego wystąpienia typu; element członkowski istnieje, nawet jeśli wystąpienie typu nie jest tworzony i jest współużytkowane przez wszystkie wystąpienia typu.|  
|virtual|Metody, właściwości i zdarzenia|Metoda może być zaimplementowana przez typ pochodny i może być wywoływana statycznie lub dynamicznie. Jeśli wywoływanie dynamiczne jest używane, typ wystąpienia, które sprawia, że wywołanie w czasie wykonywania (a nie typ znany w czasie kompilacji) określa, która implementacja metody jest wywoływana. Aby wywołać metodę wirtualną statycznie, zmienna może być rzutowana na typ, który używa żądanej wersji metody.|  
  
### <a name="overloading"></a>Przeciążenie  
 Każdy element członkowski typu ma unikatowy podpis. Podpisy metody składają się z nazwy metody i listy parametrów (kolejność i typy argumentów metody). Wiele metod o tej samej nazwie można zdefiniować w ramach typu, o ile ich podpisy różnią się. Gdy zdefiniowano dwie lub więcej metod o tej samej nazwie, metoda jest określana jako przeciążona. Na przykład <xref:System.Char?displayProperty=nameWithType>w <xref:System.Char.IsDigit%2A> , metoda jest przeciążony. Jedna metoda <xref:System.Char>ma . Druga metoda ma <xref:System.String> i <xref:System.Int32>.  
  
> [!NOTE]
> Typ zwracany nie jest uważany za część podpisu metody. Oznacza to, że metody nie mogą być przeciążone, jeśli różnią się tylko według typu zwracania.  
  
### <a name="inherit-override-and-hide-members"></a>Dziedzicz, zastępuj i ukrywaj elementy członkowskie  
 Typ pochodny dziedziczy wszystkie elementy członkowskie swojego typu podstawowego; oznacza to, że te elementy członkowskie są zdefiniowane na i dostępne dla typu pochodnego. Zachowanie lub cechy odziedziczonych członków mogą być modyfikowane na dwa sposoby:  
  
- Typ pochodny można ukryć dziedzicznego elementu członkowskiego, definiując nowy element członkowski z tym samym podpisem. Można to zrobić, aby wcześniej publiczny element członkowski był prywatny lub zdefiniował `final`nowe zachowanie dla metody dziedziczonej, która jest oznaczona jako .  
  
- Typ pochodny może zastąpić dziedziczoną metodę wirtualną. Metoda zastępowania zawiera nową definicję metody, która będzie wywoływana na podstawie typu wartości w czasie wykonywania, a nie typu zmiennej znanej w czasie kompilacji. Metoda może zastąpić metodę wirtualną tylko wtedy, gdy `final` metoda wirtualna nie jest oznaczona jako i nowa metoda jest co najmniej tak dostępna jak metoda wirtualna.  
  
## <a name="see-also"></a>Zobacz też

- [Przeglądarka interfejsu API platformy .NET](/dotnet/api)
- [środowiska uruchomieniowe w trakcie wykonania](../../../docs/standard/clr.md)
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
