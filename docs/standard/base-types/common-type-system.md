---
title: "System typu wspólnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26ee5cffd5e04a8c78cf5913b286fadfaab03c7c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="common-type-system"></a>System typu wspólnego
Wspólny system typów definiuje jak typy są zadeklarowane, używane i zarządzane przez środowisko uruchomieniowe języka wspólnego, a także jest ważnym elementem obsługi środowiska uruchomieniowego integracji między językami. Wspólny system typów wykonuje następujące funkcje:  
  
-   Ustanawia platforma, która pozwala enable integracji między językami, zabezpieczeń i wykonywanie kodu wysokiej wydajności.  
  
-   Udostępnia zorientowany obiektowo model obsługujący pełną wykonania wielu języków programowania.  
  
-   Definiuje reguły, które należy wykonać języków, co pomaga zapewnić, że obiekty napisane w różnych językach mogą współdziałać ze sobą.  
  
-   Udostępnia bibliotekę, która zawiera typy pierwotne danych (takich jak <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, i <xref:System.UInt64>) używany w aplikacjach.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Typy w .NET](#types_in_the_net_framework)  
  
-   [Definicje typu](#type_definitions)  
  
-   [Elementy członkowskie typu](#type_members)  
  
-   [Właściwości elementów członkowskich typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy w .NET  
 Wszystkie typy w .NET są typy wartości i typy referencyjne.  
  
 Typy wartości są typy danych, w których obiekty są reprezentowane przez wartość rzeczywistego obiektu. Jeśli wystąpienie typu wartości jest przypisany do zmiennej, tej zmiennej znajduje się świeżą kopię wartość.  
  
 Typy odwołań są typy danych, w których obiekty są reprezentowane przez odwołanie (podobne do wskaźnika) do wartości rzeczywistej obiektu. Jeśli typ referencyjny jest przypisany do zmiennej, tej zmiennej odwołuje się do (wskazuje) oryginalnej wartości. Kopia nie jest wykonywana.  
  
 Wspólny system typów w programie .NET obsługuje następujące pięć kategorii typów:  
  
-   [Klasy](#Classes)  
  
-   [Struktury](#Structures)  
  
-   [Wyliczenia](#Enumerations)  
  
-   [Interfejsy](#Interfaces)  
  
-   [Delegaci](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Klasy  
 Klasa jest typem referencyjnym, które mogą być uzyskane bezpośrednio z innej klasy ani niejawnie pochodzi z <xref:System.Object?displayProperty=nameWithType>. Klasa definiuje operacje, że obiekt (który jest wystąpieniem klasy) można wykonywać (metody, zdarzenia lub właściwości) oraz dane, że obiekt zawiera (pól). Mimo że klasy zwykle zawiera definicję i wykonania (w przeciwieństwie do interfejsów, na przykład zawierających tylko definicji bez wykonania), może mieć jeden lub więcej elementów członkowskich, które mają żadnej implementacji.  
  
 W poniższej tabeli opisano niektóre właściwości, które mogą być klasą. Każdego języka, który obsługuje środowisko uruchomieniowe zapewnia możliwość wskazania, że klasa lub element członkowski klasy zawiera co najmniej jeden z tych właściwości. Jednak poszczególnych języków programowania .NET obiektu docelowego może nie udostępnia tych właściwości.  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|sealed|Określa, że inna klasa nie może pochodzić z tego typu.|  
|implements|Wskazuje, czy klasa używa jednego lub więcej interfejsów zapewniając implementacje elementów członkowskich interfejsu.|  
|abstract|Wskazuje, że nie można utworzyć wystąpienia klasy. Aby go użyć, inna klasa musi pochodzić od niego.|  
|dziedziczy|Wskazuje, że wystąpień klasy mogą być używane wszędzie tam, gdzie klasa podstawowa jest określona. Klasy pochodnej, która dziedziczy po klasie podstawowej, można użyć implementacji wszystkie publiczne elementy członkowskie udostępnione przez klasę podstawową lub klasy pochodnej można zastąpić implementacji publiczne elementy członkowskie z własną implementację.|  
|wyeksportowane lub nie wyeksportowane|Wskazuje, czy klasa jest widoczny spoza zestawu, w którym jest zdefiniowany. Cecha ta ma zastosowanie tylko do klasy najwyższego poziomu, a nie w zagnieżdżonych klasach.|  
  
> [!NOTE]
>  Klasy mogą być zagnieżdżone w nadrzędnej klasy lub struktury. Klasy zagnieżdżone również mieć właściwości elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [zagnieżdżone typy](#NestedTypes).  
  
 Elementy członkowskie klasy, których implementacja nie są abstrakcyjne elementy członkowskie. Klasa, która ma co najmniej jeden abstrakcyjne elementy członkowskie jest abstrakcyjny; Nie można utworzyć nowego wystąpienia. Niektóre języki, które odnoszą się do środowiska uruchomieniowego umożliwiają oznaczenie klasy jako abstrakcyjny, nawet jeśli żaden z jego elementów członkowskich nie jest abstrakcyjna. Można użyć klasy abstrakcyjnej, aby hermetyzować podstawowy zestaw funkcji, która pochodzi z klasy mogą dziedziczyć lub zastąpienie, gdy jest to konieczne. Klasy, które nie są abstrakcyjne są określane jako konkretnych klas.  
  
 Klasę można zaimplementować dowolną liczbę interfejsów, ale może dziedziczyć tylko jedną klasę podstawową oprócz <xref:System.Object?displayProperty=nameWithType>, z którego wszystkie klasy dziedziczą niejawnie. Wszystkie klasy musi mieć co najmniej jednego konstruktora, który inicjuje nowe wystąpienia klasy. Jeśli nie zostanie jawnie zdefiniowana konstruktora, większość kompilatorów automatycznie zapewni domyślnego (bezparametrowego) konstruktora.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura jest typem wartości, która jest pochodną niejawnie <xref:System.ValueType?displayProperty=nameWithType>, który z kolei jest określana na podstawie <xref:System.Object?displayProperty=nameWithType>. Struktura jest bardzo przydatny, reprezentują wartości, którego wymagania dotyczące pamięci są małe i przekazywanie wartości jako parametrów i wartości do metod, które mają silnie typizowane parametrów. W środowisku .NET, wszystkie typy pierwotne (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64>) są zdefiniowane jako struktury.  
  
 Takich jak klasy struktury zdefiniować zarówno dane (pola struktury), jak i operacje, które można wykonać na tych danych (metody struktury). Oznacza to, że można wywołać metody w typie struktury, w tym metody wirtualne zdefiniowane dla <xref:System.Object?displayProperty=nameWithType> i <xref:System.ValueType?displayProperty=nameWithType> klasy i wszystkie metody zdefiniowane w typie wartości, sama. Innymi słowy struktury, mogą mieć pola, właściwości i zdarzeń, a także metody statyczne i Niestatyczne. Można utworzyć wystąpienia struktury, przekazywane jako parametry, przechowywać je jako zmienne lokalne lub przechowywać je w polu innego typu wartości lub typ odwołania. Struktury mogą także implementować interfejsów.  
  
 Typy wartości różnią się również z klas w wielu aspektach. Pierwszy, mimo że dziedziczą niejawnie z <xref:System.ValueType?displayProperty=nameWithType>, bezpośrednio nie mogą dziedziczyć dowolnego typu. Podobnie wszystkie typy wartości jest zapieczętowany, co oznacza, że żaden typ innych mogą pochodzić z nich. Ponadto nie wymagają konstruktorów.  
  
 Dla każdego typu wartości środowisko uruchomieniowe języka wspólnego dostarcza odpowiedniego typu opakowanego, co jest klasa, która ma taką samą stanu i zachowanie, ponieważ typ wartości. Wystąpienie typu wartości jest opakowany, gdy jest przekazywany do metody, która przyjmuje parametr typu <xref:System.Object?displayProperty=nameWithType>. Jest rozpakowany (to znaczy przekonwertować z wystąpienia klasy do wystąpienia typu wartości) podczas kontroli zwraca po wywołaniu metody akceptującego typ wartości jako parametr przez odwołanie. Niektóre języki wymagają użycia specjalnej składni, gdy typ opakowany jest wymagana; inne automatycznie używają typ opakowany, jeśli jest to potrzebne. Po zdefiniowaniu typu wartości definiowania ramce i rozpakowany typ.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenie (enum) jest typem wartości, która dziedziczy po bezpośrednio <xref:System.Enum?displayProperty=nameWithType> i że dostaw alternatywne nazwy dla wartości pierwotnych typu podstawowego. Typ wyliczeniowy ma nazwę typu podstawowego, który musi być jednego z typów wbudowanych całkowitą podpisem lub bez znaku (takie jak <xref:System.Byte>, <xref:System.Int32>, lub <xref:System.UInt64>) oraz zestawu pól. Pola są statyczne pola literału, z których każdy reprezentuje stałą. Taką samą wartość mogą być przypisane do wielu pól. W takiej sytuacji należy oznaczyć jedna z wartości jako wartość wyliczenia podstawowego odbicia i Konwersja ciągu.  
  
 Można przypisać wartości typu źródłowego na wyliczenie i na odwrót (rzutowania nie jest wymagane przez środowisko uruchomieniowe). Można utworzyć wystąpienia wyliczenia i wywołania metody <xref:System.Enum?displayProperty=nameWithType>oraz ewentualne metody zdefiniowane w typie podstawowym wyliczenia. Jednak w przypadku niektórych języków może nie umożliwiają przekazywanie wyliczenie jako parametr gdy wymagane jest wystąpienie typu podstawowego (lub odwrotnie).  
  
 Następujące dodatkowe ograniczenia są stosowane do wyliczenia:  
  
-   Nie można ich zdefiniować własne metody.  
  
-   Ich nie mogą implementować interfejsów.  
  
-   Nie można ich zdefiniować właściwości lub zdarzeń.  
  
-   Nie może być ogólny, chyba że są to ogólny tylko, ponieważ są one zagnieżdżone w obrębie typu ogólnego. Oznacza to wyliczenie nie może mieć parametrów typu własnych.  
  
    > [!NOTE]
    >  Zagnieżdżone typy (w tym wyliczenia) utworzone za pomocą języka Visual Basic, C# i C++ uwzględnia parametry typu otaczającego wszystkich typów ogólnych i w związku z tym są ogólne, nawet jeśli nie ma parametrów typu w swoich własnych. Aby uzyskać więcej informacji, zobacz "Typy zagnieżdżone" w <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> temat referencyjny.  
  
 <xref:System.FlagsAttribute> Atrybut oznacza specjalny rodzaj wyliczenie o nazwie pola bitowego. Wykonawcze nie rozróżnia tradycyjnych wyliczenia i pola bitowe, ale język może zrobić. Gdy ta rozróżnienia operatory bitowe można od pól bitowych, ale nie wyliczenia, do generowania wartości bez nazwy. Wyliczenia są zazwyczaj używane do listy unikatowych elementów, takich jak dni tygodnia, kraj lub region nazwy i tak dalej. Pola bitowe są zazwyczaj używane do listy klas lub ilości, które mogą wystąpić w połączeniu, takich jak `Red And Big And Fast`.  
  
 Poniższy przykład przedstawia użycie zarówno pól bitowych, jak i tradycyjnych wyliczenia.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Interfejsy  
 Interfejs definiuje kontrakt określa relację "można wykonać" lub "ma" relacji. Interfejsy są często używane do implementowania funkcje, takie jak porównywanie i sortowanie ( <xref:System.IComparable> i <xref:System.IComparable%601> interfejsów), testowanie równości ( <xref:System.IEquatable%601> interface), lub wyliczania elementów w kolekcji ( <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601> interfejsów). Interfejsy może mieć właściwości, metod i zdarzeń, które są abstrakcyjne elementy członkowskie; oznacza to mimo że interfejs definiuje elementy członkowskie i ich podpisów, pozostawia go do typu, który implementuje interfejs do definiowania funkcji każdy element członkowski interfejsu. Oznacza to, że klasy lub struktury, który implementuje interfejs musi podać definicje abstrakcyjne elementy członkowskie, zadeklarowany w interfejsie. Interfejs może wymagać implementującej klasy lub struktury, można też wdrożyć jeden lub więcej interfejsów.  
  
 Interfejsy, obowiązują następujące ograniczenia:  
  
-   Interfejs mogą być deklarowane z dowolnym ułatwień dostępu, ale wszystkie elementy członkowskie interfejsu muszą mieć powszechnej dostępności.  
  
-   Interfejsy nie mogą definiować konstruktorów.  
  
-   Interfejsy nie można zdefiniować pól.  
  
-   Interfejsy można zdefiniować tylko elementy członkowskie wystąpień. Nie można ich zdefiniować statyczne elementy członkowskie.  
  
 Każdego języka musi podać reguł do mapowania implementację interfejsu, który wymaga elementu członkowskiego, ponieważ więcej niż jeden interfejs można zadeklarować elementu członkowskiego o tej samej sygnaturze, a te elementy Członkowskie mogą mieć osobne implementacji.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegaty  
 Obiekty delegowane są typy odwołań, które służą do celów podobny do wskaźników funkcji w języku C++. Są one używane do obsługi zdarzeń i funkcje wywołania zwrotnego w programie .NET. W przeciwieństwie do wskaźników funkcji delegatów są bezpieczne, zweryfikowania i wpisz bezpieczne. Typ delegowany może reprezentować wszystkie wystąpienia metody lub metody statycznej, który ma niezgodny podpis.  
  
 Parametr typu delegata jest zgodny z odpowiadającego mu parametru metody, jeśli typ parametru delegowanego jest bardziej restrykcyjny niż typ parametru metody, ponieważ gwarantuje to, że argument przekazany do delegata można bezpiecznie przekazany do Metoda.  
  
 Podobnie zwracany typ delegata jest zgodny z typem zwracanym metody, jeśli typ zwracany metody jest bardziej restrykcyjny niż typ zwracany delegata, ponieważ gwarantuje to, że zwracana wartość metody mogą być bezpiecznie rzutowane na zwracany typ e delegata.  
  
 Na przykład delegata, który ma parametr typu <xref:System.Collections.IEnumerable> i typ zwracany <xref:System.Object> może reprezentować metodę, która ma parametr typu <xref:System.Object> i zwracanej wartości typu <xref:System.Collections.IEnumerable>. Aby uzyskać więcej informacji i przykładowy kod, zobacz <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Delegat jest nazywany powiązać metodę, która reprezentuje. Oprócz związana jest metoda, Delegat może być powiązana z obiektem. Obiekt reprezentuje pierwszy parametr metody i jest przekazywany do metody, za każdym razem, gdy jest wywoływany delegat. Jeśli metoda jest metodą wystąpienia, powiązany obiekt jest przekazywany jako niejawne `this` parametr (`Me` w języku Visual Basic); Jeśli metoda jest statyczna, obiekt został przekazany jako pierwszy formalny parametr metody i podpisu delegata musi być zgodna. pozostałe parametry. Aby uzyskać więcej informacji i przykładowy kod, zobacz <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Wszystkie obiekty delegowane dziedziczyć <xref:System.MulticastDelegate?displayProperty=nameWithType>, który dziedziczy z <xref:System.Delegate?displayProperty=nameWithType>. Języki C#, Visual Basic i C++ nie zezwalają na dziedziczenia z tych typów. Zamiast tego zawierają słowa kluczowe deklarowania delegatów.  
  
 Ponieważ dziedziczy delegatów <xref:System.MulticastDelegate>, delegat ma listę wywołań, czyli listę metod, które reprezentuje delegata i które są wykonywane, gdy jest wywoływany delegat. Wszystkie metody na liście odbierać argumenty podane po wywołaniu obiektu delegowanego.  
  
> [!NOTE]
>  Wartość zwrotna nie jest zdefiniowany dla delegata, który ma więcej niż jedną metodę liście wywołania, nawet jeśli delegat ma typ zwracany.  
  
 W wielu przypadkach takich jak w przypadku metod wywołania zwrotnego reprezentuje delegata tylko jedna metoda tylko akcje, które należy wykonać tworzenia delegata i wywoływanie go.  
  
 W przypadku delegatów, które reprezentują wiele metod .NET zapewnia metody <xref:System.Delegate> i <xref:System.MulticastDelegate> delegować klasy do obsługi operacji, takich jak dodawanie metody do listy wywołania delegata ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> metody), usuwanie metody ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> metodę) i pobieranie listy wywołania ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> metody).  
  
> [!NOTE]
>  Nie jest konieczne do użycia tych metod dla delegatów obsługi zdarzeń w języku C#, C++ i Visual Basic, ponieważ tych języków udostępnia składnię Dodawanie i usuwanie programów obsługi zdarzeń.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definicje typów  
 Definicja typu obejmuje następujące funkcje:  
  
-   Atrybuty zdefiniowane w typie.  
  
-   Typ ułatwień dostępu (widoczność).  
  
-   Nazwa typu.  
  
-   Typ podstawowy typu.  
  
-   Wszystkie interfejsy implementowane przez typ.  
  
-   Definicje dla wszystkich elementów członkowskich typu.  
  
### <a name="attributes"></a>Atrybuty  
 Atrybuty udostępnienia dodatkowych metadanych zdefiniowanych przez użytkownika. Najczęściej są one używane do przechowywania dodatkowych informacji o typie w jego zestaw lub modyfikowanie elementu członkowskiego typu w jednym środowisku projektowania lub czasu wykonywania.  
  
 Atrybuty są klasy, które dziedziczą z <xref:System.Attribute?displayProperty=nameWithType>. Języki, które obsługują atrybuty każdego ma swoje własne składnię stosowania atrybuty w elemencie języka. Atrybuty można zastosować do niemal wszystkich elementów języka; wynika z określonych elementów, do których można zastosować atrybutu <xref:System.AttributeUsageAttribute> do tej klasy atrybutu zastosowano.  
  
### <a name="type-accessibility"></a>Typ ułatwień dostępu  
 Wszystkie typy mają modyfikator, który zarządza ich dostępność z innych typów. W poniższej tabeli opisano dostępności typu obsługiwane przez środowisko uruchomieniowe.  
  
|Ułatwienia dostępu|Opis|  
|-------------------|-----------------|  
|public|Typ jest dostępny dla wszystkich zestawów.|  
|zestaw|Typ jest dostępny tylko w obrębie jej zestaw.|  
  
 Dostępność zagnieżdżony typ zależy od swojej domeny ułatwień dostępu, który jest określany przez zarówno zadeklarowane dostępność elementu członkowskiego i domena dostępności typu zawierającego natychmiast. Jednak domena dostępności typu zagnieżdżonego nie może przekraczać, który typu zawierającego.  
  
 Domena dostępności elementu członkowskiego zagnieżdżonych `M` zadeklarowana w typie `T` w programie `P` jest zdefiniowane w następujący sposób (biorąc pod uwagę, że `M` może być typem):  
  
-   Jeśli zadeklarowane dostępności `M` jest `public`, domena dostępności `M` jest domeną ułatwień dostępu `T`.  
  
-   Jeśli zadeklarowane dostępności `M` jest `protected internal`, domena dostępności `M` jest przecięcia domeny ułatwień dostępu `T` tekstu program `P` i pochodnych tekst programu dowolnego typu `T` zadeklarowana poza `P`.  
  
-   Jeśli zadeklarowane dostępności `M` jest `protected`, domena dostępności `M` jest przecięcia domeny ułatwień dostępu `T` tekstu program `T` i dowolny typ pochodny `T`.  
  
-   Jeśli zadeklarowane dostępności `M` jest `internal`, domena dostępności `M` jest przecięcia domeny ułatwień dostępu `T` tekstu program `P`.  
  
-   Jeśli zadeklarowane dostępności `M` jest `private`, domena dostępności `M` jest tekst program `T`.  
  
### <a name="type-names"></a>Nazwy typów  
 Wspólny system typów nakłada tylko dwa ograniczenia dotyczące nazwy:  
  
-   Wszystkie nazwy są kodowane jako ciągi znaków Unicode (16-bitowe).  
  
-   Nazwy są niedozwolone osadzone wartości 0x0000 (16-bitowe).  
  
 Jednak większość języków nałożyć dodatkowe ograniczenia nazwy typu. Wszystkie porównania są wykonywane na podstawie po bicie, a w związku z tym jest rozróżniana wielkość liter i niezależne od ustawień regionalnych.  
  
 Chociaż typu może odwoływać się typy z inne moduły i zestawy, typu musi być całkowicie zdefiniowany w ramach jednego modułu .NET. (W zależności od obsługi kompilatora, jednak ją można podzielić na wiele plików kodu źródłowego.) Nazwy typu musi być unikatowa tylko w obrębie przestrzeni nazw. Aby zidentyfikować pełni typ, nazwa typu musi być kwalifikowana przez obszar nazw, który zawiera implementację tego typu.  
  
### <a name="base-types-and-interfaces"></a>Typy podstawowe i interfejsy  
 Typem może dziedziczyć wartości i zachowania innego typu. Wspólny system typów nie zezwala na typ, który dziedziczy z więcej niż jednego typu podstawowego.  
  
 Typ można zaimplementować dowolną liczbę interfejsów. Aby zaimplementować interfejs, typ musi implementować wirtualnego członków interfejsu. Metoda wirtualna może być zaimplementowany przez typ pochodny i może być wywoływany statycznie lub dynamicznie.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Elementy członkowskie typu  
 Środowisko uruchomieniowe umożliwia definiowanie elementów członkowskich tego typu, który określa zachowania i stan typu. Elementy członkowskie typu są następujące:  
  
-   [Pola](#Fields)  
  
-   [Właściwości](#Properties)  
  
-   [Metody](#Methods)  
  
-   [Konstruktory](#Constructors)  
  
-   [Zdarzenia](#Events)  
  
-   [Zagnieżdżone typy](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pola  
 Pole zawiera opis i zawiera części typu stanu. Pól mogą być dowolnego typu obsługiwane przez środowisko uruchomieniowe. Najczęściej pola są `private` lub `protected`, dzięki czemu są one dostępne tylko z wewnątrz klasy lub z klasy pochodnej. Jeśli wartość pola można modyfikować z poza jego typu, jest zwykle używana metodą dostępu set właściwości. Publicznie ujawnionych pola są zwykle tylko do odczytu i mogą być dwa typy:  
  
-   Stałe, którego wartość jest przypisana w czasie projektowania. Są to statyczne elementy członkowskie klasy, ale ich nie są zdefiniowane przy użyciu `static` (`Shared` w języku Visual Basic) — słowo kluczowe.  
  
-   Zmienne tylko do odczytu, w których wartości można przypisać w konstruktorze klasy.  
  
 Poniższy przykład przedstawia tych dwóch użycia pola tylko do odczytu.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Właściwości  
 Właściwość nazwy wartości lub stan typu i definiuje metody do pobierania lub ustawiania wartości właściwości. Właściwości mogą być typy pierwotne, kolekcje, typy pierwotne, typy danych zdefiniowane przez użytkownika lub kolekcji typów zdefiniowanych przez użytkownika. Właściwości są często używane, aby zapobiec interfejsu publicznego typu niezależne odzwierciedla rzeczywistego typu. Dzięki temu właściwości do wartości, które nie są przechowywane bezpośrednio w klasie (na przykład, gdy właściwość zwraca obliczoną wartość) lub do wykonywania sprawdzania poprawności, zanim przypisywania wartości do pól prywatnych. Poniższy przykład przedstawia ostatnie wzorca.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Oprócz łącznie z samej właściwości Microsoft język pośredni (MSIL) dla typu, który zawiera właściwości do odczytu obejmuje `get_` *propertyname* — metoda i MSIL dla typu, który zawiera zapisu zawiera właściwości `set_` *propertyname* metody.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda opisuje czynności, które są dostępne w typie. Podpis metody Określa dozwolone typy z jego parametrów i zwracanych wartości.  
  
 Mimo że większość metody zdefiniować dokładne liczbę parametrów wymaganych do wywołania metody, w przypadku niektórych metod obsługuje zmienną liczbą parametrów. Ostatni zadeklarowany jako parametr metody jest oznaczony atrybutem <xref:System.ParamArrayAttribute> atrybutu. Kompilatory języka zwykle Podaj słowem kluczowym, takich jak `params` w języku C# i `ParamArray` w języku Visual Basic, który sprawia, że jawnego korzystania z <xref:System.ParamArrayAttribute> niepotrzebne.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktorów  
 Konstruktor jest specjalnym rodzajem metodę, która tworzy nowe wystąpienia klasy lub struktury. Podobnie jak inne metody konstruktora mogą zawierać parametrów; Konstruktory jednak brak wartości zwracanej (oznacza to, że oba operatory zwracają `void`).  
  
 Jeśli kod źródłowy dla klasy nie jawnie definiować konstruktora, kompilator obejmuje domyślnego (bezparametrowego) konstruktora. Jednak jeśli kod źródłowy dla klasy definiuje tylko konstruktory sparametryzowane, Kompilatory języka Visual Basic i C# nie generują konstruktora bez parametrów.  
  
 Jeśli kodu źródłowego dla struktury definiuje konstruktorów, musi być sparametryzowana; struktury nie mogą definiować konstruktora domyślnego (bezparametrowego), a kompilatory nie generują konstruktorów bez parametrów dla struktury lub innych typów wartości. Wszystkie typy wartości ma niejawne domyślnego konstruktora. Ten konstruktor jest implementowany przez środowisko uruchomieniowe języka wspólnego i inicjuje wszystkie pola struktury do wartości domyślnych.  
  
<a name="Events"></a>   
### <a name="events"></a>Zdarzenia  
 Zdarzenie definiuje incydent, który może być odpowiedzi i definiuje metody subskrypcja, anulowanie subskrypcji i wywołaniem zdarzenia. Zdarzenia są często używane do informowania innych typów zmian stanu. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Zagnieżdżone typy  
 Zagnieżdżony typ jest typem, który jest elementem członkowskim innego typu. Zagnieżdżone typy powinien ściśle powiązane do ich typu zawierającego i nie może być przydatne jako typu ogólnego przeznaczenia. Zagnieżdżone typy są przydatne, gdy typ deklarujący używa i tworzy wystąpienia typu zagnieżdżonego i użyj typu zagnieżdżonego nie jest widoczna w publicznych elementów członkowskich.  
  
 Zagnieżdżone typy są trudne do niektórzy deweloperzy i nie powinny być widoczne publicznie, chyba że jest przekonujący powód widoczności. W bibliotece dobrze zaprojektowanego programiści rzadko ma używać zagnieżdżonych typów do utworzenia wystąpienia obiektów lub Zadeklaruj zmienne.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Właściwości elementów członkowskich typu  
 Wspólny system typów umożliwia członkom typu mają różne właściwości; języki nie są wymagane do obsługi tych właściwości. W poniższej tabeli opisano właściwości elementu członkowskiego.  
  
|Cechy|Można zastosować do|Opis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, właściwości i zdarzeń|Typ nie dostarcza implementacji metody. Typy, które dziedziczyć lub implementować metody abstrakcyjne musi dostarczyć implementację metody. Jedynym wyjątkiem jest po typie pochodnym jest typ abstrakcyjny. Wszystkie metody abstrakcyjne są wirtualnego.|  
|prywatne, rodziny, zestawu, rodziny i zestawu, rodziny lub zestawu lub publicznego|Wszystkie|Definiuje dostępność elementu członkowskiego:<br /><br /> private<br /> Dostępne tylko z wewnątrz tego samego typu co element członkowski lub w ramach typu zagnieżdżonego.<br /><br /> Rodziny<br /> Dostępny w obrębie tego samego typu, jako element członkowski i z typów pochodnych, które dziedziczą po niej.<br /><br /> zestaw<br /> Dostępne tylko w zestawie, w którym jest zdefiniowany typ.<br /><br /> rodziny i zestawu<br /> Dostępne tylko z typów, które kwalifikują się do dostępu zarówno rodziny i zestawu.<br /><br /> rodziny lub zestawu<br /> Dostępne tylko z typów, które kwalifikują się do rodziny lub zestawu dostępu.<br /><br /> public<br /> Dostępna z dowolnego typu.|  
|końcowe|Metody, właściwości i zdarzeń|Nie można zastąpić metodę wirtualną w typie pochodnym.|  
|tylko do inicjowania|Pola|Wartość może być inicjowane tylko i nie może zostać zapisany po zainicjowaniu.|  
|Wystąpienie|Pola, metody, właściwości i zdarzeń|Jeśli element członkowski nie jest oznaczona jako `static` (C# i C++), `Shared` (Visual Basic), `virtual` (C# i C++), lub `Overridable` (Visual Basic), jest elementu członkowskiego wystąpienia (Brak słowa kluczowego nie wystąpienie). Będzie tyle kopii takich elementów członkowskich w pamięci są obiekty, które go używają.|  
|literal|Pola|Wartość przypisana do tego pola jest wartością stałą, znane w czasie kompilacji typu wartości wbudowanych. Pola literału są czasami określane jako stałe.|  
|NewSlot lub zastąpienie|Wszystkie|Określa, jak element członkowski współdziała z dziedziczone elementy członkowskie, które mają taką samą sygnaturę:<br /><br /> NewSlot<br /> Ukrywa dziedziczony elementów członkowskich, które mają taką samą sygnaturę.<br /><br /> override<br /> Zastępuje definicji dziedziczonej metody wirtualnej.<br /><br /> Wartość domyślna to newslot.|  
|static|Pola, metody, właściwości i zdarzeń|Element członkowski należy do typu, który jest zdefiniowany, nie do konkretnego wystąpienia typu; element członkowski istnieje, nawet jeśli nie jest tworzone wystąpienie typu i jest udostępniana między wszystkich wystąpień tego typu.|  
|virtual|Metody, właściwości i zdarzeń|Metoda może być zaimplementowany przez typ pochodny i może być wywoływany statycznie lub dynamicznie. Użycie dynamiczne wywołanie typu wystąpienia, który wykonuje wywołanie w czasie wykonywania (a nie typu znane w czasie kompilacji) określa, które implementacji metody jest wywoływana. Aby wywołać metody wirtualnej statycznie, zmienna może być konieczne można rzutować na typ, który korzysta z wersji żądanej metody.|  
  
### <a name="overloading"></a>Przeciążenie  
 Każdy element członkowski typu ma unikatowy podpisu. Podpisy metod zawierają nazwę metody oraz listę parametrów (kolejność i typy argumentów metody). Można zdefiniować wiele metod o tej samej nazwie w określonym typie tak długo, jak ich sygnaturach są różne. Po zdefiniowaniu dwóch lub więcej metod o tej samej nazwie, metoda jest określany przeciążony. Na przykład w <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> metody jest przeciążona. Przyjmuje jedną metodę <xref:System.Char>. Trwa innej metody <xref:System.String> i <xref:System.Int32>.  
  
> [!NOTE]
>  Zwracany typ nie jest uznawany za część podpisu metody. Oznacza to, że nie może zostać przeciążony metody, jeśli różnią się tylko typem zwracanym.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dziedziczenie, zastępowanie i ukrywanie elementów członkowskich  
 Typ pochodny dziedziczy wszystkie elementy członkowskie typu podstawowego; oznacza to, że te elementy członkowskie są zdefiniowane na i dostępne dla typu pochodnego. Można zmodyfikować zachowanie lub właściwości dziedziczone elementy członkowskie na dwa sposoby:  
  
-   Typ pochodny można ukryć dziedziczonego elementu członkowskiego, definiując nowy element członkowski o tej samej sygnaturze. Może to Przekształć w prywatny uprzednio publiczny element członkowski lub zdefiniuj nowe zachowanie dziedziczonej metody, która jest oznaczona jako `final`.  
  
-   Typ pochodny można zastąpić dziedziczonej metody wirtualnej. Metodę zastępującą udostępnia nową definicję metody, która będzie wywoływana na podstawie typu wartości w czasie wykonywania, a nie typu zmienną znane w czasie kompilacji. Metodę można przesłonić metody wirtualnej tylko wtedy, gdy metoda wirtualna nie jest oznaczony jako `final` i nowa metoda jest co najmniej jako dostępne jako metoda wirtualna.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klas programu .NET](http://go.microsoft.com/fwlink/?LinkID=217856)  
 [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md)  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
