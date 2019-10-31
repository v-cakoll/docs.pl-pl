---
title: Kodowanie znaków w programie .NET
description: Informacje o kodowaniu i dekodowanie znaków w programie .NET.
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
ms.custom: seodec18
ms.openlocfilehash: 3ac5602c32ce0dcfe21e913868faa7ab356e4194
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120601"
---
# <a name="character-encoding-in-net"></a>Kodowanie znaków w programie .NET

Znaki to abstrakcyjne jednostki, które mogą być reprezentowane na wiele różnych sposobów. Kodowanie znaków to system, który par każdy znak w obsługiwanym zestawie znaków z wartością reprezentującą ten znak. Na przykład kod Morse jest kodowaniem znaków, które par każdy znak w alfabecie łaciński z wzorcem kropek i łączników, które są odpowiednie do przesyłania przez linie telegraficzne. Kodowanie znaków dla komputerów par każdy znak w obsługiwanym zestawie znaków o wartości liczbowej, która reprezentuje ten znak. Kodowanie znaków ma dwa odrębne składniki:

- Koder, który tłumaczy sekwencję znaków na sekwencję wartości liczbowych (bajty).

- Dekoder, który tłumaczy sekwencję bajtów na sekwencję znaków.

Kodowanie znaków zawiera opis reguł, za pomocą których koder i dekoder mają działać. Na przykład Klasa <xref:System.Text.UTF8Encoding> opisuje reguły kodowania do i dekodowania z, 8-bitowy format transformacji Unicode (UTF-8), który używa od jednego do czterech bajtów do reprezentowania pojedynczego znaku Unicode. Kodowanie i dekodowanie może również obejmować walidację. Na przykład Klasa <xref:System.Text.UnicodeEncoding> sprawdza wszystkie surogaty, aby upewnić się, że stanowią poprawne pary surogatów. (Para zastępcza składa się z znaku z punktem kodu, który mieści się w zakresie od U + D800 do U + DBFF, po którym następuje znak z punktem kodu, który mieści się w zakresie od U + DC00 do U + DFFF).  Strategia rezerwowa określa, jak koder obsługuje nieprawidłowe znaki lub jak dekoder obsługuje nieprawidłowe bajty.

> [!WARNING]
> Klasy kodowania .NET umożliwiają przechowywanie i konwertowanie danych znakowych. Nie powinny być używane do przechowywania danych binarnych w postaci ciągów. W zależności od użytego kodowania Konwertowanie danych binarnych na format ciągu z klasami kodowania może spowodować nieoczekiwane zachowanie i generować niedokładne lub uszkodzone dane. Aby przekonwertować dane binarne na postać ciągu, użyj metody <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>.

Platforma .NET używa kodowania UTF-16 (reprezentowanego przez klasę <xref:System.Text.UnicodeEncoding>) do reprezentowania znaków i ciągów. Aplikacje przeznaczone dla środowiska uruchomieniowego języka wspólnego używają koderów do mapowania reprezentacji znaków Unicode obsługiwanych przez środowisko uruchomieniowe języka wspólnego do innych schematów kodowania. Używają dekoderów do mapowania znaków z kodowania innych niż Unicode na Unicode.

Ten temat zawiera następujące sekcje:

- [Kodowanie na platformie .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)

