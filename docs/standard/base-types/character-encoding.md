---
title: Kodowanie znaków w programie .NET
description: Dowiedz się więcej o kodowaniu i dekodowaniu znaków w .NET.
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
ms.openlocfilehash: 3cd461d8c56c3f31bf3ffe04acf239ecd32fe328
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711444"
---
# <a name="character-encoding-in-net"></a>Kodowanie znaków w programie .NET

Znaki są abstrakcyjne jednostki, które mogą być reprezentowane na wiele różnych sposobów. Kodowanie znaków to system, który paruje każdy znak w obsługiwanym zestawie znaków z pewną wartością reprezentującą ten znak. Na przykład kod Morse'a jest kodowaniem znaków, które paruje każdy znak alfabetu rzymskiego ze wzorem kropek i kresek, które nadają się do transmisji za pomocą linii telegraficznych. Kodowanie znaków dla komputerów paruje każdy znak w obsługiwanym zestawie znaków z wartością liczbową reprezentującą ten znak. Kodowanie znaków ma dwa różne składniki:

- Koder, który tłumaczy sekwencję znaków na sekwencję wartości liczbowych (bajtów).

- Dekoder, który tłumaczy sekwencję bajtów na sekwencję znaków.

Kodowanie znaków opisuje reguły, według których działają koder i dekoder. Na przykład <xref:System.Text.UTF8Encoding> klasa opisuje reguły kodowania i dekodowania z 8-bitowego formatu transformacji Unicode (UTF-8), który używa od jednego do czterech bajtów do reprezentowania pojedynczego znaku Unicode. Kodowanie i dekodowanie może również obejmować sprawdzanie poprawności. Na przykład <xref:System.Text.UnicodeEncoding> klasa sprawdza wszystkie surogaty, aby upewnić się, że stanowią one prawidłowe pary zastępcze. (Para zastępcza składa się ze znaku z punktem kodu, który waha się od U + D800 do U + DBFF następuje znak z punktem kodu, który waha się od U + DC00 do U + DFFF.)  Strategia rezerwowa określa, jak koder obsługuje nieprawidłowe znaki lub jak dekoder obsługuje nieprawidłowe bajty.

> [!WARNING]
> Klasy kodowania .NET umożliwiają przechowywanie i konwertowanie danych znaków. Nie powinny być używane do przechowywania danych binarnych w formie ciągu. W zależności od użytego kodowania konwersja danych binarnych do formatu ciągu za pomocą klas kodowania może wprowadzić nieoczekiwane zachowanie i wygenerować niedokładne lub uszkodzone dane. Aby przekonwertować dane binarne <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> na formularz ciągu, należy użyć tej metody.

.NET używa kodowania UTF-16 (reprezentowane <xref:System.Text.UnicodeEncoding> przez klasę) do reprezentowania znaków i ciągów. Aplikacje, które są przeznaczone dla języka wspólnego runtime używać koderów do mapowania reprezentacji znaków Unicode obsługiwane przez wspólny język wykonywania do innych schematów kodowania. Używają dekoderów do mapowania znaków z kodowania innych niż Unicode do Unicode.

Ten temat składa się z następujących sekcji:

- [Kodowanie w .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)

