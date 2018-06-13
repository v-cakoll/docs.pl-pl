---
title: Globalizacja
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eb57aa0d6645958691c0003b07db6e8bb844fc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579577"
---
# <a name="globalization"></a>Globalizacja
Globalizacja obejmuje projektowanie i tworzenie aplikacji gotowe, który obsługuje interfejsy zlokalizowanych i dane regionalne dla użytkowników w wielu kultur. Przed rozpoczęciem fazy projektowania, należy określić, które kultur aplikacji będzie obsługiwać. Mimo że aplikacja jest przeznaczony dla jednego kultury lub regionu, jako jego domyślny, można projektować i zapisać go tak, aby łatwo może zostać rozszerzony do użytkowników w innych kultur lub regionach.  
  
 Jako deweloperów wszystkie mamy założenia dotyczące interfejsów użytkownika i dane, które są tworzone przez naszych kultur. Na przykład dla programisty anglojęzycznego w Stanach Zjednoczonych serializacji danych daty i godziny jako ciąg w formacie `MM/dd/yyyy hh:mm:ss` wydaje się doskonale uzasadnione. Jednak podczas deserializacji tego ciągu w systemie w inną kulturę prawdopodobnie throw <xref:System.FormatException> wyjątku lub produktu niedokładne dane. Globalizacja umożliwia firmie Microsoft w celu identyfikowania takich założeń specyficzne dla kultury i upewnij się, że nie wpływają na projekt lub kod naszej aplikacji.  
  
 W poniższych sekcjach omówiono niektóre poważne problemy, które należy wziąć pod uwagę i najlepszych praktyk, które można wykonać podczas obsługi ciągów, daty i wartości czasu i wartości liczbowe w uniwersalnych aplikacji.  
  
