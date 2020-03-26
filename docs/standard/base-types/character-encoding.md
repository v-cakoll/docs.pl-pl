---
title: Jak używać klas kodowania znaków w .NET
description: Dowiedz się, jak używać klas kodowania znaków w .NET.
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
ms.openlocfilehash: 063cac1de6634125d7dabad9d627bceff877e567
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546740"
---
# <a name="how-to-use-character-encoding-classes-in-net"></a>Jak używać klas kodowania znaków w .NET

W tym artykule wyjaśniono, jak używać klas, które .NET zapewnia kodowania i dekodowania tekstu przy użyciu różnych schematów kodowania. Instrukcje zakładają, że przeczytałeś [Wprowadzenie do kodowania znaków w .NET](character-encoding-introduction.md).

## <a name="encoders-and-decoders"></a>Kodery i dekodery

.NET udostępnia klasy kodowania, które kodują i dekodują tekst przy użyciu różnych systemów kodowania. Na przykład <xref:System.Text.UTF8Encoding> klasa opisuje reguły kodowania i dekodowania z UTF-8. .NET używa kodowania UTF-16 (reprezentowane <xref:System.Text.UnicodeEncoding> przez `string` klasę) dla wystąpień. Kodery i dekodery są dostępne dla innych schematów kodowania.

Kodowanie i dekodowanie może również obejmować sprawdzanie poprawności. Na przykład <xref:System.Text.UnicodeEncoding> klasa sprawdza `char` wszystkie wystąpienia w zakresie zastępczym, aby upewnić się, że są one w prawidłowych par zastępczych. Strategia rezerwowa określa, jak koder obsługuje nieprawidłowe znaki lub jak dekoder obsługuje nieprawidłowe bajty.

> [!WARNING]
> Klasy kodowania platformy .NET umożliwiają przechowywanie i konwertowanie danych znaków. Nie powinny one być używane do przechowywania danych binarnych w postaci ciągu. W zależności od używanego kodowania konwertowanie danych binarnych na format ciągu z klasami kodowania może wprowadzać nieoczekiwane zachowanie i powodować niedokładne lub uszkodzone dane. Aby przekonwertować dane binarne do formularza ciągu, należy użyć <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metody.

Wszystkie klasy kodowania znaków w <xref:System.Text.Encoding?displayProperty=nameWithType> .NET dziedziczą z klasy, która jest klasą abstrakcyjną, która definiuje funkcje wspólne dla wszystkich kodowania znaków. Aby uzyskać dostęp do poszczególnych obiektów kodowania zaimplementowanych w programie .NET, wykonaj następujące czynności:

- Użyj właściwości statycznych <xref:System.Text.Encoding> klasy, które zwracają obiekty reprezentujące standardowe kodowanie znaków dostępne w .NET (ASCII, UTF-7, UTF-8, UTF-16 i UTF-32). Na przykład <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> właściwość <xref:System.Text.UnicodeEncoding> zwraca obiekt. Każdy obiekt używa zastępczego powrotu do obsługi ciągów, których nie może zakodować i bajtów, których nie można zdekodować. Aby uzyskać więcej informacji, zobacz [Wymiana rezerwowa](../../../docs/standard/base-types/character-encoding.md#Replacement).

- Wywołanie konstruktora klasy kodowania. W ten sposób można utworzyć wystąpienia obiektów kodowania ASCII, UTF-7, UTF-8, UTF-16 i UTF-32. Domyślnie każdy obiekt używa zastępczego powrotu do obsługi ciągów, których nie można zakodować i bajtów, których nie można zdekodować, ale można określić, że zamiast tego powinien zostać zgłoszony wyjątek. Aby uzyskać więcej informacji, zobacz [Rezerwa zastępcza](../../../docs/standard/base-types/character-encoding.md#Replacement) i [Rezerwa wyjątków](../../../docs/standard/base-types/character-encoding.md#Exception).

- Wywołaj <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> konstruktora i przekaż go całkowitej liczby, która reprezentuje kodowania. Standardowe obiekty kodowania używają zastępczego rezerwowego, a strony kodującej i dwubajtowego zestawu znaków (DBCS) używają najlepiej dopasowanych rezerwowych do obsługi ciągów, których nie mogą zakodować, i bajtów, których nie mogą zdekodować. Aby uzyskać więcej informacji, zobacz [Najlepiej dopasowany rezerwowy](../../../docs/standard/base-types/character-encoding.md#BestFit).

- Wywołanie <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metody, która zwraca dowolny standard, strona kodowa lub kodowanie DBCS dostępne w .NET. Przeciążenia umożliwiają określenie obiektu rezerwowego zarówno dla kodera, jak i dekodera.

Można pobrać informacje o wszystkich kodowania dostępnych w .NET, wywołując <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metodę. Program .NET obsługuje schematy kodowania znaków wymienione w poniższej tabeli.

|Klasa kodowania|Opis|
|--------------|-----------|
|[Ascii](xref:System.Text.ASCIIEncoding)|Koduje ograniczony zakres znaków przy użyciu dolnej siedem bitów bajtu. Ponieważ to kodowanie obsługuje tylko wartości znaków od U + 0000 do U + 007F, w większości przypadków jest nieodpowiednie dla aplikacji internacjonalizacji.|
|[UTF-7](xref:System.Text.UTF7Encoding)|Reprezentuje znaki jako sekwencje 7-bitowych znaków ASCII. Znaki Non-ASCII Unicode są reprezentowane przez sekwencję unikową znaków ASCII. UTF-7 obsługuje protokoły, takie jak poczta e-mail i grupa dyskusyjna. Jednak UTF-7 nie jest szczególnie bezpieczne lub solidne. W niektórych przypadkach zmiana jednego bitu może radykalnie zmienić interpretację całego ciągu UTF-7. W innych przypadkach różne ciągi UTF-7 można zakodować ten sam tekst. W przypadku sekwencji, które zawierają znaki inne niż ASCII, UTF-7 wymaga więcej miejsca niż UTF-8, a kodowanie/dekodowanie jest wolniejsze. W związku z tym należy użyć UTF-8 zamiast UTF-7, jeśli to możliwe.|
|[UTF-8](xref:System.Text.UTF8Encoding)|Reprezentuje każdy punkt kodu Unicode jako sekwencję od jednego do czterech bajtów. UTF-8 obsługuje 8-bitowe rozmiary danych i działa dobrze z wieloma istniejącymi systemami operacyjnymi. W przypadku zakresu znaków ASCII UTF-8 jest identyczny z kodowaniem ASCII i umożliwia szerszy zestaw znaków. Jednak dla skryptów chińsko-japońsko-koreańskich (CJK) UTF-8 może wymagać trzech bajtów dla każdego znaku i może powodować większe rozmiary danych niż UTF-16. Czasami ilość danych ASCII, takich jak tagi HTML, uzasadnia zwiększony rozmiar dla zakresu CJK.|
|[UTF-16](xref:System.Text.UnicodeEncoding)|Reprezentuje każdy punkt kodu Unicode jako sekwencję jednej lub dwóch 16-bitowych liczby całkowitej. Najczęściej znaki Unicode wymagają tylko jednego punktu kodu UTF-16, chociaż dodatkowe znaki Unicode (U + 10000 i większe) wymagają dwóch punktów kodu zastępczego UTF-16. Obsługiwane są zarówno małe, jak i duże endianowe rozkazy bajtów. Kodowanie UTF-16 jest używane przez środowisko <xref:System.Char> wykonawcze języka wspólnego do reprezentowania i <xref:System.String> `WCHAR` wartości i jest używane przez system operacyjny Windows do reprezentowania wartości.|
|[UTF-32](xref:System.Text.UTF32Encoding)|Reprezentuje każdy punkt kodu Unicode jako 32-bitową liczbę całkowitą. Obsługiwane są zarówno małe, jak i duże endianowe rozkazy bajtów. Kodowanie UTF-32 jest używane, gdy aplikacje chcą uniknąć zachowania punktu kodu zastępczego kodowania UTF-16 w systemach operacyjnych, dla których zakodowana przestrzeń jest zbyt ważna. Pojedyncze glify renderowane na wyświetlaczu mogą być nadal kodowane więcej niż jednym znakiem UTF-32.|
|Kodowanie ANSI/ISO|Zapewnia obsługę różnych stron kodowych. W systemach operacyjnych Windows strony kodowe są używane do obsługi określonego języka lub grupy języków. Dla tabeli, która zawiera listę stron kodowych <xref:System.Text.Encoding> obsługiwanych przez .NET, zobacz klasy. Obiekt kodowania dla określonej strony kodowej można <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> pobrać, wywołując metodę. Strona kodowa zawiera 256 punktów kodu i jest oparta na wartości zero. Na większości stron kodowych punkty kodowe od 0 do 127 reprezentują zestaw znaków ASCII, a punkty kodowe od 128 do 255 różnią się znacznie między stronami kodowymi. Na przykład strona kodowa 1252 zawiera znaki dla systemów pisania łacińskiego, w tym angielski, niemiecki i francuski. Ostatnie 128 punktów kodu na stronie kodowej 1252 zawiera znaki akcentu. Strona kodowa 1253 zawiera kody znaków, które są wymagane w greckim systemie pisania. Ostatnie 128 punktów kodu na stronie kodowej 1253 zawiera znaki greckie. W rezultacie aplikacja, która opiera się na stronach kodowych ANSI nie może przechowywać języka greckiego i niemieckiego w tym samym strumieniu tekstowym, chyba że zawiera identyfikator, który wskazuje stronę kodową, do której istnieje odwołanie.|
|Kodowanie dwu bajtowego zestawu znaków (DBCS)|Obsługuje języki, takie jak chiński, japoński i koreański, które zawierają więcej niż 256 znaków. W DBCS para punktów kodu (podwójny bajt) reprezentuje każdy znak. Właściwość <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> `false` zwraca kodowania DBCS. Obiekt kodowania dla określonego formatu DBCS można <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> pobrać, wywołując metodę. Gdy aplikacja obsługuje dane DBCS, pierwszy bajt znaku DBCS (bajt ołowiu) jest przetwarzany w połączeniu z bajtem szlaku, który bezpośrednio następuje po nim. Ponieważ pojedyncza para punktów kodu dwu bajtów może reprezentować różne znaki w zależności od strony kodowej, ten schemat nadal nie zezwala na kombinację dwóch języków, takich jak japoński i chiński, w tym samym strumieniu danych.|

Kodowania te umożliwiają pracę ze znakami Unicode, a także z kodowania, które są najczęściej używane w starszych aplikacjach. Ponadto można utworzyć kodowanie niestandardowe, definiując klasę, <xref:System.Text.Encoding> która pochodzi od i zastąpienie jej elementów członkowskich.

## <a name="net-core-encoding-support"></a>Obsługa kodowania .NET Core

Domyślnie program .NET Core nie udostępnia żadnych kodowania stron kodowych innych niż strona kodowa 28591 i kodowania Unicode, takich jak UTF-8 i UTF-16. Można jednak dodać kodowanie stron kodowych znalezione w standardowych aplikacjach systemu Windows kierowanych do aplikacji .NET. Aby uzyskać więcej <xref:System.Text.CodePagesEncodingProvider> informacji, zobacz temat.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Wybieranie klasy kodowania

Jeśli masz możliwość wyboru kodowania, które ma być używane przez aplikację, należy użyć kodowania Unicode, najlepiej albo <xref:System.Text.UTF8Encoding> lub <xref:System.Text.UnicodeEncoding>. (.NET obsługuje również trzecie kodowanie <xref:System.Text.UTF32Encoding>Unicode, .)

Jeśli planujesz użyć kodowania ASCII<xref:System.Text.ASCIIEncoding>( <xref:System.Text.UTF8Encoding> ), wybierz zamiast tego. Dwa kodowania są identyczne dla zestawu znaków <xref:System.Text.UTF8Encoding> ASCII, ale ma następujące zalety:

- Może reprezentować każdy znak Unicode, podczas gdy <xref:System.Text.ASCIIEncoding> obsługuje tylko wartości znaków Unicode między U + 0000 i U + 007F.

- Zapewnia wykrywanie błędów i lepsze bezpieczeństwo.

- Został dostrojony tak szybko, jak to możliwe i powinien być szybszy niż jakiekolwiek inne kodowanie. Nawet w przypadku zawartości, która jest całkowicie <xref:System.Text.UTF8Encoding> ASCII, <xref:System.Text.ASCIIEncoding>operacje wykonywane z są szybsze niż operacje wykonywane za pomocą .

Należy rozważyć <xref:System.Text.ASCIIEncoding> użycie tylko dla starszych aplikacji. Jednak nawet w przypadku <xref:System.Text.UTF8Encoding> starszych aplikacji może być lepszym wyborem z następujących powodów (przy założeniu ustawień domyślnych):

- Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go z <xref:System.Text.ASCIIEncoding>, każdy znak nie-ASCII koduje jako znak zapytania (?). Jeśli aplikacja następnie dekoduje te dane, informacje są tracone.

- Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go z, <xref:System.Text.UTF8Encoding>wynik wydaje się niezrozumiały, jeśli jest interpretowany jako ASCII. Jednak jeśli aplikacja następnie używa dekodera UTF-8 do dekodowania tych danych, dane wykonuje podróż w obie strony pomyślnie.

W aplikacji sieci web znaki wysyłane do klienta w odpowiedzi na żądanie sieci web powinny odzwierciedlać kodowanie używane na kliencie. W większości przypadków należy <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> ustawić właściwość na <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> wartość zwróconą przez właściwość, aby wyświetlić tekst w kodowaniu, którego oczekuje użytkownik.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Korzystanie z obiektu kodowania

Koder konwertuje ciąg znaków (najczęściej znaki Unicode) na jego ekwiwalent numeryczny (bajt). Na przykład można użyć kodera ASCII do konwersji znaków Unicode do ASCII, tak aby mogły być wyświetlane na konsoli. Aby wykonać konwersję, <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> należy wywołać metodę. Jeśli chcesz określić, ile bajtów są potrzebne do przechowywania zakodowanych znaków <xref:System.Text.Encoding.GetByteCount%2A> przed wykonaniem kodowania, można wywołać metodę.

W poniższym przykładzie użyto tablicy pojedynczego bajtów do kodowania ciągów w dwóch oddzielnych operacjach. Utrzymuje indeks, który wskazuje pozycję początkową w tablicy bajtów dla następnego zestawu bajtów zakodowanych w ASCII. Wywołuje metodę, <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> aby upewnić się, że tablica bajtów jest wystarczająco duży, aby pomieścić zakodowany ciąg. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodę do kodowania znaków w ciągu.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekoder konwertuje tablicę bajtów, która odzwierciedla kodowanie określonego znaku na zestaw znaków, w tablicy znaków lub w ciągu. Aby zdekodować tablicę bajtów <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> do tablicy znaków, należy wywołać metodę. Aby zdekodować tablicę bajtów <xref:System.Text.Encoding.GetString%2A> do ciągu, należy wywołać metodę. Jeśli chcesz określić, ile znaków są potrzebne do przechowywania zdekodowanych bajtów przed wykonaniem dekodowania, można wywołać <xref:System.Text.Encoding.GetCharCount%2A> metodę.

Poniższy przykład koduje trzy ciągi, a następnie dekoduje je do jednej tablicy znaków. Utrzymuje indeks, który wskazuje pozycję początkową w tablicy znaków dla następnego zestawu zdekodowanych znaków. Wywołuje metodę, <xref:System.Text.ASCIIEncoding.GetCharCount%2A> aby upewnić się, że tablica znaków jest wystarczająco duża, aby pomieścić wszystkie zdekodowane znaki. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodę do dekodowania tablicy bajtów.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kodowania i dekodowania klasy <xref:System.Text.Encoding> pochodzące z są przeznaczone do pracy na kompletny zestaw danych; oznacza to, że wszystkie dane, które mają być zakodowane lub zdekodowane, są dostarczane w wywołaniu pojedynczej metody. Jednak w niektórych przypadkach dane są dostępne w strumieniu, a dane, które mają być zakodowane lub zdekodowane, mogą być dostępne tylko z oddzielnych operacji odczytu. Wymaga to operacji kodowania lub dekodowania, aby zapamiętać dowolny zapisany stan z poprzedniego wywołania. Metody klas pochodzących <xref:System.Text.Encoder> <xref:System.Text.Decoder> z i są w stanie obsługiwać kodowania i dekodowania operacji, które obejmują wiele wywołań metody.

Obiekt <xref:System.Text.Encoder> dla określonego kodowania jest dostępny z <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> właściwości tego kodowania. Obiekt <xref:System.Text.Decoder> dla określonego kodowania jest dostępny z <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> właściwości tego kodowania. W przypadku operacji dekodowania <xref:System.Text.Decoder> należy <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> zauważyć, że klasy pochodzące z obejmują <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>metodę, ale nie mają metody, która odpowiada .

Poniższy przykład ilustruje różnicę <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> między przy użyciu i metody dekodowania tablicy bajtów Unicode. Przykład koduje ciąg, który zawiera niektóre znaki Unicode do pliku, a następnie używa dwóch metod dekodowania do dekodowania ich dziesięć bajtów naraz. Ponieważ para zastępcza występuje w dziesiątym i jedenastym bajtach, jest dekodowana w wywołaniach oddzielnej metody. Jak pokazuje dane <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> wyjściowe, metoda nie jest w stanie poprawnie dekodować bajtów i zamiast tego zastępuje je U + FFFD (ZNAK ZASTĘPCZY). Z drugiej strony <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda jest w stanie pomyślnie dekodować tablicy bajtów, aby uzyskać oryginalny ciąg.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Wybór strategii awaryjnej

Gdy metoda próbuje zakodować lub dekodować znak, ale nie istnieje mapowanie, należy zaimplementować strategii rezerwowej, która określa, jak nie powiodło się mapowanie powinny być obsługiwane. Istnieją trzy rodzaje strategii rezerwowych:

- Najlepiej dopasowany rezerwowy

- Wymiana rezerwy

- Rezerwa wyjątku

> [!IMPORTANT]
> Najczęstsze problemy w operacjach kodowania występują, gdy znak Unicode nie może być mapowany na kodowanie określonej strony kodowania. Najczęstsze problemy w operacjach dekodowania występują, gdy nieprawidłowe sekwencje bajtów nie mogą być przetłumaczone na prawidłowe znaki Unicode. Z tych powodów należy wiedzieć, która strategia rezerwowa używa określonego obiektu kodowania. Jeśli to możliwe, należy określić strategii rezerwowej używane przez obiekt kodowania podczas tworzenia wystąpienia obiektu.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Najlepiej dopasowany rezerwowy

Gdy znak nie ma dokładnego dopasowania w kodowaniu docelowym, koder może spróbować zamapować go na podobny znak. (Najlepiej dopasowany rezerwowy jest głównie kodowania, a nie problem dekodowania. Istnieje bardzo niewiele stron kodowych, które zawierają znaki, których nie można pomyślnie zamapować na Unicode.) Najlepiej dopasowany rezerwowy jest domyślnym dla strony kodowania i dwubajtowych <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> zestaw <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> znaków, które są pobierane przez i przeciążenia.

> [!NOTE]
> Teoretycznie klasy kodowania Unicode dostępne w<xref:System.Text.UTF8Encoding> <xref:System.Text.UnicodeEncoding>.NET <xref:System.Text.UTF32Encoding>( , i ) obsługują każdy znak w każdym zestawie znaków, dzięki czemu mogą być używane do eliminowania problemów rezerwowych najlepiej dopasowanych.

Strategie najlepszego dopasowania różnią się w zależności od strony kodowej. Na przykład w przypadku niektórych stron kodowych znaki łacińskie o pełnej szerokości są mapowane na bardziej typowe znaki łacińskie o połówkowej szerokości. W przypadku innych stron kodowych to mapowanie nie jest wykonane. Nawet w agresywnej strategii najlepiej dopasowane, nie można sobie wyobrazić pasuje do niektórych znaków w niektórych kodowania. Na przykład chiński ideograf nie ma rozsądnego mapowania do strony kodowej 1252. W takim przypadku używany jest ciąg zastępczy. Domyślnie ten ciąg jest tylko jeden znak ZAPYTANIA (U + 003F).

> [!NOTE]
> Strategie najlepszego dopasowania nie są szczegółowo udokumentowane. Jednak kilka stron kodowych są udokumentowane na stronie internetowej [konsorcjum Unicode.](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) Zapoznaj się z plikiem **readme.txt** w tym folderze, aby uzyskać opis interpretacji plików mapowania.

W poniższym przykładzie użyto strony kodowej 1252 (strony kodowej systemu Windows dla języków Zachodnioeuropejskich), aby zilustrować najlepsze dopasowanie mapowania i jego wady. Metoda <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> służy do pobierania obiektu kodowania dla strony kodowej 1252. Domyślnie używa mapowania najlepiej dopasowanych dla znaków Unicode, które nie obsługuje. W przykładzie wystąpienia ciągu zawierającego trzy znaki inne niż ASCII — ZAKREŚLONA WIELKA LITERA ŁACI S (U+24C8), SUPERSCRIPT FIVE (U+2075) i INFINITY (U+221E) — oddzielona spacjami. Jak pokazuje dane wyjściowe z przykładu, gdy ciąg jest zakodowany, trzy oryginalne znaki nieprzestrłowe są zastępowane znakiem zapytania (U +003F), DIGIT FIVE (U + 0035) i DIGIT EIGHT (U + 0038). DIGIT EIGHT jest szczególnie słabym zamiennikiem nieobsługiwanych znaków INFINITY, a znak ZAPYTANIA wskazuje, że dla oryginalnego znaku nie było dostępne żadne mapowanie.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Mapowanie best-fit jest domyślnym zachowaniem <xref:System.Text.Encoding> obiektu, który koduje dane Unicode do danych strony kodowej i istnieją starsze aplikacje, które opierają się na tym zachowaniu. Jednak większość nowych aplikacji należy unikać najlepiej dopasowanych zachowań ze względów bezpieczeństwa. Na przykład aplikacje nie powinny umieszczać nazwy domeny za pomocą kodowania najlepiej dopasowanego.

> [!NOTE]
> Można również zaimplementować niestandardowe mapowanie rezerwowe najlepiej dopasowane do kodowania. Aby uzyskać więcej informacji, zobacz [implementing niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

Jeśli najlepiej dopasowany rezerwowy jest domyślny dla obiektu kodowania, można wybrać inną <xref:System.Text.Encoding> strategię rezerwową podczas pobierania obiektu przez wywołanie <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> lub <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> przeciążenie. Poniższa sekcja zawiera przykład, który zastępuje każdy znak, który nie może być mapowany na stronę kodową 1252 gwiazdką (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Wymiana rezerwy

Gdy znak nie ma dokładnego dopasowania w schemacie docelowym, ale nie ma odpowiedniego znaku, który można odwzorować, aplikacja może określić znak zastępczy lub ciąg. Jest to domyślne zachowanie dekodera Unicode, który zastępuje dowolną sekwencję dwu bajtów, której nie można rozszyfrować za pomocą REPLACEMENT_CHARACTER (U+FFFD). Jest to również domyślne <xref:System.Text.ASCIIEncoding> zachowanie klasy, która zastępuje każdy znak, którego nie może zakodować ani dekodować za pomocą znaku zapytania. Poniższy przykład ilustruje zastąpienie znaków dla ciągu Unicode z poprzedniego przykładu. Jak pokazuje dane wyjściowe, każdy znak, którego nie można zdekodować do wartości bajtów ASCII, jest zastępowany przez 0x3F, który jest kodem ASCII dla znaku zapytania.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

.NET zawiera <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.DecoderReplacementFallback> i klasy, które zastępują ciąg zastępczy, jeśli znak nie jest mapowany dokładnie w operacji kodowania lub dekodowania. Domyślnie ten ciąg zastępczy jest znakiem zapytania, ale można wywołać przeciążenie konstruktora klasy, aby wybrać inny ciąg. Zazwyczaj ciąg zastępczy jest pojedynczym znakiem, chociaż nie jest to wymagane. Poniższy przykład zmienia zachowanie kodera strony koderowej 1252, tworząc wystąpienie <xref:System.Text.EncoderReplacementFallback> obiektu, który używa gwiazdki (*) jako ciągu zastępczego.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Można również zaimplementować klasę zastępczą dla kodowania. Aby uzyskać więcej informacji, zobacz [implementing niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

Oprócz znaku zapytania (U+003F) znak zastępczy Unicode (U+FFFD) jest powszechnie używany jako ciąg zastępczy, szczególnie w przypadku dekodowania sekwencji bajtów, których nie można pomyślnie przetłumaczyć na znaki Unicode. Możesz jednak wybrać dowolny ciąg zastępczy i może on zawierać wiele znaków.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Rezerwa wyjątku

Zamiast zapewniać najlepiej dopasowany rezerwowy lub ciąg zastępczy, koder <xref:System.Text.EncoderFallbackException> może zgłosić, jeśli nie jest w stanie zakodować zestawu znaków, a dekoder może zgłosić, <xref:System.Text.DecoderFallbackException> jeśli nie jest w stanie zdekodować tablicy bajtowej. Aby zgłosić wyjątek w operacjach kodowania <xref:System.Text.EncoderExceptionFallback> i <xref:System.Text.DecoderExceptionFallback> dekodowania, należy <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> podać obiekt i obiekt, odpowiednio, do metody. Poniższy przykład ilustruje wyjątek rezerwowych <xref:System.Text.ASCIIEncoding> z klasy.

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Można również zaimplementować niestandardowy program obsługi wyjątków dla operacji kodowania. Aby uzyskać więcej informacji, zobacz [implementing niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

Obiekty <xref:System.Text.EncoderFallbackException> <xref:System.Text.DecoderFallbackException> i obiekty zawierają następujące informacje o warunku, który spowodował wyjątek:

- Obiekt <xref:System.Text.EncoderFallbackException> zawiera <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodę, która wskazuje, czy znak lub znaki, które nie mogą być zakodowane `true`reprezentują nieznaną parę zastępczą (w takim `false`przypadku metoda zwraca) lub nieznany pojedynczy znak (w którym to przypadku metoda zwraca ). Znaki w parze zastępczej są <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> dostępne z i właściwości. Nieznany pojedynczy znak jest <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> dostępny z właściwości. Właściwość <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje położenie w ciągu, w którym znaleziono pierwszy znak, który nie mógł być zakodowany.

- Obiekt <xref:System.Text.DecoderFallbackException> zawiera <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> właściwość, która zwraca tablicę bajtów, których nie można zdekodować. Właściwość <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje pozycję początkową nieznanych bajtów.

Mimo <xref:System.Text.EncoderFallbackException> że <xref:System.Text.DecoderFallbackException> obiekty i zapewniają odpowiednie informacje diagnostyczne dotyczące wyjątku, nie zapewniają one dostępu do buforu kodowania lub dekodowania. W związku z tym nie zezwalają na zastępowanie lub poprawianie nieprawidłowych danych w ramach metody kodowania lub dekodowania.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Wdrażanie niestandardowej strategii awaryjnej

Oprócz mapowania najlepiej dopasowanych, które jest implementowane wewnętrznie przez strony kodowe, .NET zawiera następujące klasy do implementowania strategii rezerwowej:

- Użyj <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.EncoderReplacementFallbackBuffer> i zamienić znaki w operacjach kodowania.

- <xref:System.Text.DecoderReplacementFallback> Używaj <xref:System.Text.DecoderReplacementFallbackBuffer> i zamieniaj znaki w operacjach dekodowania.

- Użyj <xref:System.Text.EncoderExceptionFallback> <xref:System.Text.EncoderExceptionFallbackBuffer> i <xref:System.Text.EncoderFallbackException> rzucić, gdy znak nie może być zakodowany.

- Użyj <xref:System.Text.DecoderExceptionFallback> <xref:System.Text.DecoderExceptionFallbackBuffer> i <xref:System.Text.DecoderFallbackException> rzucać, gdy znak nie może być dekodowany.

Ponadto można zaimplementować niestandardowe rozwiązanie, które używa najlepiej dopasowanych rezerwowych, rezerwowych lub rezerwowych wyjątków, wykonując następujące kroki:

1. Wywodź <xref:System.Text.EncoderFallback> klasę z operacji kodowania i z <xref:System.Text.DecoderFallback> operacji dekodowania.

2. Wywodź <xref:System.Text.EncoderFallbackBuffer> klasę z operacji kodowania i z <xref:System.Text.DecoderFallbackBuffer> operacji dekodowania.

3. W przypadku rezerwowego wyjątku, <xref:System.Text.EncoderFallbackException> jeśli <xref:System.Text.DecoderFallbackException> wstępnie zdefiniowane i klasy nie spełniają twoich <xref:System.Exception> potrzeb, należy wyprowadzić klasę z obiektu wyjątku, takiego jak lub <xref:System.ArgumentException>.

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Wyprowadzenie z emoderFallback lub DecoderFallback

Aby zaimplementować niestandardowe rozwiązanie rezerwowe, <xref:System.Text.EncoderFallback> należy utworzyć klasę, <xref:System.Text.DecoderFallback> która dziedziczy z operacji kodowania i z operacji dekodowania. Wystąpienia tych klas są przekazywane <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> do metody i służyć jako pośrednik między klasy kodowania i implementacji rezerwowej.

Podczas tworzenia niestandardowego rozwiązania rezerwowego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- Lub <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> właściwość, która zwraca maksymalną możliwą liczbę znaków, które najlepiej dopasowane, zastępcze lub rezerwowe wyjątek może powrócić do zastąpienia pojedynczego znaku. W przypadku rezerwowego wyjątku niestandardowego jego wartość wynosi zero.

- Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> lub, która zwraca <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> niestandardowe lub implementacji. Metoda jest wywoływana przez koder, gdy napotka pierwszy znak, że nie jest w stanie pomyślnie zakodować lub przez dekoder, gdy napotka pierwszy bajt, że nie jest w stanie pomyślnie dekodować.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Pochodna z EmkoderFallbackBuffer lub DecoderFallbackBuffer

Aby zaimplementować niestandardowe rozwiązanie rezerwowe, należy <xref:System.Text.EncoderFallbackBuffer> również utworzyć klasę, <xref:System.Text.DecoderFallbackBuffer> która dziedziczy z operacji kodowania i z operacji dekodowania. Wystąpienia tych klas są zwracane przez <xref:System.Text.EncoderFallback> <xref:System.Text.DecoderFallback> <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metodę i klas. Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> jest wywoływana przez koder, gdy napotka pierwszy znak, który nie <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> jest w stanie zakodować, a metoda jest wywoływana przez dekoder, gdy napotka jeden lub więcej bajtów, że nie jest w stanie dekodować. I <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> klasy zapewniają implementacji rezerwowej. Każde wystąpienie reprezentuje bufor, który zawiera znaki rezerwowe, które zastąpią znak, który nie może być zakodowany lub sekwencji bajtów, które nie mogą być dekodowane.

Podczas tworzenia niestandardowego rozwiązania rezerwowego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- Metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> lub. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>jest wywoływana przez koder, aby zapewnić bufor rezerwowy z informacjami o znaku, który nie może zakodować. Ponieważ znak, który ma być zakodowany, może być parą zastępczą, ta metoda jest przeciążona. Jedno przeciążenie jest przekazywane znak do zakodowania i jego indeks w ciągu. Drugie przeciążenie jest przekazywane wysoki i niski surogat wraz z jego indeksu w ciągu. Metoda <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> jest wywoływana przez dekoder, aby zapewnić bufor rezerwowy z informacjami o bajtach, których nie można zdekodować. Ta metoda jest przekazywana tablicy bajtów, które nie można zdekodować, wraz z indeksem pierwszego bajtu. Metoda rezerwowa powinna `true` zostać zwracana, jeśli bufor rezerwowy może dostarczyć najlepiej dopasowany lub zastępczy znak lub znaki; w przeciwnym razie `false`powinien zwrócić . W przypadku rezerwowego wyjątku metoda rezerwowa powinna zgłosić wyjątek.

- Metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> lub, która jest wywoływana wielokrotnie przez koder lub dekoder, aby uzyskać następny znak z buforu rezerwowego. Po powrocie wszystkie znaki rezerwowe zostały zwrócone, metoda powinna zwrócić U + 0000.

- Lub <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> właściwość, która zwraca liczbę znaków pozostałych w buforze rezerwowym.

- Metoda <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> lub, która przenosi bieżącą pozycję w buforze rezerwowym do poprzedniego znaku.

- Metoda <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> lub, która ponownie inicjuje bufor rezerwowy.

Jeśli implementacja rezerwowa jest najlepiej dopasowanym rezerwowym lub rezerwowym, <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> klasy pochodzące z, a także utrzymują dwa pola wystąpienia prywatnego: dokładną liczbę znaków w buforze; i indeks następnego znaku w buforze, aby powrócić.

### <a name="an-encoderfallback-example"></a>Przykład emoderFallback

We wcześniejszym przykładzie użyto zastępczego powrotu do zastąpienia znaków Unicode, które nie odpowiadały znakom ASCII gwiazdką (*). W poniższym przykładzie użyto niestandardowej implementacji rezerwowej najlepiej dopasowanych, aby zapewnić lepsze mapowanie znaków innych niż ASCII.

Poniższy kod definiuje klasę `CustomMapper` o nazwie, <xref:System.Text.EncoderFallback> która jest pochodną do obsługi najlepiej dopasowanych mapowania znaków innych niż ASCII. Jego `CreateFallbackBuffer` metoda `CustomMapperFallbackBuffer` zwraca obiekt, <xref:System.Text.EncoderFallbackBuffer> który zapewnia implementację. Klasa `CustomMapper` używa <xref:System.Collections.Generic.Dictionary%602> obiektu do przechowywania mapowań nieobsługiconych znaków Unicode (wartość klucza) i odpowiadających im znaków 8-bitowych (które są przechowywane w dwóch kolejnych bajtach w 64-bitowej całkowitej liczby). Aby to mapowanie było dostępne w `CustomMapper` buforze rezerwowym, `CustomMapperFallbackBuffer` wystąpienie jest przekazywane jako parametr do konstruktora klasy. Ponieważ najdłuższe mapowanie jest ciąg "INF" dla znaku Unicode U `MaxCharCount` + 221E, właściwość zwraca 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Poniższy kod definiuje `CustomMapperFallbackBuffer` klasę, która pochodzi <xref:System.Text.EncoderFallbackBuffer>od . Słownik, który zawiera mapowania najlepiej dopasowanych i `CustomMapper` który jest zdefiniowany w wystąpieniu jest dostępny z jego konstruktora klasy. Jego `Fallback` metoda `true` zwraca, jeśli którykolwiek ze znaków Unicode, który nie może zakodować kodera ASCII są zdefiniowane w słowniku mapowania; w przeciwnym `false`razie zwraca . Dla każdego rezerwowego `count` zmienna prywatna wskazuje liczbę znaków, które pozostają `index` do zwrócenia, a zmienna `charsToReturn`prywatna wskazuje pozycję w buforze ciągu , następnego znaku do zwrócenia.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Poniższy kod następnie wystąpienia `CustomMapper` obiektu i przekazuje wystąpienie <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> go do metody. Dane wyjściowe wskazują, że najlepiej dopasowana implementacja rezerwowa pomyślnie obsługuje trzy znaki inne niż ASCII w oryginalnym ciągu.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do kodowania znaków w .NET](character-encoding-introduction.md)
- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