- [Wybieranie klasy kodowania](../../../docs/standard/base-types/character-encoding.md#Selecting)

- [Używanie obiektu kodowania](../../../docs/standard/base-types/character-encoding.md#Using)

- [Wybór strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)

- [Implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom)

<a name="Encodings"></a>

## <a name="encodings-in-net"></a>Kodowanie na platformie .NET

Wszystkie klasy kodowania znaków w programie .NET dziedziczą z klasy <xref:System.Text.Encoding?displayProperty=nameWithType>, która jest klasą abstrakcyjną, która definiuje funkcje wspólne dla wszystkich kodowań znaków. Aby uzyskać dostęp do poszczególnych obiektów kodowania wdrożonych w programie .NET, wykonaj następujące czynności:

- Użyj właściwości statycznych klasy <xref:System.Text.Encoding>, które zwracają obiekty reprezentujące standardowe kodowanie znaków dostępne w programie .NET (ASCII, UTF-7, UTF-8, UTF-16 i UTF-32). Na przykład właściwość <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.UnicodeEncoding>. Każdy obiekt używa powrotu zamiennej do obsługi ciągów, których nie można kodować, i bajtów, których nie można zdekodować. (Aby uzyskać więcej informacji, zobacz sekcję [Fallback wymiany](../../../docs/standard/base-types/character-encoding.md#Replacement) ).

- Wywołaj konstruktora klasy kodowania. W ten sposób można utworzyć wystąpienie obiektów dla kodowania ASCII, UTF-7, UTF-8, UTF-16 i UTF-32. Domyślnie każdy obiekt używa powrotu zamiennej do obsługi ciągów, których nie można kodować, i bajtów, których nie można zdekodować, ale można określić, że zamiast tego ma zostać zgłoszony wyjątek. (Aby uzyskać więcej informacji, zobacz sekcje rezerwowe [powrotu](../../../docs/standard/base-types/character-encoding.md#Replacement) i powrotu [wyjątku](../../../docs/standard/base-types/character-encoding.md#Exception) ).

- Wywołaj konstruktora <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> i przekaż go do liczby całkowitej, która reprezentuje kodowanie. Obiekty kodowania standardowego używają rezerw zamiennych, a strony kodowej i dwubajtowego zestawu znaków (DBCS) używają najlepiej dopasowanej rezerwy do obsługi ciągów, których nie można kodować, i bajtów, których nie można zdekodować. (Aby uzyskać więcej informacji, zobacz sekcję [najlepiej pasującą do rezerwy](../../../docs/standard/base-types/character-encoding.md#BestFit) ).

- Wywołaj metodę <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>, która zwraca dowolne kodowanie standardowe, strony kodowej lub DBCS dostępne w programie .NET. Przeciążenia umożliwiają określenie obiektu rezerwowego dla kodera i dekodera.

> [!NOTE]
> Standard Unicode przypisuje punkt kodu (numer) i nazwę każdego znaku w każdym obsługiwanym skrypcie. Na przykład znak "A" jest reprezentowany przez punkt kodu U + 0041 i nazwę "Wielka litera A". Kodowanie Unicode Transformation format (UTF) definiuje sposoby kodowania tego punktu kodu do sekwencji co najmniej jednego bajtu. Schemat kodowania Unicode upraszcza tworzenie aplikacji gotowych do zastosowania na całym świecie, ponieważ umożliwia ona używanie znaków z dowolnego zestawu znaków, które mają być reprezentowane w jednym kodowaniu. Deweloperzy aplikacji nie muszą już śledzić schematu kodowania, który był używany do tworzenia znaków dla określonego języka lub systemu pisania, a dane mogą być współużytkowane między systemami w skali międzynarodowej bez uszkodzenia.
>
> Platforma .NET obsługuje trzy kodowania zdefiniowane przez standard Unicode: UTF-8, UTF-16 i UTF-32. Aby uzyskać więcej informacji, zobacz Standard Unicode na [stronie głównej Unicode](https://www.unicode.org/).

Możesz pobrać informacje o wszystkich kodowaniach dostępnych w programie .NET, wywołując metodę <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType>. Platforma .NET obsługuje systemy kodowania znaków wymienione w poniższej tabeli.

|Kody|Class|Opis|Zalety/wady|
|--------------|-----------|-----------------|-------------------------------|
|ASCII|<xref:System.Text.ASCIIEncoding>|Koduje ograniczony zakres znaków przy użyciu krótszych siedmiu bitów bajtu.|Ponieważ to kodowanie obsługuje tylko wartości znakowe z U + 0000 za pośrednictwem U + 007F, w większości przypadków nie jest to wystarczające dla międzynarodowych aplikacji.|
|UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaki jako sekwencje 7-bitowego znaków ASCII. Znaki Unicode inne niż ASCII są reprezentowane przez sekwencję ucieczki znaków ASCII.|UTF-7 obsługuje protokoły, takie jak protokoły poczty e-mail i grupy dyskusyjne. Jednak kodowanie UTF-7 nie jest szczególnie bezpieczne ani niezawodne. W niektórych przypadkach zmiana jednego bitu może radykalnie zmienić interpretację całego ciągu UTF-7. W innych przypadkach, różne ciągi UTF-7 mogą kodować ten sam tekst. W przypadku sekwencji, które zawierają znaki inne niż ASCII, UTF-7 wymaga więcej miejsca niż UTF-8, a Kodowanie/dekodowanie jest wolniejsze. W związku z tym należy zamiast tego użyć formatu UTF-8, jeśli jest to możliwe.|
|UTF-8|<xref:System.Text.UTF8Encoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencję od 1 do 4 bajtów.|UTF-8 obsługuje 8-bitowe rozmiary danych i współpracuje z wieloma istniejącymi systemami operacyjnymi. W przypadku zakresu znaków ASCII UTF-8 jest taka sama jak kodowanie ASCII i umożliwia szerszego zestawu znaków. Jednak w przypadku skryptów w języku chińskim-japońskim (CJK) UTF-8 może wymagać trzech bajtów dla każdego znaku, co może powodować większe rozmiary danych niż UTF-16. Należy pamiętać, że czasami ilość danych ASCII, takich jak tagi HTML, uzasadnia zwiększony rozmiar dla zakresu CJK.|
|UTF-16|<xref:System.Text.UnicodeEncoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencję jednej lub 2 16-bitowej liczby całkowitej. Najpopularniejsze znaki Unicode wymagają tylko jednego punktu kodu UTF-16, chociaż znaki dodatkowe Unicode (U + 10000 i nowsze) wymagają dwóch zastępczych punktów kodowych w formacie UTF-16. Obsługiwane są zarówno kolejność bajtów little-endian, jak i big-endian.|Kodowanie UTF-16 jest używane przez środowisko uruchomieniowe języka wspólnego do reprezentowania wartości <xref:System.Char> i <xref:System.String>, które są używane przez system operacyjny Windows do reprezentowania wartości `WCHAR`.|
|UTF-32|<xref:System.Text.UTF32Encoding>|Reprezentuje każdy punkt kodu Unicode jako 32-bitową liczbę całkowitą. Obsługiwane są zarówno kolejność bajtów little-endian, jak i big-endian.|Kodowanie UTF-32 jest używane, gdy aplikacje chcą uniknąć zachowania surogatu kodu UTF-16 w systemach operacyjnych, w których zakodowane miejsce jest zbyt ważne. Pojedyncze glify renderowane na ekranie mogą wciąż być kodowane przy użyciu więcej niż jednego znaku UTF-32.|
|Kodowanie ANSI/ISO||Zapewnia obsługę różnych stron kodowych. W systemach operacyjnych Windows strony kodowe są używane do obsługi określonego języka lub grupy języków. W przypadku tabeli zawierającej listę stron kodowych obsługiwanych przez platformę .NET zapoznaj się z klasą <xref:System.Text.Encoding>. Można pobrać obiekt kodowania dla konkretnej strony kodowej, wywołując metodę <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType>.|Strona kodowa zawiera 256 punktów kodu i jest zależna od zera. W większości stron kodowych od 0 do 127 reprezentuje zestaw znaków ASCII, a punkty kodów 128 przez 255 różnią się znacząco między stronami kodowymi. Na przykład strona kodowa 1252 zawiera znaki dla systemów pisania łacińskiego, w tym angielski, niemiecki i francuski. Ostatnie 128 punktów kodowych na stronie kodowej 1252 zawierają znaki akcentu. Strona kodowa 1253 zawiera kody znaków, które są wymagane w greckim systemie pisania. Ostatnie 128 punktów kodu na stronie kodowej 1253 zawierają znaki greckie. W związku z tym aplikacja, która opiera się na stronach kodowych ANSI, nie może przechowywać greckich i niemieckich w tym samym strumieniu tekstowym, chyba że zawiera identyfikator, który wskazuje na stronę kodową, do której się odwołuje.|
|Kodowanie zestawów znaków dwubajtowych (DBCS)||Obsługuje języki, takie jak chiński, japoński i koreański, które zawierają więcej niż 256 znaków. W DBCS para punktów kodu (dwubajtowy) reprezentuje każdy znak. Właściwość <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> zwraca `false` dla kodowań DBCS. Można pobrać obiekt kodowania dla określonego zestawu DBCS, wywołując metodę <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType>.|W DBCS para punktów kodu (dwubajtowy) reprezentuje każdy znak. Gdy aplikacja obsługuje dane DBCS, pierwszy bajt znaku dwubajtowego (bajt wiodący) jest przetwarzany w połączeniu z bajtem końcowym, który natychmiast następuje po nim. Ponieważ pojedyncza para dwubajtowych punktów kodowych może reprezentować różne znaki w zależności od strony kodowej, schemat ten nadal nie pozwala na połączenie dwóch języków, takich jak japoński i chiński, w tym samym strumieniu danych.|

Te kodowania umożliwiają współdziałanie z znakami Unicode, a także z kodowaniem najczęściej używanym w starszych aplikacjach. Ponadto można utworzyć niestandardowe kodowanie przez zdefiniowanie klasy, która pochodzi od <xref:System.Text.Encoding> i przesłanianie jej elementów członkowskich.

### <a name="platform-notes-net-core"></a>Uwagi dotyczące platformy: .NET Core

Domyślnie platforma .NET Core nie udostępnia żadnych kodowań stron kodowych innych niż strona kodowa 28591 i kodowanie Unicode, takie jak UTF-8 i UTF-16. Można jednak dodać kodowanie stron kodowych Znalezione w standardowych aplikacjach systemu Windows, które są przeznaczone dla platformy .NET dla aplikacji. Aby uzyskać pełne informacje, zobacz temat <xref:System.Text.CodePagesEncodingProvider>.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Wybieranie klasy kodowania

Jeśli masz możliwość wybrania kodowania, które ma być używane przez aplikację, użyj kodowania Unicode, najlepiej <xref:System.Text.UTF8Encoding> lub <xref:System.Text.UnicodeEncoding>. (Platforma .NET obsługuje także trzecie kodowanie Unicode, <xref:System.Text.UTF32Encoding>.)

Jeśli planujesz użycie kodowania ASCII (<xref:System.Text.ASCIIEncoding>), wybierz <xref:System.Text.UTF8Encoding> zamiast tego. Dwa kodowania są identyczne dla zestawu znaków ASCII, ale <xref:System.Text.UTF8Encoding> ma następujące zalety:

- Może reprezentować każdy znak Unicode, natomiast <xref:System.Text.ASCIIEncoding> obsługuje tylko wartości znaków Unicode między U + 0000 i U + 007F.

- Zapewnia wykrywanie błędów i lepsze zabezpieczenia.

- Został dostrojony tak szybko, jak to możliwe i powinien być szybszy niż inne kodowanie. Nawet w przypadku zawartości, która jest całkowicie ASCII, operacje wykonywane przy użyciu <xref:System.Text.UTF8Encoding> są szybsze niż operacje wykonywane z <xref:System.Text.ASCIIEncoding>.

Należy rozważyć użycie <xref:System.Text.ASCIIEncoding> tylko w przypadku starszych aplikacji. Jednak nawet w przypadku starszych aplikacji <xref:System.Text.UTF8Encoding> może być lepszym wyborem z następujących powodów (przy założeniu ustawień domyślnych):

- Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje ją z <xref:System.Text.ASCIIEncoding>, każdy znak inny niż ASCII jest kodowany jako znak zapytania (?). Jeśli aplikacja następnie dekoduje te dane, informacje zostaną utracone.

- Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje ją z <xref:System.Text.UTF8Encoding>, wynik wydaje się niezrozumiały, jeśli jest interpretowany jako ASCII. Jeśli jednak aplikacja używa dekodera UTF-8, aby zdekodować te dane, dane są wykonywane pomyślnie.

W aplikacji sieci Web znaki wysyłane do klienta w odpowiedzi na żądanie sieci Web powinny odzwierciedlać kodowanie używane na kliencie. W większości przypadków należy ustawić właściwość <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> na wartość zwracaną przez właściwość <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType>, aby wyświetlić tekst w kodowaniu, którego oczekuje użytkownik.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Używanie obiektu kodowania

Koder konwertuje ciąg znaków (najczęściej są to znaki Unicode) na jego odpowiednik liczbowy (Byte). Można na przykład użyć kodera ASCII do przekonwertowania znaków Unicode na ASCII, aby można było je wyświetlić w konsoli. Aby przeprowadzić konwersję, należy wywołać metodę <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType>. Jeśli chcesz określić liczbę bajtów potrzebnych do przechowywania zakodowanych znaków przed wykonaniem kodowania, możesz wywołać metodę <xref:System.Text.Encoding.GetByteCount%2A>.

W poniższym przykładzie zastosowano tablicę jednobajtową do kodowania ciągów w dwóch oddzielnych operacjach. Zachowuje indeks wskazujący pozycję początkową w tablicy bajtów dla następnego zestawu bajtów zakodowanych w formacie ASCII. Wywołuje metodę <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType>, aby upewnić się, że tablica bajtów jest wystarczająco duża, aby pomieścić zakodowany ciąg. Następnie wywołuje metodę <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType>, aby zakodować znaki w ciągu.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekoder konwertuje tablicę bajtową, która odzwierciedla określony kodowanie znaków w zestawie znaków, w tablicy znaków lub w ciągu. Aby zdekodować tablicę bajtową do tablicy znaków, należy wywołać metodę <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType>. Aby zdekodować tablicę bajtową do ciągu, należy wywołać metodę <xref:System.Text.Encoding.GetString%2A>. Jeśli chcesz określić liczbę znaków potrzebną do przechowywania zdekodowanych bajtów przed wykonaniem dekodowania, możesz wywołać metodę <xref:System.Text.Encoding.GetCharCount%2A>.

Poniższy przykład koduje trzy ciągi, a następnie dekoduje je w postaci pojedynczej tablicy znaków. Zachowuje indeks wskazujący pozycję początkową w tablicy znaków dla następnego zestawu zdekodowanych znaków. Wywołuje metodę <xref:System.Text.ASCIIEncoding.GetCharCount%2A>, aby upewnić się, że tablica znaków jest wystarczająco duża, aby pomieścić wszystkie znaki zdekodowane. Następnie wywołuje metodę <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType>, aby zdekodować tablicę bajtów.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kodowania i dekodowania klasy pochodnej <xref:System.Text.Encoding> są przeznaczone do pracy nad kompletnym zestawem danych; oznacza to, że wszystkie dane, które mają być kodowane lub dekodowane, są dostarczane w jednym wywołaniu metody. Jednak w niektórych przypadkach dane są dostępne w strumieniu, a dane, które mają być kodowane lub dekodowane, mogą być dostępne tylko z oddzielnych operacji odczytu. Wymaga to kodowania lub dekodowania operacji, aby zapamiętać każdy zapisany stan w poprzednim wywołaniu. Metody klas pochodnych <xref:System.Text.Encoder> i <xref:System.Text.Decoder> mogą obsługiwać operacje kodowania i dekodowania obejmujące wiele wywołań metod.

Obiekt <xref:System.Text.Encoder> dla określonego kodowania jest dostępny z właściwości <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> tego kodowania. Obiekt <xref:System.Text.Decoder> dla określonego kodowania jest dostępny z właściwości <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> tego kodowania. W przypadku operacji dekodowania należy zwrócić uwagę, że klasy pochodne <xref:System.Text.Decoder> zawierają metodę <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType>, ale nie mają metody odpowiadającej <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.

Poniższy przykład ilustruje różnicę między użyciem metod <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> i <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> do dekodowania tablicy bajtowej Unicode. Przykład koduje ciąg, który zawiera znaki Unicode do pliku, a następnie używa dwóch metod dekodowania do zdekodowania ich dziesięć bajtów jednocześnie. Ponieważ para dwuskładnikowa występuje w dziesiątych i jedenastych bajtach, jest dekodowane w oddzielnych wywołaniach metod. Ponieważ dane wyjściowe są wyświetlane, Metoda <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> nie jest w stanie poprawnie zdekodować bajtów i zamiast tego zastępuje je literałem U + FFFD (znak ZASTĘPCZy). Z drugiej strony Metoda <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> może pomyślnie zdekodować tablicę bajtową, aby uzyskać oryginalny ciąg.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Wybór strategii rezerwowej

Gdy metoda próbuje zakodować lub zdekodować znak, ale nie istnieje żadne mapowanie, musi zaimplementować strategię rezerwową, która określa sposób obsługi mapowania zakończonego niepowodzeniem. Istnieją trzy typy strategii powrotu:

- Dopasowanie najlepszego dopasowania

- Alternatywa wymiany

- Rezerwa wyjątku

> [!IMPORTANT]
> Najczęstsze problemy w operacjach kodowania są wykonywane, gdy znak Unicode nie może zostać zmapowany na konkretne kodowanie strony kodowej. Najczęstsze problemy związane z dekodowaniem są wykonywane, gdy nieprawidłowe sekwencje bajtów nie mogą być przetłumaczone na prawidłowe znaki Unicode. Z tego względu należy wiedzieć, która strategia rezerwowa używa danego obiektu kodowania. Zawsze, gdy jest to możliwe, należy określić strategię rezerwową używaną przez obiekt kodowania podczas tworzenia wystąpienia obiektu.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Dopasowanie najlepszego dopasowania

Gdy znak nie ma dokładnego dopasowania w kodowaniu docelowym, koder może próbować zmapować go do podobnego znaku. (Najlepszym dopasowaniem jest raczej kodowanie, a nie problem z dekodowaniem. Istnieje kilka stron kodowych, które zawierają znaki, których nie można pomyślnie zmapować na Unicode.) Najlepszym dopasowaniem jest wartość domyślna dla kodowania strony kodowej i dwubajtowego zestawu znaków, które są pobierane przez <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> i <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> przeciążenia.

> [!NOTE]
> Teoretycznie klasy kodowania Unicode zapewniane w .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>i <xref:System.Text.UTF32Encoding>) obsługują każdy znak w każdym zestawie znaków, dzięki czemu mogą one służyć do eliminowania najbardziej pasujących problemów powrotu.

Najlepiej dopasowane strategie różnią się w zależności od stron kodowych. Na przykład w przypadku niektórych stron kodowych znaki łacińskie o pełnej szerokości są mapowane na bardziej popularne znaki łacińskie połówkowej szerokości. W przypadku innych stron kodowych mapowanie nie jest wykonywane. Nawet w ramach agresywnej strategii najlepiej dopasowanej nie ma żadnych znaków w przypadku niektórych kodowań. Na przykład, ideograph chiński nie ma uzasadnionego mapowania na stronę kodową 1252. W takim przypadku używany jest ciąg zastępczy. Domyślnie ten ciąg jest tylko pojedynczym ZNAKiem zapytania (U + 003F).

> [!NOTE]
> Strategie najlepiej dopasowane nie są udokumentowane szczegółowo. Jednak kilka stron kodowych są udokumentowane w witrynie sieci Web [konsorcjum Unicode](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) . Aby uzyskać opis sposobu interpretacji plików mapowania, zapoznaj się z plikiem **README. txt** w tym folderze.

Poniższy przykład używa strony kodowej 1252 (strona kodowa systemu Windows dla języków zachodnich Europy) do zilustrowania najlepszego mapowania i jego wad. Metoda <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> służy do pobierania obiektu kodowania dla strony kodowej 1252. Domyślnie używa mapowania najlepszego dopasowania dla znaków Unicode, które nie są obsługiwane. Przykład tworzy wystąpienie ciągu, który zawiera trzy znaki inne niż ASCII — WYRÓŻNIONe Wielka litera S (U + 24C8), indeks GÓRNy 5 (U + 2075) i NIESKOŃCZONość (U + 221E) — rozdzielone spacjami. Jako dane wyjściowe z przykładu pokazują, gdy ciąg jest zakodowany, trzy oryginalne znaki niebędące znakami spacji są zastępowane na podstawie znaku zapytania (U + 003F), cyfry pięć (U + 0035) i cyfry osiem (U + 0038). CYFRa osiem to szczególnie słabe zastąpienie dla nieobsługiwanego znaku NIESKOŃCZONości, a znak zapytania wskazuje, że dla oryginalnego znaku nie jest dostępne żadne mapowanie.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Mapowanie najlepiej dopasowane jest zachowaniem domyślnym dla obiektu <xref:System.Text.Encoding>, który koduje dane Unicode na dane strony kodowej, a istnieją starsze aplikacje, które korzystają z tego zachowania. Jednak większość nowych aplikacji powinna unikać optymalnego zachowania ze względów bezpieczeństwa. Na przykład aplikacje nie powinny umieszczać nazwy domeny za pomocą najlepszego dopasowania kodowania.

> [!NOTE]
> Możesz również zaimplementować niestandardowe mapowanie rezerwy najlepszego dopasowania dla kodowania. Aby uzyskać więcej informacji, zobacz sekcję [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) .

Jeśli jest to wartość domyślna dla obiektu Encoding, można wybrać inną strategię rezerwową podczas pobierania <xref:System.Text.Encoding> obiektu przez wywołanie <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> lub przeciążenia <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType>. Poniższa sekcja zawiera przykład zastępujący każdy znak, którego nie można zamapować na stronę kodową 1252 przy użyciu gwiazdki (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Alternatywa wymiany

Gdy znak nie ma dokładnego dopasowania w schemacie docelowym, ale nie ma odpowiedniego znaku, do którego można zamapować, aplikacja może określić znak zastępczy lub ciąg. Jest to domyślne zachowanie dla dekodera Unicode, który zastępuje dowolną dwubajtową sekwencję, której nie można zdekodować przy użyciu REPLACEMENT_CHARACTER (U + FFFD). Jest to również domyślne zachowanie klasy <xref:System.Text.ASCIIEncoding>, która zastępuje każdy znak, którego nie można kodować ani zdekodować ze znakiem zapytania. Poniższy przykład ilustruje zastąpienie znaków w ciągu Unicode z poprzedniego przykładu. Ponieważ dane wyjściowe są wyświetlane, każdy znak, którego nie można zdekodować do wartości bajtowej ASCII, jest zastępowany przez 0x3F, który jest kodem ASCII dla znaku zapytania.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

Platforma .NET zawiera klasy <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallback>, które zastępują ciąg zastępczy, jeśli znak nie mapuje się dokładnie w operacji kodowania lub dekodowania. Domyślnie ten ciąg zamienny jest znakiem zapytania, ale można wywołać przeciążenie konstruktora klasy w celu wybrania innego ciągu. Zazwyczaj ciąg zamienny jest pojedynczym znakiem, chociaż nie jest to wymagane. Poniższy przykład zmienia zachowanie kodera 1252 strony kodowej przez utworzenie wystąpienia obiektu <xref:System.Text.EncoderReplacementFallback>, który używa gwiazdki (*) jako ciągu zastępczego.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Można również zaimplementować klasę zastępczą dla kodowania. Aby uzyskać więcej informacji, zobacz sekcję [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) .

Oprócz znaku zapytania (U + 003F) znak ZASTĘPCZy Unicode (U + FFFD) jest często używany jako ciąg zamienny, szczególnie w przypadku dekodowania sekwencji bajtów, których nie można pomyślnie przetłumaczyć na znaki Unicode. Można jednak wybrać dowolny ciąg zamienny, który może zawierać wiele znaków.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Rezerwa wyjątku

Zamiast podawania najlepszego dopasowania lub ciągu zamiennego, koder może zgłosić <xref:System.Text.EncoderFallbackException>, jeśli nie jest w stanie zakodować zestawu znaków, a dekoder może zgłosić <xref:System.Text.DecoderFallbackException>, jeśli nie można zdekodować tablicy bajtów. Aby zgłosić wyjątek w operacjach kodowania i dekodowania, należy podać obiekt <xref:System.Text.EncoderExceptionFallback> i obiekt <xref:System.Text.DecoderExceptionFallback> odpowiednio do metody <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType>. Poniższy przykład ilustruje rezerwę wyjątku z klasą <xref:System.Text.ASCIIEncoding>.

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Można również zaimplementować niestandardową procedurę obsługi wyjątków dla operacji kodowania. Aby uzyskać więcej informacji, zobacz sekcję [implementowanie niestandardowej strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#Custom) .

Obiekty <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> zawierają następujące informacje o stanie, który spowodował wyjątek:

- Obiekt <xref:System.Text.EncoderFallbackException> zawiera metodę <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A>, która wskazuje, czy znak lub znaki, których nie można zakodować, reprezentują nieznaną parę surogatu (w tym przypadku metoda zwraca `true`) lub nieznany pojedynczy znak (w tym przypadku Metoda zwraca `false`). Znaki w parze dwuskładnikowej są dostępne we właściwościach <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> i <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType>. Nieznany pojedynczy znak jest dostępny z właściwości <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType>. Właściwość <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje pozycję w ciągu, w którym znaleziono pierwszy znak, który nie może zostać zakodowany.

- Obiekt <xref:System.Text.DecoderFallbackException> zawiera właściwość <xref:System.Text.DecoderFallbackException.BytesUnknown%2A>, która zwraca tablicę bajtów, których nie można zdekodować. Właściwość <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> wskazuje pozycję początkową nieznanych bajtów.

Chociaż obiekty <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> zapewniają odpowiednie informacje diagnostyczne o wyjątku, nie zapewniają dostępu do buforu kodowania lub dekodowania. W związku z tym nie zezwalają na zamienianie lub korygowanie nieprawidłowych danych w ramach metody kodowania lub dekodowania.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Implementowanie niestandardowej strategii rezerwowej

Oprócz najlepszego mapowania, które jest implementowane wewnętrznie przez strony kodowe, platforma .NET zawiera następujące klasy do implementowania strategii rezerwowej:

- Użyj <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.EncoderReplacementFallbackBuffer>, aby zastąpić znaki w operacjach kodowania.

- Użyj <xref:System.Text.DecoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallbackBuffer>, aby zamienić znaki podczas dekodowania operacji.

- Użyj <xref:System.Text.EncoderExceptionFallback> i <xref:System.Text.EncoderExceptionFallbackBuffer>, aby zgłosić <xref:System.Text.EncoderFallbackException>, gdy nie można zakodować znaku.

- Użyj <xref:System.Text.DecoderExceptionFallback> i <xref:System.Text.DecoderExceptionFallbackBuffer>, aby zgłosić <xref:System.Text.DecoderFallbackException>, gdy nie można zdekodować znaku.

Ponadto można zaimplementować niestandardowe rozwiązanie, które używa najlepszego dopasowania powrotu, powrotu zamiennej lub powrotu do wyjątków, wykonując następujące czynności:

1. Utwórz klasę z <xref:System.Text.EncoderFallback> na potrzeby operacji kodowania oraz z <xref:System.Text.DecoderFallback> do dekodowania operacji.

2. Utwórz klasę z <xref:System.Text.EncoderFallbackBuffer> na potrzeby operacji kodowania oraz z <xref:System.Text.DecoderFallbackBuffer> do dekodowania operacji.

3. W przypadku powrotu wyjątku, jeśli wstępnie zdefiniowane <xref:System.Text.EncoderFallbackException> i klasy <xref:System.Text.DecoderFallbackException> nie spełniają Twoich potrzeb, należy utworzyć klasę z obiektu wyjątku, takiego jak <xref:System.Exception> lub <xref:System.ArgumentException>.

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Wyprowadzanie z EncoderFallback lub DecoderFallback

Aby zaimplementować niestandardowe rozwiązanie alternatywne, należy utworzyć klasę, która dziedziczy po <xref:System.Text.EncoderFallback> na potrzeby operacji kodowania oraz z <xref:System.Text.DecoderFallback> do dekodowania operacji. Wystąpienia tych klas są przesyłane do metody <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> i służą jako pośrednik między klasą kodowania a implementacją rezerwową.

W przypadku tworzenia niestandardowego rozwiązania alternatywnego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- Właściwość <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType>, która zwraca maksymalną możliwą liczbę znaków, które można zwrócić, aby zamienić pojedynczy znak. W przypadku niestandardowego powrotu wyjątku jego wartość wynosi zero.

- Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType>, która zwraca <xref:System.Text.EncoderFallbackBuffer> niestandardowe lub implementację <xref:System.Text.DecoderFallbackBuffer>. Metoda jest wywoływana przez koder, gdy napotka pierwszy znak, który nie może zostać pomyślnie zakodowany, lub przez dekoder w przypadku napotkania pierwszego bajtu, którego nie można pomyślnie zdekodować.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Wyprowadzanie z EncoderFallbackBuffer lub DecoderFallbackBuffer

Aby zaimplementować niestandardowe rozwiązanie alternatywne, należy również utworzyć klasę, która dziedziczy po <xref:System.Text.EncoderFallbackBuffer> na potrzeby operacji kodowania, oraz z <xref:System.Text.DecoderFallbackBuffer> do dekodowania operacji. Wystąpienia tych klas są zwracane przez metodę <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> klas <xref:System.Text.EncoderFallback> i <xref:System.Text.DecoderFallback>. Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> jest wywoływana przez koder, gdy napotka pierwszy znak, który nie jest w stanie kodować, a metoda <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> jest wywoływana przez dekoder, gdy napotka jeden lub więcej bajtów, których nie można zdekodować. Klasy <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> zapewniają implementację rezerwową. Każde wystąpienie reprezentuje bufor, który zawiera znaki rezerwowe, które zastąpią znak, którego nie można zakodować lub nie można zdekodować sekwencji bajtów.

W przypadku tworzenia niestandardowego rozwiązania alternatywnego dla kodera lub dekodera należy zaimplementować następujące elementy członkowskie:

- Metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> jest wywoływana przez koder, aby zapewnić bufor rezerwowy z informacjami o znaku, którego nie może kodować. Ponieważ znak, który ma być zakodowany, może być parą zastępczą, ta metoda jest przeciążona. Jedno Przeciążenie jest przekazanie znaku, który ma zostać zakodowany i jego indeks w ciągu. Drugie Przeciążenie jest przenoszone z górnego i niskiego surogatu wraz z jego indeksem w ciągu. Metoda <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> jest wywoływana przez dekoder w celu zapewnienia bufora rezerwowego informacjami o bajtach, których nie można zdekodować. Ta metoda jest przenoszona tablicą bajtów, której nie można zdekodować, wraz z indeksem pierwszego bajtu. Metoda rezerwowa powinna zwracać `true`, jeśli bufor rezerwowy może dostarczyć najlepiej pasujący lub zastępczy znak lub znaki; w przeciwnym razie powinna zwrócić `false`. W przypadku powrotu wyjątku Metoda rezerwowa powinna zgłosić wyjątek.

- Metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType>, która jest wywoływana wielokrotnie przez koder lub dekoder w celu uzyskania następnego znaku z buforu rezerwowego. Gdy wszystkie znaki powrotu zostały zwrócone, metoda powinna zwrócić U + 0000.

- Właściwość <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType>, która zwraca liczbę znaków pozostałych w buforze rezerwowym.

- Metoda <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType>, która przenosi bieżącą pozycję w buforze rezerwowym do poprzedniego znaku.

- Metoda <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> lub <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType>, która ponownie inicjuje bufor rezerwowy.

Jeśli implementacja powrotu jest najlepszym dopasowaną rezerwą lub alternatywą zamienną, klasy pochodne <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> również utrzymują dwa pola wystąpienia prywatnego: dokładną liczbę znaków w buforze; i indeks następnego znaku w buforze, który ma zostać zwrócony.

### <a name="an-encoderfallback-example"></a>Przykład EncoderFallback

W poprzednim przykładzie użyto powrotu zamiennej zastępującej znaki Unicode, które nie odpowiadają znakom ASCII z gwiazdką (*). W poniższym przykładzie zastosowano niestandardową implementację rezerwową najlepiej w celu zapewnienia lepszego mapowania znaków innych niż ASCII.

Poniższy kod definiuje klasę o nazwie `CustomMapper`, która pochodzi od <xref:System.Text.EncoderFallback> do obsługi najlepszego mapowania znaków innych niż ASCII. Metoda `CreateFallbackBuffer` zwraca obiekt `CustomMapperFallbackBuffer`, który zapewnia implementację <xref:System.Text.EncoderFallbackBuffer>. Klasa `CustomMapper` używa obiektu <xref:System.Collections.Generic.Dictionary%602> do przechowywania mapowań nieobsługiwanych znaków Unicode (wartość klucza) i odpowiadających im znaków 8-bitowych (które są przechowywane w dwóch kolejnych bajtach w 64-bitowej liczbie całkowitej). Aby to mapowanie było dostępne dla buforu rezerwowego, wystąpienie `CustomMapper` zostanie przesłane jako parametr do konstruktora klasy `CustomMapperFallbackBuffer`. Ponieważ najdłuższym mapowaniem jest ciąg "INF" dla znaku Unicode U + 221E, właściwość `MaxCharCount` zwraca wartość 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Poniższy kod definiuje klasę `CustomMapperFallbackBuffer`, która pochodzi od <xref:System.Text.EncoderFallbackBuffer>. Słownik zawierający najlepsze mapowania i zdefiniowany w wystąpieniu `CustomMapper` jest dostępny z konstruktora klasy. Metoda `Fallback` zwraca `true`, jeśli którykolwiek ze znaków Unicode, które nie mogą kodować kodera ASCII, jest zdefiniowany w słowniku mapowania; w przeciwnym razie zwraca `false`. Dla każdego powrotu, prywatna zmienna `count` wskazuje liczbę znaków, które pozostały do zwrócenia, a prywatna zmienna `index` wskazuje pozycję w buforze ciągów, `charsToReturn`, od następnego znaku do zwrócenia.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Poniższy kod powoduje utworzenie wystąpienia obiektu `CustomMapper` i przekazanie jego wystąpienia do metody <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType>. Dane wyjściowe wskazują, że Najlepsza zgodność implementacja rezerwy pomyślnie obsługuje trzy znaki inne niż ASCII w oryginalnym ciągu.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