- [Wybieranie klasy kodowania](../../../docs/standard/base-types/character-encoding.md#Selecting)

- [Korzystanie z obiektu kodowania](../../../docs/standard/base-types/character-encoding.md#Using)

- [Wybór strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)

- [Wdrażanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom)

<a name="Encodings"></a>

## <a name="encodings-in-net"></a>Kodowanie w .NET

Wszystkie klasy kodowania znaków w .NET dziedziczą z <xref:System.Text.Encoding?displayProperty=nameWithType> klasy, która jest klasą abstrakcyjną, która definiuje funkcje wspólne dla wszystkich kodowania znaków. Aby uzyskać dostęp do poszczególnych obiektów kodowania zaimplementowanych w programie .NET, wykonaj następujące czynności:

- Użyj właściwości statycznych <xref:System.Text.Encoding> klasy, które zwracają obiekty reprezentujące standardowe kodowanie znaków dostępne w .NET (ASCII, UTF-7, UTF-8, UTF-16 i UTF-32). Na przykład <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Text.UnicodeEncoding> obiekt. Każdy obiekt używa zastępczego rezerwowego do obsługi ciągów, których nie może zakodować i bajtów, których nie może dekodować. (Aby uzyskać więcej informacji, zobacz [sekcję Rezerwa zastępcza).](../../../docs/standard/base-types/character-encoding.md#Replacement)

- Wywołanie konstruktora klasy kodowania. Obiekty kodowania ASCII, UTF-7, UTF-8, UTF-16 i UTF-32 można utworzyć w ten sposób. Domyślnie każdy obiekt używa zastępczego rezerwowego do obsługi ciągów, których nie może zakodować i bajtów, których nie może dekodować, ale można określić, że zamiast tego powinien zostać zgłoszony wyjątek. (Aby uzyskać więcej informacji, zobacz [sekcje Rezerwa zastępcza](../../../docs/standard/base-types/character-encoding.md#Replacement) i [Rezerwa wyjątku).](../../../docs/standard/base-types/character-encoding.md#Exception)

- Wywołać <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> konstruktora i przekazać mu liczby całkowitej, która reprezentuje kodowanie. Standardowe obiekty kodowania używają zastępczego rezerwowego, a strona kodowa i dwubajtowy zestaw znaków (DBCS) kodują obiekty, używają najlepiej dopasowanych rezerwowych do obsługi ciągów, których nie mogą kodować i bajtów, których nie mogą dekodować. (Aby uzyskać więcej informacji, zobacz sekcję [Rezerwowa najlepszego](../../../docs/standard/base-types/character-encoding.md#BestFit) dopasowania).

- Wywołaj <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metodę, która zwraca wszelkie standardowe, strony kodowej lub kodowania DBCS dostępne w .NET. Przeciążenia pozwalają określić obiekt rezerwowy zarówno dla kodera, jak i dekodera.

> [!NOTE]
> Standard Unicode przypisuje punkt kodowy (numer) i nazwę do każdego znaku w każdym obsługiwanym skrypcie. Na przykład znak "A" jest reprezentowany przez punkt kodowy U+0041 i nazwę "LATIN CAPITAL LETTER A". Kodowanie formatu transformacji Unicode (UTF) definiują sposoby kodowania tego punktu kodu w sekwencji jednego lub więcej bajtów. Schemat kodowania Unicode upraszcza tworzenie aplikacji gotowych do użycia na całym świecie, ponieważ umożliwia reprezentowanie znaków z dowolnego zestawu znaków w jednym kodowaniu. Deweloperzy aplikacji nie muszą już śledzić schematu kodowania, który był używany do tworzenia znaków dla określonego języka lub systemu pisania, a dane mogą być udostępniane między systemami na arenie międzynarodowej bez uszkodzenia.
>
> .NET obsługuje trzy kodowania zdefiniowane przez standard Unicode: UTF-8, UTF-16 i UTF-32. Aby uzyskać więcej informacji, zobacz Standard Unicode na [stronie głównej Unicode](https://www.unicode.org/).

Można pobrać informacje o wszystkich kodowania dostępnych w .NET, wywołując <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metodę. Program .NET obsługuje systemy kodowania znaków wymienione w poniższej tabeli.

|Kodowanie|Klasa|Opis|Zalety/wady|
|--------------|-----------|-----------------|-------------------------------|
|ASCII|<xref:System.Text.ASCIIEncoding>|Koduje ograniczony zakres znaków przy użyciu dolnych siedmiu bitów bajtu.|Ponieważ to kodowanie obsługuje tylko wartości znaków od U +0000 do U + 007F, w większości przypadków jest nieodpowiednie dla aplikacji umiędzynarodowionych.|
|UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaki jako sekwencje 7-bitowych znaków ASCII. Znaki Unicode inne niż ASCII są reprezentowane przez sekwencję ucieczki znaków ASCII.|UTF-7 obsługuje protokoły, takie jak protokoły poczty e-mail i grup dyskusyjnych. Jednak UTF-7 nie jest szczególnie bezpieczny lub niezawodny. W niektórych przypadkach zmiana jednego bitu może radykalnie zmienić interpretację całego ciągu UTF-7. W innych przypadkach różne ciągi UTF-7 można zakodować ten sam tekst. W przypadku sekwencji, które zawierają znaki inne niż ASCII, UTF-7 wymaga więcej miejsca niż UTF-8, a kodowanie/dekodowanie jest wolniejsze. W związku z tym należy użyć UTF-8 zamiast UTF-7, jeśli to możliwe.|
|UTF-8|<xref:System.Text.UTF8Encoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencję od jednego do czterech bajtów.|UTF-8 obsługuje 8-bitowe rozmiary danych i działa dobrze z wieloma istniejącymi systemami operacyjnymi. W przypadku zakresu znaków ASCII UTF-8 jest identyczny z kodowaniem ASCII i umożliwia szerszy zestaw znaków. Jednak w przypadku skryptów chińsko-japońsko-koreańskich (CJK) utf-8 może wymagać trzech bajtów dla każdego znaku i może potencjalnie powodować większe rozmiary danych niż UTF-16. Należy zauważyć, że czasami ilość danych ASCII, takich jak tagi HTML, uzasadnia zwiększony rozmiar dla zakresu CJK.|
|UTF-16|<xref:System.Text.UnicodeEncoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencję jednej lub dwóch 16-bitowych liczb całkowitych. Najczęstsze znaki Unicode wymagają tylko jednego punktu kodowego UTF-16, chociaż dodatkowe znaki Unicode (U +10000 i większe) wymagają dwóch zastępczych punktów kodu UTF-16. Zarówno little-endian i big-endian byte zamówienia są obsługiwane.|Kodowanie UTF-16 jest używane przez środowisko <xref:System.Char> uruchomieniowe języka wspólnego do reprezentowania i <xref:System.String> `WCHAR` wartości i jest używane przez system operacyjny Windows do reprezentowania wartości.|
|UTF-32|<xref:System.Text.UTF32Encoding>|Reprezentuje każdy punkt kodu Unicode jako 32-bitową liczbę całkowitą. Zarówno little-endian i big-endian byte zamówienia są obsługiwane.|Kodowanie UTF-32 jest używane, gdy aplikacje chcą uniknąć zastępczego zachowania punktu kodu kodowania UTF-16 w systemach operacyjnych, dla których zakodowane miejsce jest zbyt ważne. Pojedyncze glify renderowane na wyświetlaczu nadal mogą być kodowane za pomocą więcej niż jednego znaku UTF-32.|
|Kodowanie ANSI/ISO||Zapewnia obsługę różnych stron kodowych. W systemach operacyjnych Windows strony kodowe są używane do obsługi określonego języka lub grupy języków. W przypadku tabeli, która zawiera listę stron kodowych obsługiwanych przez program .NET, zobacz <xref:System.Text.Encoding> klasę. Można pobrać obiekt kodowania dla określonej strony kodowej, wywołując <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metodę.|Strona kodowa zawiera 256 punktów kodowych i jest oparta na zeru. Na większości stron kodowych punkty kodu od 0 do 127 reprezentują zestaw znaków ASCII, a punkty kodu od 128 do 255 różnią się znacznie między stronami kodowymi. Na przykład strona kodowa 1252 zawiera znaki dla systemów pisania łacińskiego, w tym angielski, niemiecki i francuski. Ostatnie 128 punktów kodowych na stronie kodowej 1252 zawiera znaki akcentu. Strona kodowa 1253 zawiera kody znaków, które są wymagane w greckim systemie pisania. Ostatnie 128 punktów kodowych na stronie kodowej 1253 zawiera znaki greckie. W rezultacie aplikacja, która opiera się na stronach kodowych ANSI nie może przechowywać grecki i niemiecki w tym samym strumieniu tekstu, chyba że zawiera identyfikator, który wskazuje stronę kodową, do której istnieje odwołanie.|
|Dwubajtowe kodowanie zestawu znaków (DBCS)||Obsługuje języki, takie jak chiński, japoński i koreański, które zawierają więcej niż 256 znaków. W DBCS para punktów kodu (podwójny bajt) reprezentuje każdy znak. Właściwość <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> zwraca `false` dla kodowania DBCS. Można pobrać obiekt kodowania dla określonego DBCS <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> wywołując metodę.|W DBCS para punktów kodu (podwójny bajt) reprezentuje każdy znak. Gdy aplikacja obsługuje dane DBCS, pierwszy bajt znaku DBCS (bajt ołowiu) jest przetwarzany w połączeniu z bajtem szlaku, który natychmiast następuje po nim. Ponieważ pojedyncza para dwubajtowych punktów kodu może reprezentować różne znaki w zależności od strony kodowej, ten schemat nadal nie zezwala na kombinację dwóch języków, takich jak japoński i chiński, w tym samym strumieniu danych.|

Te kodowania umożliwiają pracę ze znakami Unicode, a także z kodowaniem, które są najczęściej używane w starszych aplikacjach. Ponadto można utworzyć niestandardowe kodowanie, definiując klasę, <xref:System.Text.Encoding> która wywodzi się i zaostrza jej elementy członkowskie.

### <a name="platform-notes-net-core"></a>Uwagi dotyczące platformy: .NET Core

Domyślnie .NET Core nie udostępnia żadnych kodowania strony kodowej innych niż strona kodowa 28591 i kodowanie Unicode, takich jak UTF-8 i UTF-16. Można jednak dodać kodowanie strony kodowej znajdujące się w standardowych aplikacjach systemu Windows, które są przeznaczone dla aplikacji .NET. Aby uzyskać pełne <xref:System.Text.CodePagesEncodingProvider> informacje, zobacz temat.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Wybieranie klasy kodowania

Jeśli masz możliwość wyboru kodowania, które ma być używane przez aplikację, należy użyć kodowania <xref:System.Text.UTF8Encoding> <xref:System.Text.UnicodeEncoding>Unicode, najlepiej albo albo . (.NET obsługuje również trzecie kodowanie <xref:System.Text.UTF32Encoding>Unicode,)

Jeśli planujesz użyć kodowania ASCII<xref:System.Text.ASCIIEncoding>( <xref:System.Text.UTF8Encoding> ), wybierz zamiast tego. Dwa kodowania są identyczne dla zestawu znaków ASCII, ale <xref:System.Text.UTF8Encoding> ma następujące zalety:

- Może reprezentować każdy znak Unicode, podczas <xref:System.Text.ASCIIEncoding> gdy obsługuje tylko wartości znaków Unicode między U + 0000 i U + 007F.

- Zapewnia wykrywanie błędów i lepsze bezpieczeństwo.

- Został dostrojony do tak szybko, jak to możliwe i powinny być szybsze niż jakiekolwiek inne kodowania. Nawet w przypadku zawartości, która jest całkowicie <xref:System.Text.UTF8Encoding> ASCII, operacje <xref:System.Text.ASCIIEncoding>wykonywane z są szybsze niż operacje wykonywane z .

Należy rozważyć <xref:System.Text.ASCIIEncoding> użycie tylko dla starszych aplikacji. Jednak nawet w przypadku <xref:System.Text.UTF8Encoding> starszych aplikacji może być lepszym wyborem z następujących powodów (przy założeniu ustawień domyślnych):

- Jeśli aplikacja ma zawartość, która nie jest ściśle <xref:System.Text.ASCIIEncoding>ASCII i koduje go, każdy znak nie ASCII koduje jako znak zapytania (?). Jeśli aplikacja następnie dekoduje te dane, informacje zostaną utracone.

- Jeśli aplikacja ma zawartość, która nie jest ściśle <xref:System.Text.UTF8Encoding>ASCII i koduje go, wynik wydaje się niezrozumiały, jeśli interpretowane jako ASCII. Jednak jeśli aplikacja następnie używa dekodera UTF-8 do dekodowania tych danych, dane wykonuje podróż w obie strony pomyślnie.

W aplikacji sieci web znaki wysyłane do klienta w odpowiedzi na żądanie sieci web powinny odzwierciedlać kodowanie używane na kliencie. W większości przypadków należy <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> ustawić właściwość na wartość <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> zwracaną przez właściwość, aby wyświetlić tekst w kodowaniu, którego oczekuje użytkownik.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Korzystanie z obiektu kodowania

Koder konwertuje ciąg znaków (najczęściej znaki Unicode) na jego odpowiednik numeryczny (bajtowy). Na przykład można użyć kodera ASCII do konwersji znaków Unicode na ASCII, aby mogły być wyświetlane w konsoli. Aby wykonać konwersję, <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> należy wywołać metodę. Jeśli chcesz określić, ile bajtów jest potrzebnych do przechowywania zakodowanych znaków przed <xref:System.Text.Encoding.GetByteCount%2A> wykonaniem kodowania, możesz wywołać tę metodę.

W poniższym przykładzie użyto tablicy pojedynczego bajtu do kodowania ciągów w dwóch oddzielnych operacjach. Utrzymuje indeks, który wskazuje pozycję początkową w tablicy bajtów dla następnego zestawu bajtów zakodowanych przez ASCII. Wywołuje metodę, <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> aby upewnić się, że tablica bajtów jest wystarczająco duży, aby pomieścić zakodowany ciąg. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodę kodowania znaków w ciągu.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekoder konwertuje tablicę bajtów, która odzwierciedla kodowanie określonego znaku na zestaw znaków, w tablicy znaków lub w ciągu. Aby odkodować tablicę bajtów do <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> tablicy znaków, należy wywołać metodę. Aby odkodować tablicę bajtów na <xref:System.Text.Encoding.GetString%2A> ciąg, należy wywołać metodę. Jeśli chcesz określić, ile znaków jest potrzebnych do przechowywania zdekodowanych bajtów <xref:System.Text.Encoding.GetCharCount%2A> przed wykonaniem dekodowania, możesz wywołać tę metodę.

Poniższy przykład koduje trzy ciągi, a następnie dekoduje je w jednej tablicy znaków. Utrzymuje indeks, który wskazuje pozycję początkową w tablicy znaków dla następnego zestawu znaków zdekodowanych. Wywołuje metodę, <xref:System.Text.ASCIIEncoding.GetCharCount%2A> aby upewnić się, że tablica znaków jest wystarczająco duża, aby pomieścić wszystkie znaki dekodowane. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodę do dekodowania tablicy bajtów.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kodowania i dekodowania klasy pochodzące jednych z <xref:System.Text.Encoding> są przeznaczone do pracy nad kompletnym zestawem danych; oznacza to, że wszystkie dane, które mają być zakodowane lub zdekodowane jest dostarczany w wywołaniu jednej metody. Jednak w niektórych przypadkach dane są dostępne w strumieniu, a dane, które mają być zakodowane lub dekodowane mogą być dostępne tylko z oddzielnych operacji odczytu. Wymaga to operacji kodowania lub dekodowania, aby zapamiętać każdy zapisany stan z poprzedniego wywołania. Metody klas pochodzących z <xref:System.Text.Encoder> <xref:System.Text.Decoder> i są w stanie obsługiwać kodowania i dekodowania operacji, które obejmują wiele wywołań metody.

Obiekt <xref:System.Text.Encoder> dla określonego kodowania jest dostępny z <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> tej właściwości kodowania. Obiekt <xref:System.Text.Decoder> dla określonego kodowania jest dostępny z <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> tej właściwości kodowania. W przypadku operacji dekodowania należy <xref:System.Text.Decoder> pamiętać, <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> że klasy pochodzące z obejmują metodę, <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>ale nie mają metody, która odpowiada .

W poniższym przykładzie przedstawiono różnicę między przy użyciu <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> i <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody dekodowania tablicy bajtów Unicode. Przykład koduje ciąg, który zawiera niektóre znaki Unicode do pliku, a następnie używa dwóch metod dekodowania do dekodowania ich dziesięć bajtów naraz. Ponieważ para zastępcza występuje w dziesiątym i jedenastym bajtach, jest dekodowana w wywołaniach oddzielnych metod. Jak pokazuje dane <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> wyjściowe, metoda nie jest w stanie poprawnie odkodować bajtów i zamiast tego zastępuje je U + FFFD (znak zastępczy). Z drugiej strony <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda jest w stanie pomyślnie odkodować tablicy bajtów, aby uzyskać oryginalny ciąg.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Wybór strategii rezerwowej

Gdy metoda próbuje zakodować lub odkodować znak, ale nie istnieje mapowanie, musi zaimplementować strategię rezerwową, która określa, jak powinno być obsługiwane mapowanie nie powiodło się. Istnieją trzy rodzaje strategii rezerwowych:

- Najlepiej dopasowany rezerwowy

- Rezerwowy zamiennik

- Rezerwa wyjątku

> [!IMPORTANT]
> Najczęstsze problemy w operacjach kodowania występują, gdy znak Unicode nie może być mapowany do kodowania określonej strony kodowej. Najczęstsze problemy w operacjach dekodowania występują, gdy nieprawidłowe sekwencje bajtów nie mogą być tłumaczone na prawidłowe znaki Unicode. Z tych powodów należy wiedzieć, która strategia rezerwowa określonego obiektu kodowania używa. Jeśli to możliwe, należy określić strategię rezerwową używaną przez obiekt kodowania podczas tworzenia wystąpienia obiektu.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Najlepiej dopasowany rezerwowy

Jeśli znak nie ma dokładnego dopasowania w kodowaniu docelowym, koder może spróbować zamapować go na podobny znak. (Best-fit rezerwowy jest głównie kodowania, a nie problem dekodowania. Istnieje bardzo niewiele stron kodowych, które zawierają znaki, których nie można pomyślnie zamapować na Unicode.) Najlepiej dopasowany rezerwowy jest domyślnym dla kodowania strony kodowej i dwubajtowych kodowań zestawu znaków, które są pobierane przez <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> i <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> przeciążenia.

> [!NOTE]
> Teoretycznie klasy kodowania Unicode dostępne w<xref:System.Text.UTF8Encoding>.NET ( , <xref:System.Text.UnicodeEncoding>i <xref:System.Text.UTF32Encoding>) obsługują każdy znak w każdym zestawie znaków, dzięki czemu mogą być używane do wyeliminowania najlepiej dopasowanych problemów rezerwowych.

Strategie najlepszego dopasowania różnią się w zależności od strony kodowej. Na przykład dla niektórych stron kodowych znaki łacińskie o pełnej szerokości są mapowane na bardziej typowe znaki łacińskie o połowie szerokości. W przypadku innych stron kodowych to mapowanie nie jest wykonane. Nawet w agresywnej strategii best-fit, nie ma możliwego dopasowania dla niektórych znaków w niektórych kodowaniach. Na przykład chiński ideograf nie ma rozsądnego mapowania na stronę kodową 1252. W takim przypadku używany jest ciąg zastępczy. Domyślnie ten ciąg jest tylko pojedynczym znakiem zapytania (U +003F).

> [!NOTE]
> Strategie najlepiej dopasowane nie są szczegółowo udokumentowane. Jednak kilka stron kodowych są udokumentowane w witrynie internetowej [konsorcjum Unicode.](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) Zapoznaj się z plikiem **readme.txt** w tym folderze, aby uzyskać opis sposobu interpretowania plików mapowania.

W poniższym przykładzie użyto strony kodowej 1252 (strona kodowa systemu Windows dla języków zachodnioeuropejskich) w celu zilustrowania mapowania najlepiej dopasowanego i jego wad. Metoda <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> jest używana do pobierania obiektu kodowania dla strony kodowej 1252. Domyślnie używa mapowania najlepiej dopasowane dla znaków Unicode, które nie obsługują. W przykładzie tworzy ciąg zawierający trzy znaki inne niż ASCII - CIRCLED LATIN CAPITAL LETTER S (U+24C8), SUPERSCRIPT FIVE (U+2075) i INFINITY (U+221E) - oddzielone spacjami. Jak pokazuje dane wyjściowe z przykładu, gdy ciąg jest zakodowany, trzy oryginalne znaki niespętowe są zastępowane znakiem ZAPYTANIA (U +003F), DIGIT FIVE (U+0035) i DIGIT EIGHT (U+0038). CYFRA ÓSMA jest szczególnie słabym zamiennikiem nieobsługiwanego znaku INFINITY, a znak zapytania wskazuje, że dla oryginalnego znaku nie było dostępne mapowanie.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Mapowanie najlepiej dopasowane jest domyślnym zachowaniem <xref:System.Text.Encoding> obiektu, który koduje dane Unicode do danych strony kodowej, a istnieją starsze aplikacje, które opierają się na tym zachowaniu. Jednak większość nowych aplikacji należy unikać zachowanie najlepiej dopasowane ze względów bezpieczeństwa. Na przykład aplikacje nie powinny umieszczać nazwy domeny za pomocą kodowania najlepiej dopasowanego.

> [!NOTE]
> Można również zaimplementować niestandardowe mapowanie rezerwowe najlepiej dopasowane dla kodowania. Aby uzyskać więcej informacji, zobacz [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

Jeśli najlepiej dopasowany rezerwowy jest domyślnym obiektem kodującym, można wybrać inną <xref:System.Text.Encoding> strategię <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> rezerwową podczas pobierania obiektu przez wywołanie lub <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> przeciążenie. Poniższa sekcja zawiera przykład, który zastępuje każdy znak, który nie może być mapowany na stronę kodową 1252 gwiazdką (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Rezerwa zastępcza

Gdy znak nie ma dokładnego dopasowania w schemacie docelowym, ale nie ma odpowiedniego znaku, na który można go mapować, aplikacja może określić znak zastępczy lub ciąg znaków. Jest to domyślne zachowanie dekodera Unicode, który zastępuje dowolną sekwencję dwubajtową, której nie można rozszyfrować za pomocą REPLACEMENT_CHARACTER (U +FFFD). Jest to również domyślne <xref:System.Text.ASCIIEncoding> zachowanie klasy, która zastępuje każdy znak, którego nie można zakodować lub odkodować znakiem zapytania. W poniższym przykładzie przedstawiono zastąpienie znaków dla ciągu Unicode z poprzedniego przykładu. Jak pokazuje dane wyjściowe, każdy znak, którego nie można zdekodować na wartość bajtu ASCII, jest zastępowany przez 0x3F, który jest kodem ASCII dla znaku zapytania.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

.NET zawiera <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.DecoderReplacementFallback> i klas, które zastępują ciąg zastępczy, jeśli znak nie mapuje dokładnie w operacji kodowania lub dekodowania. Domyślnie ten ciąg zastępczy jest znakiem zapytania, ale można wywołać przeciążenie konstruktora klasy, aby wybrać inny ciąg. Zazwyczaj ciąg zastępczy jest pojedynczy znak, chociaż nie jest to wymagane. Poniższy przykład zmienia zachowanie kodera strony kodowej 1252, tworząc <xref:System.Text.EncoderReplacementFallback> wystąpienie obiektu, który używa gwiazdki (*) jako ciągu zastępczego.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Można również zaimplementować klasę zastępczą dla kodowania. Aby uzyskać więcej informacji, zobacz [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

Oprócz znaku zapytania (U +003F), znak zastępczy Unicode (U + FFFD) jest powszechnie używany jako ciąg zastępczy, szczególnie podczas dekodowania sekwencji bajtów, których nie można pomyślnie przetłumaczyć na znaki Unicode. Możesz jednak wybrać dowolny ciąg zastępczy i może zawierać wiele znaków.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Rezerwa wyjątku

Zamiast zapewniać najlepiej dopasowany ciąg rezerwowy lub zastępczy, koder <xref:System.Text.EncoderFallbackException> może wystawić koder, jeśli nie jest w stanie <xref:System.Text.DecoderFallbackException> zakodować zestawu znaków, a dekoder może wystawić a, jeśli nie jest w stanie rozszyfrować tablicy bajtów. Aby zgłosić wyjątek w operacji kodowania i dekodowania, należy podać <xref:System.Text.EncoderExceptionFallback> obiekt i <xref:System.Text.DecoderExceptionFallback> obiekt, odpowiednio, do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Poniższy przykład ilustruje rezerwowego wyjątku z klasą. <xref:System.Text.ASCIIEncoding>

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Można również zaimplementować program obsługi wyjątków niestandardowych dla operacji kodowania. Aby uzyskać więcej informacji, zobacz [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.

I <xref:System.Text.EncoderFallbackException> <xref:System.Text.DecoderFallbackException> obiekty zawierają następujące informacje o stanie, który spowodował wyjątek:

- Obiekt <xref:System.Text.EncoderFallbackException> zawiera <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodę, która wskazuje, czy znak lub znaki, których nie można zakodować, `true`reprezentują nieznaną parę zastępczą (w takim przypadku zwraca metodę) lub nieznany pojedynczy znak (w takim przypadku zwraca `false`metodę). Znaki w parze zastępczej są <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> dostępne z i właściwości. Nieznany pojedynczy znak jest <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> dostępny w obiekcie. Właściwość <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje pozycję w ciągu, w którym znaleziono pierwszy znak, który nie mógł być zakodowany.

- Obiekt <xref:System.Text.DecoderFallbackException> zawiera <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> właściwość, która zwraca tablicę bajtów, których nie można zdekodować. Właściwość <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje pozycję początkową nieznanych bajtów.

Mimo <xref:System.Text.EncoderFallbackException> że <xref:System.Text.DecoderFallbackException> i obiekty zapewniają odpowiednie informacje diagnostyczne dotyczące wyjątku, nie zapewniają dostępu do buforu kodowania lub dekodowania. W związku z tym nie zezwalają one na nieprawidłowe dane, które mają być zastąpione lub poprawione w ramach metody kodowania lub dekodowania.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Wdrażanie niestandardowej strategii rezerwowej

Oprócz najlepszego mapowania, który jest implementowany wewnętrznie przez strony kodowe, .NET zawiera następujące klasy do implementowania strategii rezerwowej:

- Użyj <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.EncoderReplacementFallbackBuffer> i zastąpić znaki w operacjach kodowania.

- Użyj <xref:System.Text.DecoderReplacementFallback> <xref:System.Text.DecoderReplacementFallbackBuffer> i zastąpić znaki w operacjach dekodowania.

- Użyj <xref:System.Text.EncoderExceptionFallback> <xref:System.Text.EncoderExceptionFallbackBuffer> i wrzucić, <xref:System.Text.EncoderFallbackException> gdy znak nie może być zakodowany.

- Użyj <xref:System.Text.DecoderExceptionFallback> <xref:System.Text.DecoderExceptionFallbackBuffer> i rzucać, <xref:System.Text.DecoderFallbackException> gdy znak nie może być dekodowany.

Ponadto można zaimplementować niestandardowe rozwiązanie, które używa najlepiej dopasowanego rezerwowego, rezerwowego lub rezerwowego wyjątku, wykonując następujące kroki:

1. Wyprowadzić klasę <xref:System.Text.EncoderFallback> z operacji kodowania <xref:System.Text.DecoderFallback> i z operacji dekodowania.

2. Wyprowadzić klasę <xref:System.Text.EncoderFallbackBuffer> z operacji kodowania <xref:System.Text.DecoderFallbackBuffer> i z operacji dekodowania.

3. W przypadku rezerwowego wyjątku, <xref:System.Text.EncoderFallbackException> <xref:System.Text.DecoderFallbackException> jeśli wstępnie zdefiniowane i klasy nie spełniają twoich <xref:System.Exception> potrzeb, należy wyprowadzić klasę z obiektu wyjątku, takiego jak lub <xref:System.ArgumentException>.

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Wynikające z EncoderFallback lub DecoderFallback

Aby zaimplementować niestandardowe rozwiązanie rezerwowe, należy <xref:System.Text.EncoderFallback> utworzyć klasę, która <xref:System.Text.DecoderFallback> dziedziczy z operacji kodowania i z operacji dekodowania. Wystąpienia tych klas są przekazywane <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> do metody i służyć jako pośrednik między klasy kodowania i implementacji rezerwowej.

Podczas tworzenia niestandardowego rozwiązania rezerwowego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> Właściwość, <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> która zwraca maksymalną możliwą liczbę znaków, które najlepiej dopasowane, zastąpienie lub rezerwowego wyjątku może powrócić do zastąpienia pojedynczego znaku. Dla rezerwowego wyjątku niestandardowego jego wartość wynosi zero.

- Lub <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda, która zwraca <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> niestandardowe lub implementacji. Metoda jest wywoływana przez koder, gdy napotka pierwszy znak, który nie jest w stanie pomyślnie zakodować lub przez dekoder, gdy napotka pierwszy bajt, który nie jest w stanie pomyślnie rozszyfrować.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Wynikające z EncoderFallbackBuffer lub DecoderFallbackBuffer

Aby zaimplementować niestandardowe rozwiązanie rezerwowe, należy również <xref:System.Text.EncoderFallbackBuffer> utworzyć klasę, która <xref:System.Text.DecoderFallbackBuffer> dziedziczy z dla operacji kodowania i z operacji dekodowania. Wystąpienia tych klas są zwracane <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> przez <xref:System.Text.EncoderFallback> metodę <xref:System.Text.DecoderFallback> i klas. Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> jest wywoływana przez koder, gdy napotka pierwszy znak, który nie jest <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> w stanie zakodować, a metoda jest wywoływana przez dekoder, gdy napotka jeden lub więcej bajtów, których nie jest w stanie dekodować. I <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> klasy zapewniają implementację rezerwowej. Każde wystąpienie reprezentuje bufor, który zawiera znaki rezerwowe, które zastąpią znak, który nie może być zakodowany lub sekwencję bajtów, których nie można zdekodować.

Podczas tworzenia niestandardowego rozwiązania rezerwowego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- Lub <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metoda. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>jest wywoływana przez koder, aby zapewnić buforrezerwowy z informacjami o znaku, który nie może zakodować. Ponieważ znak, który ma być zakodowany może być parą zastępczą, ta metoda jest przeciążona. Jedno przeciążenie jest przekazywane znak do zakodowania i jego indeks w ciągu. Drugie przeciążenie jest przekazywane wysokie i niskie surogat wraz z jego indeksu w ciągu. Metoda <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> jest wywoływana przez dekoder, aby zapewnić bufor rezerwowy z informacjami o bajtach, których nie można dekodować. Ta metoda jest przekazywana tablicy bajtów, których nie można dekodować, wraz z indeksem pierwszego bajtu. Metoda rezerwowa powinna `true` zwrócić, jeśli bufor rezerwowy może dostarczyć najlepiej dopasowany lub zastępczy znak lub znaki; w przeciwnym razie `false`powinien powrócić . Dla rezerwowego wyjątku metody rezerwowej należy zgłosić wyjątek.

- Lub <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> metoda, która jest wywoływana wielokrotnie przez koder lub dekoder, aby uzyskać następny znak z buforu rezerwowego. Po zwróceniu wszystkich znaków rezerwowych metoda powinna zwrócić U+0000.

- <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> Właściwość, <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> która zwraca liczbę znaków pozostałych w buforze rezerwowym.

- Lub <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> metoda, która przenosi bieżącą pozycję w buforze rezerwowym do poprzedniego znaku.

- Lub <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> metoda, która ponownie inicjuje bufor rezerwowy.

Jeśli rezerwowa implementacja jest najlepiej dopasowanym rezerwowym lub rezerwowym, klasy pochodzące z <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> również obsługiwać dwa pola wystąpienia prywatnego: dokładną liczbę znaków w buforze; i indeks następnego znaku w buforze do zwrócenia.

### <a name="an-encoderfallback-example"></a>Przykład EncoderFallback

We wcześniejszym przykładzie użyto zastępczego rezerwowego powrotu do zastąpienia znaków Unicode, które nie odpowiadały znakom ASCII gwiazdką (*). W poniższym przykładzie użyto niestandardowej implementacji rezerwowej najlepiej dopasowanej, aby zapewnić lepsze mapowanie znaków innych niż ASCII.

Poniższy kod definiuje klasę `CustomMapper` o nazwie, <xref:System.Text.EncoderFallback> która jest pochodną do obsługi najlepiej dopasowane mapowanie znaków innych niż ASCII. Jego `CreateFallbackBuffer` metoda `CustomMapperFallbackBuffer` zwraca obiekt, <xref:System.Text.EncoderFallbackBuffer> który zapewnia implementacji. Klasa `CustomMapper` używa <xref:System.Collections.Generic.Dictionary%602> obiektu do przechowywania mapowania nieobsługiwanych znaków Unicode (wartość klucza) i odpowiadających im znaków 8-bitowych (które są przechowywane w dwóch kolejnych bajtach w 64-bitowej liczbie całkowitej). Aby udostępnić to mapowanie do `CustomMapper` buforu rezerwowego, wystąpienie `CustomMapperFallbackBuffer` jest przekazywane jako parametr do konstruktora klasy. Ponieważ najdłuższe mapowanie jest ciągiem "INF" dla znaku Unicode `MaxCharCount` U +221E, właściwość zwraca 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Poniższy kod definiuje `CustomMapperFallbackBuffer` klasę, która jest <xref:System.Text.EncoderFallbackBuffer>pochodną . Słownik, który zawiera mapowania najlepiej dopasowanych i `CustomMapper` który jest zdefiniowany w wystąpieniu jest dostępny z jego konstruktora klasy. Jego `Fallback` metoda `true` zwraca, jeśli którykolwiek ze znaków Unicode, które koder ASCII nie może zakodować są zdefiniowane w słowniku mapowania; w przeciwnym `false`razie zwraca . Dla każdego rezerwowego `count` zmienna prywatna wskazuje liczbę znaków, które pozostają `index` do zwrócenia, a `charsToReturn`zmienna prywatna wskazuje pozycję w buforze ciągu, , następnego znaku do zwrócenia.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Poniższy kod następnie tworzy wystąpienia `CustomMapper` obiektu i przekazuje jego <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> wystąpienie do metody. Dane wyjściowe wskazują, że najlepiej dopasowana implementacja rezerwowa pomyślnie obsługuje trzy znaki inne niż ASCII w oryginalnym ciągu.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