-   [Obsługa ciągów](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Korzystanie z Unicode](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Pliki zasobów](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Wyszukiwanie i porównywanie ciągów ](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Testowanie pod kątem równości ciągów](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Kolejność i sortowanie ciągów ](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Unikaj ciągów](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Obsługa daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Utrwalanie daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Wyświetlanie daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Serializacja i świadomości strefy czasowej](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Data i czas arytmetyczne](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Obsługa wartości liczbowych](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Wyświetlanie wartości liczbowych](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Przechowywanie wartości liczbowych](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Praca z ustawieniami specyficzne dla kultury](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Obsługa ciągów  
 Obsługa znaków i ciągów jest podstawowym elementem globalizacji, ponieważ każdy kultury lub regionu mogą użyć różnych znaków i zestawów znaków i sortowane w inny sposób. Ta sekcja zawiera zalecenia dotyczące używania ciągów w aplikacjach uniwersalnych.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Użyj wewnętrznie Unicode  
 Domyślnie program .NET Framework używa ciągów Unicode. Ciąg Unicode składa się z zero, co najmniej jeden <xref:System.Char> obiektów, z których każdy reprezentuje jednostki kodu UTF-16. Brak reprezentację prawie wszystkich znaków każdego zestawu używany na całym świecie znaków Unicode.  
  
 Wiele aplikacji i systemy operacyjne, w tym systemie operacyjnym Windows, można użyć również stron kodowych używany do reprezentowania zestawów znaków. Strony kodowe zwykle zawiera standardowe wartości ASCII z 0x00 za pośrednictwem 0x7F oraz mapowanie innych znaków na pozostałe wartości z 0x80 za pośrednictwem 0xFF. Interpretacja wartości z 0x80 za pośrednictwem 0xFF zależy od konkretnej strony kodowej. W związku z tym należy unikać używania stron kodowych w uniwersalnych aplikacji, jeśli to możliwe.  
  
 Poniższy przykład przedstawia zagrożeń interpretowanie stroną kodową, gdy domyślna strona kodowa w systemie różni się od strony kodowej zapisywane dane. (Aby symulować tego scenariusza, przykładzie jawnie określa różne strony kodowe.) Po pierwsze w przykładzie zdefiniowano tablicę, która składa się z wielkich liter alfabetu greckiego. Koduje je do tablicy typu byte przy użyciu kodu strony 737 (znanej także jako grecki MS-DOS), a tablica bajtów jest zapisywany do pliku. Jeśli plik jest pobierany i jego tablicy bajtów jest dekodowany przy użyciu kodu strony 737, są przywracane oryginalne znaki. Jednak jeśli plik jest pobierany i jego tablicy bajtów jest dekodowany przy użyciu strona kodowa 1252 (lub Windows-1252, który reprezentuje znaków alfabetu łacińskiego), oryginalne znaki zostaną utracone.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Użycie znaków Unicode zapewnia, że tej samej jednostki kod zawsze mapowane na te same znaki i czy znaków zawsze mapowane na tym samym tablice typu byte.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Użyj plików zasobów  
 Nawet jeśli tworzysz aplikację, która jest przeznaczony dla jednego kultury lub regionu, pliki zasobów należy używać do przechowywania ciągów i innych zasobów, które są wyświetlane w interfejsie użytkownika. Nigdy nie należy dodawać bezpośrednio w kodzie. Korzystanie z zasobów plików ma następujące korzyści:  
  
-   Wszystkie ciągi znajdują się w jednej lokalizacji. Nie masz do wyszukiwania w całym kodzie źródła, aby zidentyfikować ciągów, aby zmodyfikować dla określonego języka i kultury.  
  
-   Nie istnieje potrzeba duplikowanie ciągów. Deweloperzy, którzy nie używają plików zasobów często zdefiniować te same parametry w wielu plików kodu źródłowego. Tego duplikowania zwiększa prawdopodobieństwo, że jedna lub więcej wystąpień będą pomijane, jeśli ciąg zostanie zmodyfikowana.  
  
-   Może zawierać innych niż ciąg zasoby, takie jak obrazy lub dane binarne w pliku zasobu zamiast przechowywania ich w oddzielnych autonomiczny plik, aby łatwo pobrać.  
  
 Przy użyciu plików zasobów ma szczególne, jeśli tworzysz zlokalizowanej aplikacji. Podczas wdrażania zasobów w zestawy satelickie środowisko uruchomieniowe języka wspólnego automatycznie wybiera odpowiednią kultury zasób, w oparciu o użytkownika bieżącej kultury interfejsu użytkownika, zgodnie z definicją w <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Tak długo, jak podaj odpowiedni zasób specyficzne dla kultury i poprawnie wystąpienia <xref:System.Resources.ResourceManager> obiekt lub Klasa zasobu o jednoznacznie, środowisko uruchomieniowe obsługuje Szczegóły pobierania odpowiednie zasoby.  
  
 Aby uzyskać więcej informacji o tworzeniu plików zasobów, zobacz [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Aby uzyskać informacje o tworzeniu i wdrażaniu zestawy satelickie, zobacz [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) i [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Wyszukiwanie i porównywanie ciągów  
 Jeśli to możliwe, powinna obsługiwać ciągi jako ciągi całego zamiast ich obsługę jako serię znaki. Jest to szczególnie ważne podczas sortowania lub Wyszukaj podciągów, aby zapobiec problemom skojarzone z analizy łączenie znaków.  
  
> [!TIP]
>  Można użyć <xref:System.Globalization.StringInfo> klasy do pracy z elementów tekstu, a nie poszczególnych znaków w ciągu.  
  
 W ciągu wyszukiwania i porównań powszechnym błędem jest traktowane jako zbiór znaków, z których każdy jest reprezentowany przez ciąg <xref:System.Char> obiektu. W rzeczywistości pojedynczy znak może zostać utworzona przez jedną, dwie lub więcej <xref:System.Char> obiektów. Znaki te znajdują się najczęściej w ciągach od kultury, w których alfabetach składać się ze znaków spoza zakresu znaków Unicode podstawowa łacińskich (U + 0021 za pomocą U + 007E). Poniższy przykład podejmie próbę odnalezienia indeks znak LATIN litera A z DIAKRYTYCZNY (U + 00C 0) w ciągu. Jednak ten znak może być reprezentowany na dwa sposoby: jako pojedynczy kod jednostki (U + 00C 0) lub znak złożony (code dwie jednostki: U + 0021 i U + 007E). W takim przypadku znak jest reprezentowana w wystąpienia ciągu przez dwa <xref:System.Char> obiektów, U + 0021 i U + 007E. Przykładowy kod wywołuje <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> i <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> przeciążenia do Znajdź pozycję tego znaku w ciągu wystąpienia, ale te zwraca różne wyniki. W pierwszym wywołaniu metody ma <xref:System.Char> argument; wykonuje porównanie liczby porządkowej i dlatego nie można odnaleźć dopasowania. Drugie wywołanie ma <xref:System.String> argument; wykonuje porównanie zależne od kultury i w związku z tym znalezienia dopasowania.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Niektóre niejednoznaczności w tym przykładzie (wywołań do dwóch podobnych przeciążenia metody zwraca różne wyniki) można uniknąć, wywołując przeciążenia, które obejmuje <xref:System.StringComparison> parametrów, takich jak <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 Jednak wyszukiwania nie zawsze są zależne od kultury. Jeśli celem wyszukiwania jest podjęcie decyzji zabezpieczeń lub Zezwalaj lub nie zezwalaj na dostęp do niektórych zasobów, porównanie powinny być porządkowej, zgodnie z opisem w następnej sekcji.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Testowanie ciągów pod kątem równości  
 Jeśli chcesz przetestować dwa ciągi dla równości zamiast określania ich porównanie w porządku sortowania użyć <xref:System.String.Equals%2A?displayProperty=nameWithType> metody zamiast metodę porównywania ciągów, takich jak <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Porównania równości są zazwyczaj wykonywane do warunkowo dostęp do niektórych zasobów. Na przykład można wykonać porównania równości weryfikacji hasło lub potwierdź, że plik istnieje. Takie-językowe porównania powinna być zawsze porządkowej zamiast zależne od kultury. Ogólnie rzecz biorąc, należy wywołać wystąpienie <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody lub statycznego <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody o wartości <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> dla ciągów, takich jak hasła, a wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla ciągów, takich jak nazwy plików lub identyfikatorów URI.  
  
 Porównania równości czasami obejmują wyszukiwania lub podciąg porównania zamiast wywołań <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. W niektórych przypadkach może używać wyszukiwania podciągu, aby określić, czy ten podciąg jest równa innego ciągu. W przypadku innych niż językowe cel to porównanie wyszukiwania należy również porządkowej zamiast zależne od kultury.  
  
 Poniższy przykład przedstawia niebezpieczeństwo wyszukiwanie zależne od kultury na dane językowe. `AccessesFileSystem` Metoda jest przeznaczona do identyfikatory URI, które rozpoczynają się od podciągu "FILE" Zabroń używania dostępu do systemu plików. Aby to zrobić, wykonuje porównanie zależne od kultury, bez uwzględniania wielkości liter na początku identyfikatora URI z ciągu "Plik". Ponieważ identyfikator URI, który uzyskuje dostęp do systemu plików może się rozpoczynać albo "pliku:" lub "pliku:", niejawne zakłada się, że ten "i" (U + 0069) zawsze jest odpowiednikiem małe litery "I" (U + 0049). Jednak w turecki i Azerbejdżański, wersja wielkie litery "i" jest "İ" (U + 0130). Z powodu tej różnicy porównanie zależne od kultury umożliwia dostępu do systemu plików, czy powinien być zabroniony.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Można uniknąć tego problemu, wykonując porządkowej porównania, który ignoruje wielkość liter, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Szeregowanie i sortowania ciągów  
 Zazwyczaj uporządkowanej ciągów, które mają być wyświetlane w interfejsie użytkownika mają być sortowane zależności od kultury. W większości przypadków takie porównywanie ciągów obsługi niejawnie przez program .NET Framework podczas wywoływania metody, która sortuje ciągi znaków, takich jak <xref:System.Array.Sort%2A?displayProperty=nameWithType> lub <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Domyślnie ciągi są sortowane przy użyciu konwencji sortowania bieżącej kultury. Poniższy przykład przedstawia różnica w przypadku sortowania na tablicę ciągów za pomocą Konwencji kultury angielski (Stany Zjednoczone) i kultury szwedzki (Szwecja).  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Porównanie ciągów z uwzględnieniem kultury jest definiowana za pomocą <xref:System.Globalization.CompareInfo> obiektu, który jest zwracany przez poszczególnych kultur <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> właściwości. Porównywanie ciągów zależne od kultury, które używają <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda przeciąża również użycie <xref:System.Globalization.CompareInfo> obiektu.  
  
 .NET Framework używa tabel podczas sortowania zależne od kultury danych ciągu. Zawartość tych tabel, które zawierają dane dotyczące sortowania wagi, a ciąg normalizacji zależy od wersji Standard Unicode zaimplementowany przy użyciu określonej wersji programu .NET Framework. W poniższej tabeli wymieniono wersje Unicode zaimplementowany przy użyciu określonej wersji programu .NET Framework. Należy pamiętać, że ta lista obsługiwanych wersji Unicode dotyczy porównanie znaków i sortowania. nie ma zastosowania do klasyfikacji znaków Unicode w według kategorii. Aby uzyskać więcej informacji, zobacz sekcję "Ciągów i Unicode Standard" w <xref:System.String> artykułu.  
  
|Wersja programu .NET Framework|System operacyjny|Wersja Unicode|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Wszystkie systemy operacyjne|Unicode 4.1|  
|.NET Framework 3.0|Wszystkie systemy operacyjne|Unicode 4.1|  
|Program .NET Framework 3,5|Wszystkie systemy operacyjne|Unicode 4.1|  
|Program .NET Framework 4|Wszystkie systemy operacyjne|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Unicode 6.0|  
  
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], porównywanie i sortowanie ciągów zależy od systemu operacyjnego. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systemem [!INCLUDE[win7](../../../includes/win7-md.md)] pobiera dane z własną tabel, które implementuje Unicode 5.0. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systemem [!INCLUDE[win8](../../../includes/win8-md.md)] pobiera dane z tabel systemu operacyjnego, które implementują Unicode w wersji 6.0. Jeśli serializacji zależne od kultury posortowane dane, można użyć <xref:System.Globalization.SortVersion> klasę, aby określić, gdy dane serializowane potrzebuje można sortować, tak aby były zgodne z programu .NET Framework i kolejność sortowania systemu operacyjnego. Na przykład zobacz <xref:System.Globalization.SortVersion> klasy tematu.  
  
 Jeśli aplikacja przeprowadza szeroką gamę specyficzne dla kultury rodzaje danych dotyczących ciągu, możesz pracować z <xref:System.Globalization.SortKey> klasy do porównania ciągów. Klucz odzwierciedla specyficzne dla kultury sortowania wagi, tym alfabetyczne, wielkości liter i znaków diakrytycznych wagi określony ciąg. Ponieważ porównania przy użyciu kluczy sortowania są binarne, są szybsze niż porównań, które używają <xref:System.Globalization.CompareInfo> obiekt jawnie lub niejawnie. Utwórz klucz specyficzne dla kultury sortowania dla określonego ciągu przez przekazanie ciąg <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metody.  
  
 Poniższy przykład jest podobny do poprzedniego przykładu. Jednak zamiast wywoływać metodę <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metodę, która wywołuje niejawnie <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> definiuje metodę, <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementację, która porównuje klucze sortowania, które tworzy i przekazuje do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metody.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Unikaj łączenia ciągów  
 Jeśli to możliwe należy unikać złożonego ciągów, które są tworzone w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają gramatyczne kolejności w języku oryginalnej aplikacji, która nie ma zastosowania do innych językach lokalnych.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Obsługa daty i godziny  
 Sposób obsługi daty i wartości czasu zależy od tego, czy są wyświetlane w interfejsie użytkownika lub utrwalone. W tej sekcji sprawdza, czy zarówno użycia. Omówiono również, jak można obsługiwać różnice stref czasowych i operacje arytmetyczne podczas pracy z daty i godziny.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Wyświetlanie daty i godziny  
 Zwykle, gdy daty i godziny są wyświetlane w interfejsie użytkownika, należy używać konwencji formatowania kultury użytkownika, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości oraz <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez `CultureInfo.CurrentCulture.DateTimeFormat` właściwości. Konwencje formatowanie bieżącej kultury zostaną automatycznie użyte podczas formatowania daty przy użyciu jednej z następujących metod:  
  
-   Bez parametrów <xref:System.DateTime.ToString?displayProperty=nameWithType> — metoda  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Metodę, która zawiera ciąg formatu  
  
-   Bez parametrów <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> — metoda  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, W tym ciągu formatu  
  
-   [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md) funkcja, gdy jest używany z zastosowaniem dat  
  
 Poniższy przykład przedstawia sunrise i zachód słońca dane dwukrotnie 11 października 2012. Ustawia najpierw bieżącej kultury, chorwacki (Chorwacja), a następnie angielski (Polska). W każdym przypadku daty i godziny są wyświetlane w formacie, który jest odpowiedni dla tej kultury.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Przechowywanie daty i godziny  
 Nigdy nie ma utrwalić danych daty i godziny w formacie, który można różnią się zależnie od kultury. Jest to typowe błąd programistyczny, których wynikiem jest uszkodzone dane lub wyjątek czasu wykonywania. Poniższy przykład serializuje dwiema datami 9 styczeń 2013 i 18 sierpnia 2013 jako ciągi za pomocą Konwencji formatowania kultury angielski (Stany Zjednoczone). Gdy dane są pobierane i analizować za pomocą Konwencji kultury angielski (Stany Zjednoczone), został pomyślnie przywrócony. Jednak po pobrać i przeanalizować przy użyciu konwencji kultury angielski (brytyjski), pierwszej dacie błędnie jest interpretowana jako 1 września, a drugi nie przeanalizować ponieważ kalendarza gregoriańskiego nie ma 18 miesiącem.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Można uniknąć tego problemu w jednym z trzech sposobów:  
  
-   Serialize Data i godzina w formacie binarnym, a nie jako ciąg.  
  
-   Zapisz i przeanalizować reprezentację ciągu daty i godziny przy użyciu ciąg formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.  
  
-   Zapisz ten ciąg przy użyciu formatowania konwencjach Niezmienna kultura.  
  
 Poniższy przykład przedstawia ostatniego podejście. Używa konwencji formatowania z kulturą niezmienną zwrócony przez statycznych <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Serializacja i świadomości strefy czasowej  
 Wartość daty i godziny może mieć wielu interpretacje, począwszy od czasu ogólne ("magazynów Otwórz na 2 stycznia 2013 o 9:00") do określonego momentu w czasie ("Data urodzenia: 2 stycznia 2013 godziny 6:32:00: 00"). Gdy wartość czasu reprezentuje określonym momencie, a następnie przywróć ją z serializacji wartości, należy upewnić się, reprezentuje tego samego moment w czasie, niezależnie od lokalizacji geograficznej lub strefy czasowej użytkownika.  
  
 Poniższy przykład przedstawia ten problem. Zapisuje pojedynczy lokalnego wartość daty i godziny jako ciąg w trzech [standardowych formatów](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" dla ogólnych daty długi czas, "s" dla sortowanie daty/godziny, a "o" do przesyłania danych daty i godziny) oraz w formacie binarnym.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Po przywróceniu danych w systemie w tej samej strefie czasowej co system, na którym została wykonana serializacja zdeserializowany wartości daty i godziny dokładnie odzwierciedlał oryginalnej wartości, jak przedstawiono na dane wyjściowe:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Jednak w przypadku przywracania danych w systemie w innej strefie czasowej, tylko daty i godziny wartość sformatowano go przy użyciu ciągu standardowym formacie "o" (wyrównana) zachowuje informacje o strefie czasowej i w związku z tym reprezentuje takie same błyskawicznych w czasie. Poniżej przedstawiono dane wyjściowe po przywróceniu danych daty i godziny w systemie w strefie romantyka (czas standardowy):  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Dokładnie odzwierciedlał wartość daty i godziny, która reprezentuje pojedynczy chwilę czasu niezależnie od strefy czasowej systemu, na którym jest deserializacji danych, wykonaj jedną z następujących czynności:  
  
-   Zapisz wartość jako ciąg przy użyciu ciągu (obustronne) formatem "o". Następnie do deserializacji w systemie docelowym.  
  
-   Przekonwertuj go na czas UTC i zapisz go jako ciąg przy użyciu standardowego formatu ciągu "r" (RFC1123). Następnie do deserializacji w systemie docelowym i przekonwertować go na czas lokalny.  
  
-   Przekonwertuj go na czas UTC i zapisz go jako ciąg przy użyciu ciągu standardowym formacie "u" (uniwersalny sortowanie). Następnie do deserializacji w systemie docelowym i przekonwertować go na czas lokalny.  
  
-   Przekonwertuj go na czas UTC i zapisz go w formacie binarnym. Następnie do deserializacji w systemie docelowym i przekonwertować go na czas lokalny.  
  
 Poniższy przykład przedstawia każdego technik.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Gdy dane są serializowane w systemie w strefie czasowej pacyficzny standardowe i deserializacji w systemie w strefie romantyka (czas standardowy), w przykładzie przedstawiono następujące dane wyjściowe:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Aby uzyskać więcej informacji, zobacz [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Wykonywanie działań arytmetycznych daty i czasu  
 Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> typy obsługują operacje arytmetyczne. Można obliczyć różnicę między dwoma wartościami typu date, lub można dodawania lub odejmowania przedziały czasu określonego do lub z wartości daty. Jednak operacje arytmetyczne na wartości daty i godziny nie uwzględniać stref czasowych i reguły korekty strefy czasowej. W związku z tym data i godzina arytmetycznego na wartości, które reprezentują chwil w czasie może zwrócić wyniki niedokładne.  
  
 Na przykład przejście ze pacyficznego czasu standardowego do czasu pacyficznego letniego występuje w drugą niedzielę marca, czyli 10 marca 2013 roku. Jako poniższy przykład pokazuje, czy obliczenia daty i czasu, który jest 10 o godzinie: 30 48 godzin po 9 marca 2013 w systemie w pacyficzny standardowa strefy czasowej wynik 11 marca 2013 10 o godzinie: 30, nie przyjmuje pośredniczące dostosowania czasu pod uwagę.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Do zapewnienia, że operacja arytmetyczna na wartości daty i godziny dokładne wyniki, wykonaj następujące kroki:  
  
1.  Konwertuj czas w strefie czasowej źródła na czas UTC.  
  
2.  Wykonywania operacji arytmetycznej.  
  
3.  Jeśli wynik jest wartość daty i godziny, przekonwertuj go od czasu UTC na czas w strefie czasowej źródła.  
  
 Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że będzie wykonywać te trzy kroki, aby prawidłowo dodać 48 godzin 9 marca 2013 10 o godzinie: 30  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Aby uzyskać więcej informacji, zobacz [wykonywania operacje arytmetyczne przy użyciu daty i godziny](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Korzystając z nazw wrażliwych na ustawienia kulturowe do elementów daty  
 Aplikacja może być konieczne wyświetlona nazwa miesiąca lub dzień tygodnia. Aby to zrobić, kodu podobne do poniższych jest wspólnej.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Jednak ten kod zawsze zwraca nazwy dni tygodnia w języku angielskim. Kod, który wyodrębnia nazwy miesiąca jest często bardziej sztywne. Zakłada się często 12 miesięczny kalendarz z nazwami miesięcy w określonym języku.  
  
 Za pomocą [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) lub właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu, ułatwia wyodrębnić ciągów, które odzwierciedlać nazwy dni tygodnia lub miesięcy w kultury użytkownika, jak pokazano w poniższym przykładzie. Zmiany bieżącej kultury francuski (Francja), a nazwa dzień tygodnia i nazwa miesiąca 1 lipca 2013.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Obsługa wartości numerycznych  
 Obsługa liczb zależy od tego, czy są wyświetlane w interfejsie użytkownika lub utrwalone. W tej sekcji sprawdza, czy zarówno użycia.  
  
> [!NOTE]
>  Analizowanie i operacji formatowania, .NET Framework rozpoznaje tylko podstawowe znaki alfabetu łacińskiego od 0 do 9 (U + 0030 za pośrednictwem U + 0039) jako cyfr.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Wyświetlanie wartości numerycznych  
 Zwykle, gdy liczby są wyświetlane w interfejsie użytkownika, należy używać konwencji formatowania kultury użytkownika, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości oraz <xref:System.Globalization.NumberFormatInfo> obiektu zwróconego przez `CultureInfo.CurrentCulture.NumberFormat` właściwości. Konwencje formatowanie bieżącej kultury zostaną automatycznie użyte podczas formatowania daty przy użyciu dowolnej z następujących metod:  
  
-   Bez parametrów `ToString` metody typu liczbowego  
  
-   `ToString(String)` Metody dowolnego typu liczbowego, który zawiera ciąg formatu jako argument  
  
-   [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md) funkcja, gdy jest używany z wartości liczbowych  
  
 Poniższy przykład przedstawia średnią temperaturę miesiąca w Paryża, Francja. Pierwsze ustawienie bieżącej kultury francuski (Francja) przed wyświetleniem danych, a następnie ustawia język angielski (Stany Zjednoczone). W każdym przypadku nazwy miesięcy i temperatury są wyświetlane w formacie, który jest odpowiedni dla tej kultury. Należy pamiętać, że kultur dwóch różnych separatorów w wartości temperatury. Również należy zauważyć, że w przykładzie użyto "MMMM" Niestandardowa data i godzina ciąg formatu do nazwy pełny miesiąc wyświetlanej i że przydzielania odpowiednią ilość miejsca dla nazwy miesięcy w ciągu wyniku przez określenie długości najdłuższym nazwy miesiąca w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>tablicy.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Przechowywanie wartości numerycznych  
 Nigdy nie należy zachować dane liczbowe w formacie specyficzne dla kultury. Jest to typowe błąd programistyczny, których wynikiem jest uszkodzone dane lub wyjątek czasu wykonywania. Poniższy przykład generuje dziesięć losowych liczb zmiennoprzecinkowych i serializuje je jako ciągi za pomocą Konwencji formatowania kultury angielski (Stany Zjednoczone). Gdy dane są pobierane i analizować za pomocą Konwencji kultury angielski (Stany Zjednoczone), został pomyślnie przywrócony. Jednak gdy jest pobrać i przeanalizować przy użyciu konwencji kultury francuski (Francja), brak liczb można przeanalizować ponieważ kultur używają różnych separatorów.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 Aby uniknąć tego problemu, można użyć jednej z następujących metod:  
  
-   Zapisz i przeanalizować reprezentację liczby przy użyciu ciąg formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.  
  
-   Zapisz numer jako ciągu przy użyciu formatowania konwencjach Niezmienna kultura, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Serializuje kod w pliku binarnego zamiast formatu ciągu.  
  
 Poniższy przykład przedstawia ostatniego podejście. Serializuje go tablica <xref:System.Double> wartości, a następnie deserializuje i wyświetla je przy użyciu konwencji formatowania angielski (Stany Zjednoczone) i kultur francuski (Francja).  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Serializacji wartości waluty jest szczególnych przypadkach. Ponieważ wartość waluty zależy jednostkę waluty, w której jest wyrażona; Warto małego traktować go jako niezależne wartość liczbową. Jednak jeśli zapiszesz wartości waluty jako ciąg formatowania, która zawiera symbol waluty, nie można zdeserializować w systemie, w których domyślną kulturę korzysta inny symbol waluty, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Zamiast tego należy serializować wartość liczbową wraz z niektórych informacji kultury, takie jak nazwa kultury, tak, aby wartość i jego symbol waluty może być zdeserializowany, niezależnie od bieżącej kultury. Poniższy przykład robi to poprzez definiowanie `CurrencyValue` struktury z dwóch elementów: <xref:System.Decimal> wartość i nazwę kultury, do którego należy wartość.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Praca z ustawieniami specyficznymi dla kultury  
 W programie .NET Framework <xref:System.Globalization.CultureInfo> klasa reprezentuje określonej kultury lub regionu. Niektóre właściwości zwracają obiektów, które zawierają szczegółowe informacje dotyczące pewien aspekt kultury:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Zwraca <xref:System.Globalization.CompareInfo> obiekt, który zawiera informacje dotyczące sposobu kultura porównuje i porządkuje ciągów.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Zwraca <xref:System.Globalization.DateTimeFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używaną w formatowaniu danych daty i godziny.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używaną w formatowaniu dane liczbowe.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Zwraca właściwość <xref:System.Globalization.TextInfo> obiektu, który zawiera informacje o kultura do zapisywania systemu.  
  
 Ogólnie rzecz biorąc, nie należy wprowadzać żadnych założenia dotyczące wartości określonych <xref:System.Globalization.CultureInfo> właściwości i ich powiązanych obiektów. Zamiast tego należy wyświetlić dane specyficzne dla kultury jako mogą ulec zmianie, z tego względu:  
  
-   Pojedyncze wartości właściwości podlegają zmiany i poprawki w czasie, ponieważ danych jest usuwana, lepiej danych stanie się dostępny, lub zmień konwencje specyficzne dla kultury.  
  
-   Pojedyncze wartości właściwości mogą być różne w różnych wersjach systemu operacyjnego lub .NET Framework w wersji.  
  
-   .NET Framework obsługuje zastępczy kultur. Dzięki temu można zdefiniować nowego kulturą niestandardową, której uzupełnia istniejące kultur standardowe albo całkowicie zastępuje istniejące standardowe kultury.  
  
-   Użytkownik może dostosować ustawienia specyficzne dla kultury przy użyciu **Region i język** aplikacji w Panelu sterowania. Podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu, można określić, czy odzwierciedla te modyfikacje użytkownika, wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora. Zazwyczaj dla aplikacji przez użytkownika końcowego można powinna być zgodna preferencje użytkownika tak, aby użytkownik zobaczy z danymi w formacie, który użytkownik oczekuje.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)  
 [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
