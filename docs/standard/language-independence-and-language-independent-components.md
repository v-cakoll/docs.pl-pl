---
title: Niezależność od języka i elementy niezależne od języka
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57934742e378df9bf77938e8c6b3b49cb25e6ecf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647756"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka
Program .NET Framework jest niezależny od języka. Oznacza to, że jako deweloper możesz tworzyć w jednym z wielu języków, których platformą docelową .NET Framework, takich jak C#, C++sposób niezamierzony, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL i Windows PowerShell. Dostępne typy i członków bibliotek klas opracowanych dla programu .NET Framework bez znajomości języka, w którym zostały one pierwotnie napisane i bez konieczności którąkolwiek z Konwencji języka oryginału. Jeśli jesteś deweloperem składnika, dostęp do danego składnika jest możliwy przez dowolną aplikację .NET Framework, niezależnie od języka.  
  
> [!NOTE]
>  To pierwsza część w tym artykule omówiono tworzenie składników niezależnych od języka — czyli składników, które mogą być używane przez aplikacje napisane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego napisanego w wielu językach; zobacz [współdziałanie między językami](#CrossLang) w drugiej części tego artykułu.  
  
 Pełna interakcja z innymi obiektami napisanymi w dowolnym języku, obiekty muszą ujawnić obiektom wywołującym tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest zdefiniowany przez Common Language Specification (CLS), czyli zestaw reguł, które dotyczą generowanych zestawów. Specyfikacja Common Language Specification jest zdefiniowana w partycji I i klauzulach od 7 do 11 [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Jeśli składnik jest zgodny ze specyfikacją języka wspólnego, może być zgodne ze specyfikacją CLS i jest możliwy z kodu w zestawach napisanych w dowolnym języku programowania, który obsługuje specyfikację CLS. Można określić, czy składnika jest zgodny ze specyfikacją języka wspólnego w czasie kompilacji, stosując <xref:System.CLSCompliantAttribute> atrybutu do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute).  
  
 W tym artykule:  
  
- [Reguły zgodności ze specyfikacją CLS](#Rules)  
  
    - [Typy i podpisy typu członka](#Types)  
  
    - [Konwencje nazewnictwa](#naming)  
  
    - [Konwersja typu](#conversion)  
  
    - [Tablice](#arrays)  
  
    - [Interfejsy](#Interfaces)  
  
    - [Wyliczenia](#enums)  
  
    - [Ogólnie rzecz biorąc wpisz członków](#members)  
  
    - [Ułatwienia dostępu członków](#MemberAccess)  
  
    - [Typy ogólne i członkowie](#Generics)  
  
    - [Konstruktory](#ctors)  
  
    - [Właściwości](#properties)  
  
    - [Zdarzenia](#events)  
  
    - [Overloads](#overloads)  
  
    - [Wyjątki](#exceptions)  
  
    - [Atrybuty](#attributes)  
  
- [Atrybut CLSCompliantAttribute](#CLSAttribute)  
  
- [Współdziałanie między językami](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>Reguły zgodności ze specyfikacją CLS  
 W tej sekcji omówiono zasady tworzenia składników zgodnych ze specyfikacją CLS. Aby uzyskać pełną listę reguł, patrz część I, klauzula 11 dokumentu [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
> [!NOTE]
>  Specyfikacja Common Language Specification omawia każdą regułę pod kątem zgodności ze specyfikacją CLS, ma zastosowanie do konsumentów (deweloperzy, którzy programowo uzyskują dostęp do składnika, który jest zgodny ze specyfikacją CLS), struktur (deweloperzy, którzy używają kompilatora języka do utworzenia CLS-compliant biblioteki) i extenderów (deweloperzy, którzy tworzą narzędzia, takie jak kompilator języka lub parser kodu tworzący składniki zgodne ze specyfikacją CLS). W tym artykule koncentruje się na reguły, ponieważ mają one zastosowanie do struktur. Należy zauważyć, że niektóre z reguł, które są stosowane do urządzeń Extender mogą dotyczyć także zestawów, które są tworzone przy użyciu Reflection.Emit.  
  
 Aby zaprojektować składnik, który jest niezależny od języka, wystarczy zastosować reguły zgodności ze specyfikacją CLS interfejsu publicznego danego składnika. Implementacja prywatna nie musi być zgodna ze specyfikacją.  
  
> [!IMPORTANT]
>  Reguły zgodności ze specyfikacją CLS dotyczą tylko publicznego interfejsu składnika, aby nie jego prywatnej implementacji.  
  
 Na przykład niepodpisane liczby całkowite inne niż <xref:System.Byte> nie są zgodne ze specyfikacją CLS. Ponieważ `Person` klasy w poniższym przykładzie ujawnia `Age` właściwości typu <xref:System.UInt16>, poniższy kod wyświetla ostrzeżenie kompilatora.  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 Możesz wprowadzić `Person` klasy zgodne ze specyfikacją CLS, zmieniając typ `Age` właściwość <xref:System.UInt16> do <xref:System.Int16>, który jest zgodny ze specyfikacją CLS, 16-bitowa liczba całkowita ze znakiem. Nie trzeba zmieniać typu prywatnego `personAge` pola.  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 Publiczny interfejs biblioteki składa się z następujących czynności:  
  
- Definicje klas publicznych.  
  
- Definicje publicznych członków klas publicznych oraz definicje członków dostępnych dla klas pochodnych (czyli chronionych elementów członkowskich).  
  
- Parametry i zwracane typy metod publicznych klas publicznych oraz parametry i zwracane typy metod w klasach pochodnych.  
  
 W poniższej tabeli wymieniono reguły zgodności ze specyfikacją CLS. Tekst reguł jest pobierany dosłownie z [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Copyright 2012 by Ecma International. W poniższych sekcjach znajduje się bardziej szczegółowe informacje dotyczące tych zasad.  
  
|Kategoria|Zobacz|Reguła|Numer reguły|  
|--------------|---------|----------|-----------------|  
|Ułatwienia dostępu|[Ułatwienia dostępu członków](#MemberAccess)|Nie powinna być zmieniana dostępność, podczas zastępowania dziedziczonych metod, z wyjątkiem sytuacji, gdy zastępowania metody dziedziczonej z innego zestawu o dostępności `family-or-assembly`. W tym przypadku zastąpienie musi mieć poziom dostępności `family`.|10|  
|Ułatwienia dostępu|[Ułatwienia dostępu członków](#MemberAccess)|Widoczność i dostępność typów i elementów członkowskich jest taka, że typy w podpisie dowolnego elementu członkowskiego są widoczne i dostępne zawsze, gdy sam element członkowski jest widoczny i dostępny. Na przykład metoda publiczna, która jest widoczna spoza jej zestawu nie mają argumentem, którego typ jest widoczny tylko w obrębie zestawu. Widoczność i dostępność typów tworzących typ ogólny z wystąpieniami używany w podpisie dowolnego elementu członkowskiego jest widoczny i dostępny zawsze, gdy sam element członkowski jest widoczny i dostępny. Na przykład skonkretyzowany typ ogólny obecny w podpisie elementu członkowskiego, który jest widoczny na zewnątrz zestawu nie posiada argument rodzajowy, którego typ jest widoczny tylko w obrębie zestawu.|12|  
|Tablice|[Tablice](#arrays)|Tablice powinny zawierać elementy o typie zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy powinny mieć dolne granice równe zero. Tylko fakt, że element jest tablicą i typem elementu tablicy jest wymagany dla rozróżnienia między przeciążeniami. Kiedy przeciążenie opiera się na dwóch lub większej liczbie typów tablicy typy elementu muszą być typami nazwanymi.|16|  
|Atrybuty|[Atrybuty](#attributes)|Atrybuty powinny być typu <xref:System.Attribute?displayProperty=nameWithType>, lub typu z niego dziedziczącego.|41|  
|Atrybuty|[Atrybuty](#attributes)|Specyfikacja CLS zezwala tylko na podzestaw kodowań atrybutów niestandardowych. Jedyne typy, które mają się pojawiać w tych kodowaniach to (zobacz część IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , a każdy typ wyliczeniowy oparty na zgodny ze specyfikacją CLS podstawowym typie integer.|34|  
|Atrybuty|[Atrybuty](#attributes)|Specyfikacja CLS nie zezwala na Modyfikatory widoczne publicznie (`modreq`, zob. partycja II), ale zezwala na Modyfikatory opcjonalne (`modopt`, zob. partycja II) nie rozumie.|35|  
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektu musi wywołać konstruktora pewnego wystąpienia klasy podstawowej zanim nastąpi dostęp do danych wystąpienia dziedziczonego. (To nie dotyczy typów wartości, które nie wymagają konstruktorów.)|21|  
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektu nie będzie wywoływany z wyjątkiem jako część tworzenia obiektu i obiekt nie może być inicjowany dwukrotnie.|22|  
|Wyliczenia|[Wyliczenia](#enums)|Podstawowym typem wyliczenia będzie wbudowany typ liczby całkowitej ze specyfikacją CLS, nazwy pola będzie "value__" i pole to będzie oznakowane `RTSpecialName`.|7|  
|Wyliczenia|[Wyliczenia](#enums)|Istnieją dwa odrębne rodzaje wyliczeń, wskazywane przez obecność lub Brak <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybut niestandardowy (zobacz Biblioteka partycja IV). Reprezentuje nazwane wartości liczb całkowitych; inne reprezentuje nazwane flagi bitowe, które mogą być połączone do generowania wartości nienazwanej. Wartość `enum` nie jest ograniczona do określonej wartości.|8|  
|Wyliczenia|[Wyliczenia](#enums)|Literał statycznego pola elementu enum ma typ wyliczenia Enum.|9|  
|Zdarzenia|[Zdarzenia](#events)|Metody, które implementują zdarzenie to będzie oznakowane `SpecialName` w metadanych.|29|  
|Zdarzenia|[Zdarzenia](#events)|Dostępności zdarzenia i jego metod dostępu muszą być identyczne.|30|  
|Zdarzenia|[Zdarzenia](#events)|`add` i `remove` metody dla zdarzenia muszą być obecne lub nieobecne.|31|  
|Zdarzenia|[Zdarzenia](#events)|`add` i `remove` metody zdarzenia powinny uwzględniać jeden parametr, którego typ definiuje typ zdarzenia i musi pochodzić z <xref:System.Delegate?displayProperty=nameWithType>.|32|  
|Zdarzenia|[Zdarzenia](#events)|Zdarzenia powinny przestrzegać określonego wzorca nazewnictwa. `SpecialName` Atrybut określone w regule CLS 29 będzie ignorowany w odpowiednich porównaniach nazw i będzie stosować się do reguł identyfikatorów.|33|  
|Wyjątki|[Wyjątki](#exceptions)|Obiekty, które są generowane powinny być typu <xref:System.Exception?displayProperty=nameWithType> lub typu z niego dziedziczącego. Niemniej jednak metody ze specyfikacją CLS nie muszą blokować propagacji innych typów wyjątków.|40|  
|Ogólne|[Zgodność ze specyfikacją CLS: zasady](#Rules)|Zasady CLS dotyczą tylko tych części typu, które są dostępne lub widoczne poza zestawem.|1|  
|Ogólne|[Zgodność ze specyfikacją CLS: zasady](#Rules)|Członkowie typów zgodnych ze specyfikacją CLS nie jest oznaczony zgodne ze specyfikacją CLS.|2|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Zagnieżdżone typy muszą mieć przynajmniej tyle parametrów ogólnych, co typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają według pozycji parametrom ogólnym w jego typie otaczającym.|42|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Nazwa typu ogólnego koduje liczbę parametrów typu zadeklarowanej dla typu niezagnieżdżonego, lub nowo wprowadzonego typu, jeśli jest zagnieżdżony, zgodnie z zasadami określonymi powyżej.|43|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Typ ogólny powinien ponownie deklarować ograniczenia wystarczające do zagwarantowania, że wszelkie ograniczenia typu podstawowego lub interfejsów będą spełnione przez ograniczenia typu ogólnego.|4444|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Typy używane jako warunki ograniczające w parametrach ogólnych powinny być zgodne ze specyfikacją CLS.|45|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Widoczność i dostępność elementów członkowskich (w tym typów zagnieżdżonych) w skonkretyzowanym typie ogólnym są uznawane za objętą zakresem konkretyzacji niż deklaracją typu ogólnego jako całości. Tak zakładając, reguły widoczności i dostępności reguły CLS 12 nadal mają zastosowanie.|46|  
|Typy ogólne|[Typy ogólne i członkowie](#Generics)|Dla każdej abstrakcyjnej lub standardowej wirtualnej metody jest domyślna konkretnych (nieabstrakcyjna) implementacja.|47|  
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie wymaga definicji metod zgodne ze specyfikacją CLS w celu ich wdrożenia.|18|  
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie mogą definiować metod statycznych ani nie mogą definiować pól.|19|  
|Elementy członkowskie|[Ogólnie rzecz biorąc wpisz członków](#members)|Globalne statyczne pola i metody nie są zgodne ze specyfikacją CLS.|36|  
|Elementy członkowskie|--|Wartość literału statycznego jest określana za pomocą metadanych inicjowania pola. Zgodne ze specyfikacją CLS literał musi mieć wartość określoną w metadanych inicjalizacji pola, który ma ten sam typ, co literał (lub typu podstawowego, jeśli ten literał jest `enum`).|13|  
|Elementy członkowskie|[Ogólnie rzecz biorąc wpisz członków](#members)|Ograniczenie vararg nie jest częścią specyfikacji CLS, a jedyną Konwencją wywoływania obsługiwaną przez specyfikację CLS jest standardowa zarządzana Konwencja wywoływania.|15|  
|Konwencje nazewnictwa|[Konwencje nazewnictwa](#naming)|Zestawy postępuje zgodnie z załącznikiem 7 z technicznego raportu 15 standardy Unicode Standard3.0 regulującego zestaw znaków do rozpoczynać i znajdować się w identyfikatorach, dostępne online pod <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Identyfikatory powinny być w formacie kanonicznym, zdefiniowane przez formularz normalizacji Unicode C. Ze względów ze specyfikacją CLS dwa identyfikatory są takie same, jeśli ich mapowania na małe litery (określone przez Unicode mapowania na małe litery niewrażliwość na ustawienia regionalne, jeden do jednego) są takie same. Oznacza to, że dwa identyfikatory uważane za różne w ramach CLS są różnią się tylko w ich przypadku. Jednak aby można było przesłonić dziedziczonej definicji interfejsu wiersza polecenia wymaga precyzyjnego kodowania pierwotnej deklaracji.|4|  
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS są różne, niezależnie od rodzaju, z wyjątkiem sytuacji, w których nazwy są identyczne i rozpoznawane przez przeciążenie. Oznacza to podczas gdy specyfikacja CTS zezwala jeden typ używał tej samej nazwy dla metody, pola, specyfikacja CLS nie zezwala.|5|  
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Pola i zagnieżdżone typy powinny wyróżniać się przez porównanie identyfikatorów, mimo że CTS pozwala odróżniać odrębne podpisy. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikatorów), może różnić się więcej niż tylko zwracanym typem, z wyjątkiem określonych w zasadzie 39 CLS.|6|  
|Przeciążenie|[Overloads](#overloads)|Tylko właściwości i metody mogą być przeciążone.|37|  
|Przeciążenie|[Overloads](#overloads)|Właściwości i metody mogą być przeciążone, oparte tylko na liczbie i rodzaju ich parametrów, z wyjątkiem operatorów konwersji o nazwie `op_Implicit` i `op_Explicit`, które również mogą być przeciążone oparciu o ich typ zwrotu.|38|  
|Przeciążenie|--|Jeśli dwa lub więcej metod zgodnych ze specyfikacją CLS zadeklarowane w typie mają taką samą nazwę, dla określonego zestawu wystąpień typu mają ten sam parametr i zwracane typy, następnie wszystkie te metody są semantycznie równoważne w tych wystąpieniach typów.|48|  
|Types|[Typ i podpisy typu członka](#Types)|<xref:System.Object?displayProperty=nameWithType> jest zgodny ze specyfikacją CLS. Inne klasy zgodne ze specyfikacją CLS musi dziedziczyć od zgodne ze specyfikacją CLS klasy.|23|  
|Właściwości|[Właściwości](#properties)|Metody, które implementują metody getter i setter właściwości to będzie oznakowane `SpecialName` w metadanych.|24|  
|Właściwości|[Właściwości](#properties)|Metod dostępu do właściwości musza być statyczne, wirtualne lub być wystąpieniem.|26|  
|Właściwości|[Właściwości](#properties)|Typ właściwości jest zwracany typ metody pobierającej oraz typ ostatniego argumentu metody ustawiającej. Typy parametrów właściwości powinny być typami z parametrami metody pobierającej oraz typami wszystkich parametrów poza ostatnim metody ustawiającej. Wszystkie te typy są zgodne ze specyfikacją CLS i nie może być zarządzanymi wskaźnikami (czyli nie mogą być przekazywane przez odwołanie).|27|  
|Właściwości|[Właściwości](#properties)|Właściwości powinny przestrzegać określonego wzorca nazewnictwa. `SpecialName` Określone w regule CLS 24 atrybut będzie ignorowany w odpowiednich porównaniach nazw i będzie stosować się do reguł identyfikatorów. Właściwość musi posiadać metodę getter i/lub metoda ustawiająca.|28|  
|Konwersja typu|[Konwersja typu](#conversion)|Jeśli `op_Implicit` lub `op_Explicit` zostanie podana, należy zapewnić alternatywny sposób wymuszenia.|39|  
|Types|[Typ i podpisy typu członka](#Types)|Spakowane typy wartości nie są zgodne ze specyfikacją CLS.|3|  
|Types|[Typ i podpisy typu członka](#Types)|Wszystkie typy pojawiające się w podpisie jest zgodny ze specyfikacją CLS. Wszystkie typy tworzące typ ogólny jest zgodny ze specyfikacją CLS.|11|  
|Types|[Typ i podpisy typu członka](#Types)|Wpisane odwołania nie są zgodne ze specyfikacją CLS.|14|  
|Types|[Typ i podpisy typu członka](#Types)|Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS.|17|  
|Types|[Typ i podpisy typu członka](#Types)|Zgodne ze specyfikacją CLS klasy, typy wartości i interfejsy nie wymagają wdrażania członków niezgodnych-ze specyfikacją CLS.|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>Typy i podpisy typu członka  
 <xref:System.Object?displayProperty=nameWithType> Typ jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typów środowiska .NET Framework. Dziedziczenie w .NET Framework jest niejawne (na przykład <xref:System.String> klasa dziedziczy niejawnie z <xref:System.Object> klasy) lub jawny (na przykład <xref:System.Globalization.CultureNotFoundException> klasa dziedziczy jawnie z <xref:System.ArgumentException> klasy, która dziedziczy jawnie <xref:System.SystemException> klasy, która dziedziczy jawnie <xref:System.Exception> klasy). Typ pochodny był zgodny ze specyfikacją CLS jego typ podstawowy również musi być zgodny ze specyfikacją CLS.  
  
 Poniższy kod przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje podstawę `Counter` klasę korzystającą z liczbą całkowitą bez znaku 32-bitowych jako licznika. Ponieważ klasa oferuje funkcje licznika dzięki zawijaniu liczbą całkowitą bez znaku, klasa jest oznaczona jako zgodna ze specyfikacją niezgodne ze specyfikacją. W rezultacie Klasa pochodna, `NonZeroCounter`, również jest zgodny ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 Wszystkie typy, które pojawiają się w podpisach członków, łącznie z typem zwracania metody lub typem właściwości musi być zgodny ze specyfikacją CLS. Dodatkowo dla typów ogólnych:  
  
- Wszystkie typy tworzące typ ogólny muszą być zgodne ze specyfikacją CLS.  
  
- Wszystkie typy używane jako warunki ograniczające w parametrach rodzajowych musi być zgodny ze specyfikacją CLS.  
  
 .NET Framework [wspólny system typów](../../docs/standard/base-types/common-type-system.md) obejmują szereg wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie kodowane w metadanych zestawu. Z tych typów wewnętrznyc typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.  
  
|Typ zgodny ze specyfikacją CLS|Opis|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8-bitowej nieoznaczonej liczby całkowitej|  
|<xref:System.Int16>|16-bitową|  
|<xref:System.Int32>|32-bitową|  
|<xref:System.Int64>|64-bitową|  
|<xref:System.Single>|Wartość zmiennoprzecinkowa o pojedynczej precyzji|  
|<xref:System.Double>|Wartość zmiennoprzecinkowa o podwójnej precyzji|  
|<xref:System.Boolean>|`true` lub `false` typ wartości|  
|<xref:System.Char>|Jednostka zakodowany kodu UTF-16|  
|<xref:System.Decimal>|Liczba dziesiętna non--liczba zmiennoprzecinkowa|  
|<xref:System.IntPtr>|Wskaźnik lub uchwyt rozmiaru zdefiniowanej platformy|  
|<xref:System.String>|Zbiór zero, co najmniej jeden <xref:System.Char> obiektów|  
  
 Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.  
  
|Typ niezgodny|Opis|Alternatywa zgodna ze specyfikacją CLS|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|Typ danych 8-bitową|<xref:System.Int16>|  
|<xref:System.TypedReference>|Wskaźnik do obiektu oraz jego typ obsługi|Brak|  
|<xref:System.UInt16>|16-bitowej nieoznaczonej liczby całkowitej|<xref:System.Int32>|  
|<xref:System.UInt32>|32-bitowej nieoznaczonej liczby całkowitej|<xref:System.Int64>|  
|<xref:System.UInt64>|64-bitowej nieoznaczonej liczby całkowitej|<xref:System.Int64> (możliwe przepełnienie), <xref:System.Numerics.BigInteger>, lub <xref:System.Double>|  
|<xref:System.UIntPtr>|Nieoznaczony wskaźnik lub uchwyt|<xref:System.IntPtr>|  
  
 Biblioteka klas programu .NET Framework lub inne biblioteki klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:  
  
- Spakowane typy wartości. W poniższym przykładzie C# tworzy klasę, która ma właściwość publiczną typu `int*` o nazwie `Value`. Ponieważ `int*` jest typem wartości spakowanej, kompilator oznacza go jako zgodny ze specyfikacją niezgodne ze specyfikacją.  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
- Odwołania typizowane to specjalne konstrukty zawierające odwołanie do obiektu i odwołanie do typu. Wpisane odwołania są reprezentowane w .NET Framework według <xref:System.TypedReference> klasy.  
  
 Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować <xref:System.CLSCompliantAttribute> atrybutem `isCompliant` wartość `false` do niego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute) sekcji.  
  
 Poniższy przykład ilustruje problem zgodności ze specyfikacją CLS w podpisie metody i w tworzeniu wystąpienia typu ogólnego. Definiuje on `InvoiceItem` klasę z właściwością typu <xref:System.UInt32>, właściwość typu `Nullable(Of UInt32)`i konstruktora z parametrami typu <xref:System.UInt32> i `Nullable(Of UInt32)`. Otrzymujemy cztery ostrzeżenia kompilatora podczas próby skompilowania tego przykładu.  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 Aby wyeliminować ostrzeżenia kompilatora, Zamień typy zgodne ze specyfikacją niezgodne ze specyfikacją w `InvoiceItem` interfejsu publicznego zgodnych typów:  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 Oprócz określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Należą do nich typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej do utworzenia tablicy liczb całkowitych.  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 Klasy abstrakcyjne dla zgodne ze specyfikacją CLS (to znaczy klas oznaczonych jako `abstract` w języku C# lub jako `MustInherit` w języku Visual Basic), wszystkie elementy członkowskie klasy, również musi być zgodny ze specyfikacją CLS.  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>Konwencje nazewnictwa  
 Ponieważ w niektórych językach programowania jest rozróżniana wielkość liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i członkowie) muszą różnić się przez więcej niż wielkością liter. Dwa identyfikatory są uważane za równoważne, jeżeli ich mapowania na małe litery są takie same. Poniższy przykład C# definiuje dwie klasy publiczne, `Person` i `person`. Ponieważ różnią się tylko wielkością liter, kompilator języka C# oznacza je jako niezgodne ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 Programowanie identyfikatorów języka, takich jak nazwy przestrzeni nazw, typów i członków, musi być zgodna z [Unicode Standard 3.0, 15 raportów technicznych, załącznika 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:  
  
- Pierwszy znak identyfikatora może być dowolnego Unicode wielką literą, małą literą, literą, literą modyfikatora, inną literą lub znakiem liczby. Aby uzyskać informacji na temat kategorii znaków Unicode, zobacz <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> wyliczenia.  
  
- Kolejne znaki mogą należeć do dowolnej kategorii jako pierwszego znaku i mogą również obejmować nierozdzielające, odstępy, łączenie znaków, liczby dziesiętne, znaki rozdzielające łącznika i kody formatowania.  
  
 Przed porównaniem identyfikatorów, należy odfiltrować kody formatowania i dokonać konwersji identyfikatorów do formularza normalizacji Unicode C, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowane UTF-16. Sekwencje znaków, które generują te same jednostki kodu w formularzu C normalizacji Unicode nie są zgodne ze specyfikacją CLS. Poniższy przykład definiuje właściwość o nazwie `Å`, która składa się ze znaku ANGSTROM SIGN (U + 212B), i drugą właściwość o nazwie `Å`, która składa się ze znaku LATIN CAPITAL LETTER A WITH RING ABOVE (U + 00 C 5). Zarówno C# i Kompilatory języka Visual Basic Flaga kod źródłowy jako zgodny ze specyfikacją niezgodne ze specyfikacją.  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 Nazwy elementów członkowskich z określonego zakresu (np. obszary nazw w zestawie, typy w przestrzeni nazw lub członków w ramach danego typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane przez przeciążenie. Wymóg ten jest bardziej rygorystyczny niż wspólny system typów umożliwia członkom wielu w zakresie miało identyczne nazwy, tak długo, jak są one różnych rodzajów elementów członkowskich (na przykład jeden jest metodą i inny jest polem). W szczególności dla członków typu:  
  
- Pola i zagnieżdżone typy są rozróżniane według nazwy samodzielnie.  
  
- Metody, właściwości i zdarzenia, które mają taką samą nazwę muszą różnić się przez więcej niż tylko zwracanym typem.  
  
 Poniższy przykład ilustruje wymaganie, że nazwy elementów członkowskich musi być unikatowa w obrębie swojego zakresu. Definiuje klasę o nazwie `Converter` zawierającej czterech członków o nazwie `Conversion`. Trzy to metody, a jedna jest właściwością. Metoda, która obejmuje <xref:System.Int64> parametr ma unikatową nazwę, ale dwie metody z <xref:System.Int32> parametru są, ponieważ wartość zwracana nie jest uważany za część podpisu elementu członkowskiego. `Conversion` Właściwości również narusza to wymaganie, ponieważ właściwości nie może mieć taką samą nazwę jak metody przeciążone.  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 Poszczególne języki obejmują unikatowe słowa kluczowe, więc języki przeznaczone środowiska uruchomieniowego języka wspólnego muszą również zapewnić pewien mechanizm dla odwoływania się do identyfikatorów (takich jak nazwy typu), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w językach C# i Visual Basic. Jednak w poniższym przykładzie w języku Visual Basic jest w stanie odróżnić klasę o nazwie `case` z `case` — słowo kluczowe przy użyciu otwierających i zamykających nawiasów klamrowych. W przeciwnym razie przykład komunikat o błędzie, "Słowo kluczowe nie jest prawidłowe jako identyfikator" i kompilacja nie powiedzie się.  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 W poniższym przykładzie C# jest w stanie utworzyć `case` przy użyciu `@` symbolu, aby odróżnić identyfikator od słowa kluczowego języka. Bez tego kompilator języka C# będzie wyświetlane dwa komunikaty o błędach, "Oczekiwano typu" i "wyrażeniu występuje nieprawidłowe określenie"case"."  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>Konwersja typu  
 Specyfikacja Common Language Specification definiuje dwa operatory konwersji:  
  
- `op_Implicit`, który jest wykorzystywany do poszerzenia konwersje, nie powodują utraty danych lub precyzji. Na przykład <xref:System.Decimal> struktura zawiera przeciążony `op_Implicit` operatora, aby konwertować wartości typów całkowitych i <xref:System.Char> wartości <xref:System.Decimal> wartości.  
  
- `op_Explicit`, które są wykorzystywane przy zawężaniu zakresu konwersje, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub dokładności. Na przykład <xref:System.Decimal> struktura zawiera przeciążony `op_Explicit` operatora konwersji <xref:System.Double> i <xref:System.Single> wartości <xref:System.Decimal> i konwertowania <xref:System.Decimal> wartości całkowitych, <xref:System.Double>, <xref:System.Single>, i <xref:System.Char>.  
  
 Jednak nie wszystkie języki obsługują przeciążanie operatora lub definicję niestandardowych operatorów. Jeśli użytkownik chce zaimplementować te operatory konwersji, należy także podać alternatywny sposób wykonania konwersji. Firma Microsoft zaleca, aby zapewnić `From` *Xxx* i `To` *Xxx* metody.  
  
 Poniższy przykład definiuje zgodne ze specyfikacją CLS Konwersje jawne i niejawne. Tworzy `UDouble` klasa, która reprezentuje podpisaną podwójnej precyzji liczby zmiennopozycyjnej. Rozporządzenie to przewiduje niejawną konwersję z `UDouble` do <xref:System.Double> i jawne konwersje z `UDouble` do <xref:System.Single>, <xref:System.Double> do `UDouble`, i <xref:System.Single> do `UDouble`. Umożliwia on również definiowanie `ToDouble` metodę jako alternatywa dla operatora niejawnej konwersji i `ToSingle`, `FromDouble`, i `FromSingle` metody jako alternatywy dla operatora konwersji jawnej.  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>Tablice  
 Tablice zgodne ze specyfikacją CLS są zgodne z następującymi zasadami:  
  
- Wszystkie wymiary tablicy muszą mieć dolną granicę równą zero. Poniższy przykład tworzy tablicę ze specyfikacją CLS niezgodne ze specyfikacją z dolną granicą równą jeden. Należy pamiętać, że, mimo obecności <xref:System.CLSCompliantAttribute> atrybutu, kompilator nie może wykryć czy tablica zwrócona przez `Numbers.GetTenPrimes` metoda nie jest zgodny ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
- Wszystkie elementy tablicy musi składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice zgodne ze specyfikacją niezgodne ze specyfikacją. Pierwsza zwraca tablicę <xref:System.UInt32> wartości. Druga zwraca <xref:System.Object> tablicy, która obejmuje <xref:System.Int32> i <xref:System.UInt32> wartości. Mimo że kompilator identyfikuje pierwszą tablicę jako niezgodną z powodu jego <xref:System.UInt32> typu, nie rozpoznaje, że druga tablica zawiera elementy inne niż zgodne ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
- Rozdzielczość przeciążenia dla metod, które mają parametry tablicy jest opiera się na fakcie, że są to tablice i na ich typie elementu. Z tego powodu następujące definicja przeciążonej `GetSquares` metodą jest zgodny ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Interfejsy  
 Interfejsy zgodne ze specyfikacją CLS można zdefiniować właściwości, zdarzenia i metody wirtualne (metody bez wdrażania). Zgodne ze specyfikacją CLS interfejs nie może zawierać żadnych z następujących czynności:  
  
- Metody statyczne lub pola statyczne. Zarówno C# i Kompilatory języka Visual Basic generują błędy kompilatora, jeśli zdefiniujesz członka statycznego w interfejsie.  
  
- Pola. Zarówno C# i Kompilatory języka Visual Basic generują błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.  
  
- Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu zawiera metodę `INumber.GetUnsigned`, która jest oznaczona jako niezgodna-ze specyfikacją CLS. Ten przykład generuje ostrzeżenie kompilatora.  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     Z powodu działania tej reguły typy zgodne ze specyfikacją CLS nie muszą Implementuj składowe zgodne ze specyfikacją niezgodne ze specyfikacją. Jeśli platforma zgodna ze specyfikacją CLS udostępnia klasę, która implementuje interfejs zgodne ze specyfikacją CLS, powinno dodatkowo dostarczać konkretnych implementacji wszystkich członków innych niż zgodne ze specyfikacją CLS.  
  
 Kompilatory języka zgodne ze specyfikacją CLS muszą również pozwalać, aby klasa zapewniała oddzielne implementacje członków, którzy mają taką samą nazwę i podpis w wielu interfejsach.  Zarówno C# i Visual Basic obsługują [jawne implementacje interfejsu](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) aby zapewnić różne implementacje metod o identycznej nazwie. Visual Basic obsługuje również `Implements` implementuje słowo kluczowe, które umożliwia jawne wyznaczanie interfejsu i członka określonego elementu członkowskiego. Poniższy przykład ilustruje ten scenariusz, definiując `Temperature` klasę, która implementuje `ICelsius` i `IFahrenheit` interfejsów jako jawne implementacje interfejsu.  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenia zgodne ze specyfikacją CLS muszą wykonać następujące czynności:  
  
- Podstawowym typem wyliczenia musi być typu integer zgodnym ze specyfikacją CLS wewnętrzne (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, lub <xref:System.Int64>). Na przykład, poniższy kod próbuje zdefiniować wyliczenie, którego podstawowym typem jest <xref:System.UInt32> i generuje ostrzeżenie kompilatora.  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
- Typ wyliczenia musi posiadać jedno pole wystąpienia o nazwie `Value__` oznaczona za pomocą <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> atrybutu. Dzięki temu można odwoływać się niejawnie do wartości pola.  
  
- Wyliczenie zawiera pola statyczne literału o typach jest zgodny z typem samego wyliczenia. Na przykład, jeśli zdefiniujesz `State` wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` są statycznymi polami literału, którego typem jest `State`.  
  
- Istnieją dwa rodzaje wyliczeń:  
  
    - Wyliczenie, które reprezentuje zestaw wzajemnie się wykluczających, nazwanych wartości całkowitych. Ten typ wyliczenia jest oznaczany przez brak z <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu niestandardowego.  
  
    - Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć do generowania wartości nienazwanej. Ten typ wyliczenia jest oznaczany przez obecność programu <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu niestandardowego.  
  
     Aby uzyskać więcej informacji, zobacz dokumentację dla <xref:System.Enum> struktury.  
  
- Wartość wyliczenia nie jest ograniczona do zakresu jego określonych wartości. Innymi słowy zakres wartości wyliczenia to zakres wartości bazowej. Możesz użyć <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metodę, aby określić, czy określona wartość jest członkiem wyliczenia.  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>Ogólnie rzecz biorąc wpisz członków  
 Specyfikacja Common Language Specification wymaga wszystkich pól i metod, które były dostępne jako elementy członkowskie określonej klasy. Dlatego globalne pola i metody statyczne (czyli pola statyczne lub metody, które są definiowane niezależnie od typu) nie są zgodne ze specyfikacją CLS. Jeśli próbujesz dołączyć globalne pole lub metodę w kodzie źródłowym, kompilatory języków C# i Visual Basic generują błędy kompilatora.  
  
 Specyfikacja Common Language Specification obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje on konwencji wywoływania niezarządzanego i metod ze zmiennym argumentem list oznaczonych `varargs` — słowo kluczowe. W przypadku listy zmiennych argumentów, które są zgodne ze standardową konwencją zarządzanego wywoływania użyj <xref:System.ParamArrayAttribute> atrybutu lub implementacji konkretnego języka, takich jak `params` — słowo kluczowe w języku C# i `ParamArray` — słowo kluczowe w języku Visual Basic.  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>Ułatwienia dostępu członków  
 Zastępowanie dziedziczonego członka nie można zmienić dostępności tego członka. Na przykład publiczną metodę w klasie bazowej nie może być zastąpiona przez prywatną metodę w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku C#) lub `Protected Friend` (w języku Visual Basic) elementu członkowskiego w jednym zestawie, który jest zastępowany przez typ w innym zestawie. W tym przypadku dostępnośc zastąpienia jest `Protected`.  
  
 Poniższy przykład ilustruje błąd, który jest generowany, jeśli <xref:System.CLSCompliantAttribute> ma ustawioną wartość atrybutu `true`, i `Human`, która jest klasą pochodną `Animal`, próbuje zmienić dostępność `Species` właściwość publicznej na prywatną. Przykład pomyślnie wykonuje kompilację po zmianie jego dostępności na publiczną.  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 Typy w podpisie elementu członkowskiego musi być dostępny zawsze, gdy członek jest dostępny. Na przykład oznacza to, że publiczny członek nie może zawierać parametru, którego typ jest prywatny, chroniony lub wewnętrzny. Poniższy przykład ilustruje błąd kompilatora, który występuje, gdy `StringWrapper` konstruktora klasy uwidacznia wewnętrzną `StringOperationType` wartości wyliczenia, która określa, jak powinna być otoczona wartość ciągu.  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>Typy ogólne i członkowie  
 Zagnieżdżone typy zawsze mieć przynajmniej tyle parametrów ogólnych, co ich typ otaczający. Odpowiadają one według pozycji parametrom ogólnym w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.  
  
 Relacja między parametrów typu ogólnego dla typu zawierającego i jego typów zagnieżdżonych może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ rodzajowy `Outer<T>` zawiera dwie klasy zagnieżdżonych, `Inner1A` i `Inner1B<U>`. Wywołania `ToString` metody, która każda klasa dziedziczy <xref:System.Object.ToString%2A?displayProperty=nameWithType>, pokazują, że każda klasa zagnieżdżona zawiera parametry typu klasy zawierającej.  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 Nazwy typów ogólnych zakodowane są w formie *nazwa\`n*, gdzie *nazwa* jest nazwą typu \` jest znak literału, i *n* jest liczbą parametrów zadeklarowanych w typie lub, w przypadku zagnieżdżonych typów rodzajowych liczbę nowo wprowadzonych parametrów typu. To kodowanie nazw typu ogólnego jest przydatne głównie dla deweloperów, którzy używają odbicia do dostępu do typów ogólnych zgodnych ze specyfikacją CLS w bibliotece.  
  
 Jeżeli ograniczenia są stosowane jako ogólnego typu, wszystkie typy używane jako ograniczenia również muszą być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` to znaczy nie zgodne ze specyfikacją CLS i klasę ogólną o nazwie `BaseCollection` której parametr typu musi pochodzić od klasy `BaseClass`. Ale ponieważ `BaseClass` nie jest zgodny ze specyfikacją CLS, kompilator generuje ostrzeżenie.  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 Jeśli typ ogólny jest pochodną ogólnego typu podstawowego, musi redeklarować wszelkie ograniczenia tak, aby mógł zagwarantować, że spełnione są również ograniczenia dotyczące typu podstawowego. W poniższym przykładzie zdefiniowano `Number<T>` reprezentujące dowolnego typu liczbowego. Umożliwia on również definiowanie `FloatingPoint<T>` klasy, która reprezentuje zmiennoprzecinkową wartości. Jednakże, kod źródłowy nie zostanie skompilowany, ponieważ nie ma zastosowania ograniczenia na `Number<T>` (że T musi być typem wartości) do `FloatingPoint<T>`.  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 Przykład pomyślnie wykonuje kompilację ograniczenie zostanie dodane do `FloatingPoint<T>` klasy.  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Specyfikacja Common Language Specification nakłada wystąpienia Konserwatywny model dla typów zagnieżdżonych i chronionych elementów członkowskich. Otwarte typy ogólne nie mogą ujawnić pól ani członków z podpisami, zawierającymi określone podczas tworzenia wystąpienia zagnieżdżonego, chronionego typu ogólnego. Typy nieuniwersalne, rozszerzające możliwości określonego wystąpienia rodzajowego klasy podstawowej lub interfejsu nie mogą ujawnić pól ani członków z podpisami, zawierającymi różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.  
  
 W poniższym przykładzie zdefiniowano typ ogólny, `C1<T>` (lub `C1(Of T)` w języku Visual Basic) i klasę chronioną `C1<T>.N` (lub `C1(Of T).N` w języku Visual Basic). `C1<T>` posiada dwie metody, `M1` i `M2`. Jednak `M1` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` (lub `C1(Of Integer).N`) z typu C1\<T > (lub `C1(Of T)`). Druga klasa `C2`, jest tworzony na podstawie `C1<long>` (lub `C1(Of Long)`). Posiada dwie metody `M3` i `M4`. `M3` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić `C1<int>.N` (lub `C1(Of Integer).N`) obiekt z podklasy `C1<long>`. Należy pamiętać, że Kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic wyświetli błąd przy próbie kompilacji `M4`.  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>Konstruktorów  
 Konstruktory w klasach zgodnych ze specyfikacją CLS i struktury, należy wykonać następujące czynności:  
  
- Konstruktor klasy pochodnej musi wywołać konstruktora wystąpienia klasy podstawowej zanim uzyskuje dostęp do danych wystąpienia dziedziczonego. Ten wymóg jest fakt, że Konstruktory klasy bazowej nie są dziedziczone przez ich klasy pochodne. Ta zasada nie ma zastosowania do struktur, które nie obsługują bezpośredniego dziedziczenia.  
  
     Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności ze specyfikacją CLS, co ilustruje poniższy przykład. Tworzy `Doctor` klasy, która jest pochodną `Person` klasy, ale `Doctor` klasy nie wywoła `Person` Konstruktor klasyinicjuje pola wystąpień.  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
- Nie można wywołać konstruktora obiektu z wyjątkiem tworzenia obiektu. Ponadto nie można zainicjować obiektu dwa razy. Oznacza to, że na przykład <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> i metody deserializacji, takich jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> nie mogą wywoływać konstruktorów.  
  
<a name="properties"></a>   
### <a name="properties"></a>Właściwości  
 Właściwości typów zgodnych ze specyfikacją CLS muszą wykonać następujące czynności:  
  
- Właściwość musi posiadać setter i/lub metody pobierającej. W zestawie są one implementowane jako specjalne metody, co oznacza, że pojawią się one jako odrębne metody (metoda pobierająca o nazwie `get_` *propertyname* i metoda ustawiająca o `set_` *propertyname*) oznaczone jako `SpecialName` w metadanych zestawu. Kompilatory C# i Visual Basic wymuszają tę regułę automatycznie, bez potrzeby stosowania <xref:System.CLSCompliantAttribute> atrybutu.  
  
- Typ właściwości jest zwracany typ metody pobierającej oraz typ ostatniego argumentu metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS i argumentów nie można przypisać do właściwości przez odwołanie (oznacza to, nie mogą być wskaźnikami zarządzanymi).  
  
- Jeśli właściwość jest zarówno metody pobierającą i ustawiającą, obie muszą być wirtualne, statyczne lub wystąpieniami. Kompilatory C# i Visual Basic automatycznie wymuszają tę regułę poprzez ich składnię definicji właściwości.  
  
<a name="events"></a>   
### <a name="events"></a>Zdarzenia  
 Zdarzenie jest definiowane przez nazwę i jej typu. Typ zdarzenia jest delegat, który jest używany do wskazania zdarzenia. Na przykład <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie jest typu <xref:System.ResolveEventHandler>. Oprócz samego zdarzenia trzy metody z nazwami na podstawie nazwy zdarzenia zapewniają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:  
  
- Metoda dodawania programu obsługi zdarzeń o nazwie `add_` *EventName*. Na przykład metoda subskrypcji zdarzeń dla <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> nosi nazwę zdarzeń `add_AssemblyResolve`.  
  
- Metoda usuwania programu obsługi zdarzeń o nazwie `remove_` *EventName*. Na przykład metoda usuwania dla <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> nosi nazwę zdarzeń `remove_AssemblyResolve`.  
  
- Metoda wskazywania, że zdarzenie nastąpiło, o nazwie `raise_` *EventName*.  
  
> [!NOTE]
>  Większość zasad specyfikacji języka wspólnego dotyczących zdarzeń jest implementowanych przez Kompilatory języka i są niewidoczne dla deweloperów składników.  
  
 Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć identyczną dostępność. Wszystkie one muszą również mieć statyczne, wystąpienie, lub wirtualnych. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody dodawania i usuwania muszą być obie obecne lub nieobecne.  
  
 W poniższym przykładzie zdefiniowano klasę zgodne ze specyfikacją CLS, o nazwie `Temperature` która zgłasza `TemperatureChanged` zdarzeń, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. `Temperature` Jawnie definiuje klasę `raise_TemperatureChanged` metodę, tak że można selektywnie wykonywać procedury obsługi zdarzeń.  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Overloads  
 Specyfikacja Common Language Specification nakłada następujące wymagania na przeciążone elementy członkowskie:  
  
- Elementy Członkowskie mogą być przeciążane na podstawie liczby parametrów i typ każdego parametru. Konwencja wywoływania, typ zwracany, Modyfikatory niestandardowe stosowane dla metody lub jej parametrów i tego, czy parametry są przekazywane przez wartość lub przez odwołanie nie są uwzględniane przy rozróżnianiu poszczególnych przeciążeń. Aby uzyskać przykład, zobacz kod dla wymogu, że nazwy muszą być unikatowe w obrębie zakresu w [konwencje nazewnictwa](#naming) sekcji.  
  
- Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.  
  
- Metody ogólne mogą być przeciążane na podstawie liczby ich parametrów ogólnych.  
  
> [!NOTE]
>  `op_Explicit` i `op_Implicit` operatory są wyjątki od reguły, które zwracają wartość nie jest uważana za część podpisu metody w przypadku rozpoznawania przeciążenia. Te dwa operatory mogą być przeciążone dla obu swoich parametrów i ich wartości zwracanej.  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>Wyjątki  
 Obiekty wyjątków muszą pochodzić z <xref:System.Exception?displayProperty=nameWithType> lub z innych typów pochodzących od <xref:System.Exception?displayProperty=nameWithType>. Poniższy przykład ilustruje błąd kompilatora, która powstaje, gdy klasa niestandardowa o nazwie `ErrorClass` służy do obsługi wyjątków.  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 Aby naprawić ten błąd `ErrorClass` musi dziedziczyć klasy <xref:System.Exception?displayProperty=nameWithType>. Ponadto `Message` właściwość musi zostać zastąpiona. Poniższy przykład usuwa te błędy, aby zdefiniować `ErrorClass` klasę, która jest zgodna ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>Atrybuty  
 Zestawy w zestawach.NET Framework, atrybuty niestandardowe zapewniają rozszerzony mechanizm do przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów, takich jak zestawy, typy, elementy członkowskie i parametry metody programowania. Atrybuty niestandardowe muszą pochodzić z <xref:System.Attribute?displayProperty=nameWithType> lub typ pochodzący od <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Poniższy przykład narusza tę regułę. Definiuje on `NumericAttribute` klasę, która nie pochodzi od <xref:System.Attribute?displayProperty=nameWithType>. Należy zauważyć, że błąd kompilatora powstaje tylko kiedy innych niż zgodne ze specyfikacją CLS jest stosowany, nie wtedy, gdy klasa jest zdefiniowana.  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 Konstruktor lub właściwości atrybutu zgodne ze specyfikacją CLS mogą uwidaczniać tylko następujące typy:  
  
- <xref:System.Boolean>  
  
- <xref:System.Byte>  
  
- <xref:System.Char>  
  
- <xref:System.Double>  
  
- <xref:System.Int16>  
  
- <xref:System.Int32>  
  
- <xref:System.Int64>  
  
- <xref:System.Single>  
  
- <xref:System.String>  
  
- <xref:System.Type>  
  
- Każdy typ wyliczenia o typie podstawowym <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, lub <xref:System.Int64>.  
  
 W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasę pochodzącą od <xref:System.Attribute>. Konstruktor klasy ma parametr typu `Descriptor`, więc klasa nie jest zgodny ze specyfikacją CLS. Należy pamiętać, że kompilator języka C# emituje ostrzeżenie, ale kompiluje pomyślnie, a kompilator Visual Basic nie emituje ostrzeżenia ani błędu.  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliantAttribute  
 <xref:System.CLSCompliantAttribute> Atrybut jest używany do wskazania, czy element programu jest zgodny z Common Language Specification. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Konstruktora zawiera jeden parametr wymagany `isCompliant`, która wskazuje, czy element programu jest zgodne ze specyfikacją CLS.  
  
 W czasie kompilacji kompilator wykrywa niezgodne elementy, które jest uważana za zgodny ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie generuje ostrzeżeń dotyczących typów ani elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.  
  
 Deweloperzy składników mogą użyć <xref:System.CLSCompliantAttribute> atrybutu na dwa sposoby:  
  
- Aby zdefiniować części interfejsu publicznego udostępnianego przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. Jeśli ten atrybut jest używany do oznaczania elementów konkretnego programu jako zgodne ze specyfikacją CLS, posługiwanie się nim gwarantuje, że te elementy są dostępne we wszystkich językach i narzędzia, które obsługują program .NET Framework.  
  
- Aby upewnić się, że interfejs publiczny biblioteki składników udostępnia tylko te elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zasadniczo generują ostrzeżenie.  
  
> [!WARNING]
>  W niektórych przypadkach Kompilatory języka wymuszają reguły zgodne ze specyfikacją CLS, niezależnie od tego, czy <xref:System.CLSCompliantAttribute> atrybut jest używany. Na przykład określenie członka statycznego w interfejsie narusza regułę specyfikacji CLS. W odniesieniu do tego, jeśli zdefiniujesz `static` (w języku C#) lub `Shared` (w języku Visual Basic) elementu członkowskiego w interfejsie, zarówno Kompilatory języka C# i Visual Basic wyświetlony komunikat o błędzie i nie skompilują aplikacji.  
  
 <xref:System.CLSCompliantAttribute> Atrybut jest oznaczony za pomocą <xref:System.AttributeUsageAttribute> atrybut, który ma wartość <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Ta wartość umożliwia zastosowanie <xref:System.CLSCompliantAttribute> atrybutu do dowolnego elementu programu, w tym zestawy, moduły, elementy członkowskie (konstruktorów, metod, właściwości, pola i zdarzenia), typu typami (klasy, struktury, wyliczenia, interfejsy i delegaci), Parametry, ogólne parametry i wartości zwracane. Jednak w praktyce powinien zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i generowanie ostrzeżenia kompilatora, ilekroć mogą wystąpić niezgodny parametr, parametr ogólny, lub zwrócą wartość w swojej bibliotece interfejsu publicznego w dalszym ciągu.  
  
 Wartość <xref:System.CLSCompliantAttribute> atrybutu jest dziedziczona przez zawarte elementy programu. Na przykład, jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.  
  
 Można wyraźnie przezwyciężyć posiadaną podatność przez zastosowanie <xref:System.CLSCompliantAttribute> atrybutu to zawartego elementu programu. Na przykład, można użyć <xref:System.CLSCompliantAttribute> atrybutem `isCompliant` wartość `false` do zdefiniowania niezgodnego typu w zgodnym zestawie, a, można użyć atrybutu z `isCompliant` wartość `true` do zdefiniowania zgodnego typu w zestawie niezgodnym. Można także zdefiniować niezgodnych członków w zgodnym typie. Jednak niezgodnego typu nie może mieć zgodnych członków, więc nie można użyć atrybutu z `isCompliant` wartość `true` Aby zastąpić dziedziczenie z niezgodnego typu.  
  
 Opracowując składniki, należy zawsze używać <xref:System.CLSCompliantAttribute> atrybutu, aby wskazać, czy zestaw, jego typy i jego członkowie są zgodne ze specyfikacją CLS.  
  
 Aby utworzyć składniki zgodne ze specyfikacją CLS:  
  
1. Użyj <xref:System.CLSCompliantAttribute> aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.  
  
2. Oznacz zgodni typów w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.  
  
3. Umożliwia oznaczenie wszystkich członków publicznie narażonych w typach zgodnych ze specyfikacją CLS jako niezgodne.  
  
4. Zapewniają zgodne ze specyfikacją CLS alternatywę dla członków innych niż zgodne ze specyfikacją CLS.  
  
 Jeśli już pomyślnie oznaczone wszystkie niezgodne typy i elementy członkowskie, kompilator nie powinien emitować żadnych ostrzeżeń o braku zgodności. Jednakże należy wskazać składniki, które nie są zgodne ze specyfikacją CLS i wyświetlić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.  
  
 W poniższym przykładzie użyto <xref:System.CLSCompliantAttribute> atrybut do definiowania zgodne ze specyfikacją CLS zestawu i typu `CharacterUtilities`, która ma dwie składowe zgodne ze specyfikacją niezgodne ze specyfikacją. Ponieważ obaj członkowie są oznaczeni `CLSCompliant(false)` atrybutu, kompilator nie generuje ostrzeżeń. Ta klasa oferuje również zgodne ze specyfikacją CLS alternatywę dla obu metod. Zwykle, możemy po prostu dodać dwa przeciążenia do `ToUTF16` metody w celu zapewnienia alternatywy zgodnej ze specyfikacją CLS. Jednakże ponieważ nie można obciążać metod na podstawie wartości zwracanej, nazwy metod zgodne ze specyfikacją CLS różnią się od nazw metod niezgodnych.  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 Jeśli tworzysz aplikację, a nie bibliotekę (to znaczy, jeśli nie udostępniasz typów lub elementów członkowskich, które mogą być wykorzystane przez innych programistów aplikacji), zgodność ze specyfikacją CLS elementów programu, z których korzysta aplikacja mogą być przydatne tylko wtedy, gdy język ich nie obsługuje . W takim przypadku Twój kompilator języka wygeneruje błąd podczas próby użycia elementu innego niż zgodne ze specyfikacją CLS.  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>Współdziałanie między językami  
 Niezależność od języka ma wiele znaczeń. Znaczenie jedną, co zostało omówione w artykule [niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md), polega na bezproblemowe korzystanie z typów napisane w jednym języku z aplikacji napisanych w innym języku. Drugi znaczenia, czyli ten artykuł koncentruje się polega na połączeniu kodu napisanego w wielu językach, w ramach pojedynczego zestawu .NET Framework.  
  
 W poniższym przykładzie pokazano współdziałanie między językami, tworząc bibliotekę klas o nazwie Utilities.dll, który zawiera dwie klasy `NumericLib` i `StringLib`. `NumericLib` Klasy został napisany w języku C# i `StringLib` klasy został napisany w języku Visual Basic. Poniżej przedstawiono kod źródłowy StringUtil.vb, który zawiera jeden element członkowski, `ToTitleCase`w jego `StringLib` klasy.  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 Poniżej przedstawiono kod źródłowy NumberUtil.cs, który definiuje `NumericLib` klasy, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 Aby spakować dwóch klas w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego języka Visual Basic w module, użyj tego polecenia:  
  
```console  
vbc /t:module StringUtil.vb   
```  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora języka Visual Basic, zobacz [tworzenie z wiersza polecenia](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
 Aby skompilować plik kodu źródłowego języka C# w module, użyj tego polecenia:  
  
```console  
csc /t:module NumberUtil.cs  
```  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora C#, zobacz [wiersza polecenia tworzenia przy użyciu csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
 Następnie użyj [opcje konsolidatora](/cpp/build/reference/linker-options) skompilować dwa moduły do zestawu:  
  
```console  
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll   
```  
  
 Poniższy przykład następnie wywołuje `NumericLib.NearZero` i `StringLib.ToTitleCase` metody. Należy pamiętać, że zarówno kod języka Visual Basic, jak i kodu C# mają dostęp do metod w obu klasach.  
  
 [!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
 [!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]  
  
 Aby skompilować kod w języku Visual Basic, użyj tego polecenia:  
  
```console  
vbc example.vb /r:UtilityLib.dll  
```  
  
 Aby skompilować przy użyciu języka C#, Zmień nazwę kompilator **vbc** do **csc**i zmień rozszerzenie pliku z .vb CS:  
  
```console  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.CLSCompliantAttribute>
