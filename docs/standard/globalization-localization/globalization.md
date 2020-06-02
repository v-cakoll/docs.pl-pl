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
ms.openlocfilehash: adc617362cf3ba07ff63f1095968e2bd88df88d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291919"
---
# <a name="globalization"></a>Globalizacja

Globalizacja obejmuje projektowanie i opracowywanie gotowej do użytku aplikacji, która obsługuje zlokalizowane interfejsy i dane regionalne dla użytkowników w wielu kulturach. Przed rozpoczęciem fazy projektowania należy określić, które kultury będą obsługiwane przez aplikację. Mimo że aplikacja odwołuje się do pojedynczej kultury lub regionu jako domyślnego, można projektować i pisać, aby można ją było łatwo rozszerzyć do użytkowników w innych kulturach lub regionach.

Wszyscy deweloperzy mają założenia dotyczące interfejsów użytkownika i danych, które są tworzone przez nasze kultury. Na przykład w przypadku programisty w języku angielskim w Stany Zjednoczone, Serializowanie danych daty i godziny jako ciągu w formacie jest `MM/dd/yyyy hh:mm:ss` doskonale uzasadnione. Jednak deserializacja tego ciągu w systemie w innej kulturze prawdopodobnie zgłosi <xref:System.FormatException> wyjątek lub wygeneruje niedokładne dane. Globalizacja pozwala nam zidentyfikować takie założenia specyficzne dla kultury i upewnić się, że nie wpływają one na projekt lub kod aplikacji.

W tym artykule omówiono niektóre główne problemy, które należy wziąć pod uwagę, oraz najlepsze rozwiązania, które można wykonać podczas obsługi ciągów, wartości daty i godziny oraz wartości liczbowych w aplikacji globalnej.

## <a name="strings"></a>Ciągi

Obsługa znaków i ciągów jest centralną ostrością globalizacji, ponieważ każda kultura lub region może używać różnych znaków i zestawów znaków i sortować je inaczej. Ta sekcja zawiera zalecenia dotyczące używania ciągów w aplikacjach globalnych.

### <a name="use-unicode-internally"></a>Użyj wewnętrznie Unicode

Domyślnie platforma .NET używa ciągów Unicode. Ciąg Unicode składa się z zero, jeden lub więcej <xref:System.Char> obiektów, z których każdy reprezentuje jednostkę kodu UTF-16. Istnieje reprezentacja Unicode dla niemal każdego znaku w każdym zestawie znaków używanym na całym świecie.

Wiele aplikacji i systemów operacyjnych, w tym system operacyjny Windows, może służyć również do reprezentowania zestawów znaków przy użyciu stron kodowych. Strony kodowe zwykle zawierają standardowe wartości ASCII od 0x00 przez 0x7F i mapują inne znaki na pozostałe wartości z 0x80 do 0xFF. Interpretacja wartości z 0x80 do 0xFF zależy od określonej strony kodowej. W związku z tym należy unikać używania stron kodowych w aplikacji globalnej, jeśli jest to możliwe.

Poniższy przykład ilustruje zagrożenia interpretacji danych strony kodowej, gdy domyślna strona kodowa systemu różni się od strony kodowej, na której zapisano dane. (W celu zasymulowania tego scenariusza przykład jawnie określa różne strony kodowe). Najpierw w przykładzie zdefiniowano tablicę, która składa się z wielkich liter alfabetu greckiego. Koduje je do tablicy bajtowej przy użyciu strony kodowej 737 (znanej także jako system MS-DOS) i zapisuje tablicę bajtową do pliku. Jeśli plik jest pobierany, a jego tablica bajtowa jest zdekodowana przy użyciu strony kodowej 737, oryginalne znaki są przywracane. Jednak jeśli plik jest pobierany, a jego tablica bajtowa jest dekodowane przy użyciu strony kodowej 1252 (lub Windows-1252, która reprezentuje znaki alfabetu łacińskiego), oryginalne znaki są tracone.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Użycie Unicode gwarantuje, że te same jednostki kodu są zawsze mapowane na te same znaki i że te same znaki są zawsze mapowane na te same tablice bajtowe.

### <a name="use-resource-files"></a>Korzystanie z plików zasobów

Nawet jeśli tworzysz aplikację, która jest przeznaczona dla pojedynczej kultury lub regionu, należy używać plików zasobów do przechowywania ciągów i innych zasobów, które są wyświetlane w interfejsie użytkownika. Nigdy nie należy dodawać ich bezpośrednio do kodu. Korzystanie z plików zasobów ma wiele zalet:

- Wszystkie ciągi znajdują się w jednej lokalizacji. Nie musisz przeszukiwać w całym kodzie źródłowym, aby identyfikować ciągi do modyfikacji w konkretnym języku lub kulturze.

- Nie ma potrzeby duplikowania ciągów. Deweloperzy, którzy nie używają plików zasobów, często definiują ten sam ciąg w wielu plikach kodu źródłowego. To duplikowanie zwiększa prawdopodobieństwo, że co najmniej jedno wystąpienie zostanie odszukane po zmodyfikowaniu ciągu.

- W pliku zasobów można uwzględnić zasoby niebędące ciągami, takie jak obrazy lub dane binarne, a nie przechowywać ich w osobnym pliku autonomicznym, dzięki czemu można je łatwo pobrać.

Korzystanie z plików zasobów ma szczególne zalety, jeśli tworzysz zlokalizowaną aplikację. Podczas wdrażania zasobów w zestawach satelickich środowisko uruchomieniowe języka wspólnego automatycznie wybiera zasób odpowiedni dla kultury w oparciu o bieżącą kulturę interfejsu użytkownika określoną przez <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> Właściwość. O ile nie podajesz odpowiedniego zasobu specyficznego dla kultury i poprawnie utworzysz wystąpienie <xref:System.Resources.ResourceManager> obiektu lub użyj klasy zasobów o jednoznacznie określonym typie, środowisko uruchomieniowe obsługuje szczegóły pobierania odpowiednich zasobów.

Aby uzyskać więcej informacji na temat tworzenia plików zasobów, zobacz [Tworzenie plików zasobów](../../framework/resources/creating-resource-files-for-desktop-apps.md). Aby uzyskać informacje na temat tworzenia i wdrażania zestawów satelickich, zobacz [Tworzenie zestawów satelickich](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) i [pakowanie i wdrażanie zasobów](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Wyszukiwanie i Porównywanie ciągów

Jeśli to możliwe, należy obsługiwać ciągi jako całe ciągi zamiast obsługiwać je jako serię pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów, aby zapobiec problemom związanym z analizowaniem połączonych znaków.

> [!TIP]
> Można użyć <xref:System.Globalization.StringInfo> klasy do pracy z elementami tekstowymi, a nie pojedynczymi znakami w ciągu.

W przypadku wyszukiwania i porównywania ciągów częstą pomyłką jest traktowanie ciągu jako kolekcji znaków, z których każdy jest reprezentowany przez <xref:System.Char> obiekt. W rzeczywistości pojedynczy znak może być tworzony przez jeden, dwa lub więcej <xref:System.Char> obiektów. Takie znaki są najczęściej używane w ciągach z kultur, których alfabety składają się z znaków spoza zakresu znaków łacińskich Unicode Basic (U + 0021 do U + 007E). Poniższy przykład próbuje znaleźć indeks wielkiej litery A ze znakiem akcentu słabego (U + 00C0) w ciągu. Jednak ten znak może być reprezentowany na dwa różne sposoby: jako jedna Jednostka kodu (U + 00C0) lub jako znak złożony (dwie jednostki kodu: U + 0041 i U + 0300). W tym przypadku znak jest reprezentowany w wystąpieniu ciągu przez dwa <xref:System.Char> obiekty, u + 0041 i U + 0300. Przykładowy kod wywołuje <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> i <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> przeciążeń, aby znaleźć pozycję tego znaku w wystąpieniu ciągu, ale zwracają różne wyniki. Pierwsze wywołanie metody ma <xref:System.Char> argument; wykonuje porównanie porządkowe i w związku z tym nie może znaleźć dopasowania. Drugie wywołanie ma <xref:System.String> argument; wykonuje ono porównanie zależne od kultury i dlatego znajduje dopasowanie.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Można uniknąć niektórych niejednoznaczności tego przykładu (wywołania dwóch podobnych przeciążeń metody zwracają różne wyniki) przez wywołanie przeciążenia, które zawiera <xref:System.StringComparison> parametr, taki jak <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

Jednak wyszukiwania nie zawsze są zależne od kultury. Jeśli celem wyszukiwania jest podjęcie decyzji dotyczącej zabezpieczeń lub zezwolenie na dostęp do pewnego zasobu lub uniemożliwienie dostępu do niego, porównywanie powinno być porządkowe, zgodnie z opisem w następnej sekcji.

### <a name="test-strings-for-equality"></a>Ciągi testowe dla równości

Jeśli chcesz przetestować dwa ciągi pod kątem równości, zamiast określić sposób ich porównania w kolejności sortowania, użyj <xref:System.String.Equals%2A?displayProperty=nameWithType> metody zamiast metody porównywania ciągów, takiej jak <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> .

Porównania dla równości są zwykle wykonywane w celu zapewnienia warunkowego dostępu do określonego zasobu. Na przykład można przeprowadzić porównanie równości, aby zweryfikować hasło lub potwierdzić, że plik istnieje. Takie porównania nielingwistyczne powinny zawsze być liczbami porządkowymi, a nie z uwzględnieniem kultury. Ogólnie rzecz biorąc, należy wywołać metodę wystąpienia <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub metodę statyczną <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> z wartością <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> dla ciągów, takich jak hasła, oraz wartości <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla ciągów, takich jak nazwy plików lub identyfikatory URI.

Porównania dla równości czasami obejmują wyszukiwania lub porównania podciągów, a nie wywołania <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. W niektórych przypadkach możesz użyć wyszukiwania podciągu, aby określić, czy ten podciąg ma być innym ciągiem. Jeśli przeznaczeniem tego porównania jest inne niż językowe, wyszukiwanie powinno również mieć wartość porządkową, a nie jest zależne od kultury.

Poniższy przykład ilustruje niebezpieczeństwo wyszukiwania z uwzględnieniem kultury w przypadku danych niejęzykowych. `AccessesFileSystem`Metoda została zaprojektowana w celu zabronienia dostępu do systemu plików dla identyfikatorów URI rozpoczynających się od podciągu "File". W tym celu wykonuje porównanie bez uwzględniania wielkości liter względem początku identyfikatora URI z ciągiem "FILE". Ponieważ identyfikator URI, który uzyskuje dostęp do systemu plików, może rozpoczynać się od "FILE:" lub "File:", niejawne założenie to "i" (U + 0069) jest zawsze małymi literami "I" (U + 0049). Jednak w tureckim i azerbejdżańskim, Wielka wersja "i" to "i" (U + 0130). Ze względu na to rozbieżność porównanie wrażliwe na kulturę umożliwia dostęp do systemu plików, gdy powinien być zabroniony.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Można uniknąć tego problemu, wykonując porównanie porządkowe, które ignoruje wielkość liter, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Kolejność i sortowanie ciągów

Zazwyczaj uporządkowane ciągi, które mają być wyświetlane w interfejsie użytkownika, powinny być sortowane w oparciu o kulturę. W większości przypadków takie porównania ciągów są obsługiwane niejawnie przez platformę .NET po wywołaniu metody, która sortuje ciągi, takie jak <xref:System.Array.Sort%2A?displayProperty=nameWithType> lub <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> . Domyślnie ciągi są sortowane przy użyciu konwencji sortowania bieżącej kultury. Poniższy przykład ilustruje różnicę, gdy tablica ciągów jest sortowana przy użyciu Konwencji kultury angielskiej (Stany Zjednoczone) i kultury szwedzkiej (Szwecja).

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Porównywanie ciągów zależnych od kultury jest definiowane przez <xref:System.Globalization.CompareInfo> obiekt, który jest zwracany przez właściwość każdej kultury <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> . Porównania ciągów uwzględniających kulturę, które używają <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążeń metody, również używają <xref:System.Globalization.CompareInfo> obiektu.

Platforma .NET używa tabel do wykonywania sortowania z uwzględnieniem kultury danych w postaci ciągów. Zawartość tych tabel, która zawiera dane dotyczące sortowania i normalizacji ciągów, jest określana na podstawie wersji standardu Unicode zaimplementowanej przez określoną wersję programu .NET. W poniższej tabeli wymieniono wersje standardu Unicode zaimplementowane przez określone wersje .NET Framework i platformy .NET Core. Należy zauważyć, że ta lista obsługiwanych wersji Unicode ma zastosowanie do porównywania znaków i sortowania. nie dotyczy klasyfikacji znaków Unicode według kategorii. Aby uzyskać więcej informacji, zobacz sekcję "ciągi i standard Unicode" w <xref:System.String> artykule.

|Wersja programu .NET Framework|System operacyjny|Wersja Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Wszystkie systemy operacyjne|Unicode 4,1|
|.NET Framework 3.0|Wszystkie systemy operacyjne|Unicode 4,1|
|Program .NET Framework 3,5|Wszystkie systemy operacyjne|Unicode 4,1|
|Program .NET Framework 4|Wszystkie systemy operacyjne|Unicode 5,0|
|.NET Framework 4,5 i nowsze w systemie Windows 7|Unicode 5,0|
|.NET Framework 4,5 i nowsze w systemach operacyjnych Windows 8 i nowszych|6.3.0 Unicode|
|.NET Core (wszystkie wersje)|Zależy od wersji standardu Unicode obsługiwanego przez podstawowy system operacyjny.|

Począwszy od .NET Framework 4,5 i we wszystkich wersjach programu .NET Core, Porównywanie ciągów i sortowanie zależy od systemu operacyjnego. .NET Framework 4,5 i późniejsze działania w systemie Windows 7 pobiera dane z własnych tabel, które implementują standard Unicode 5,0. .NET Framework 4,5 i późniejsze uruchomione w systemie Windows 8 i nowszych pobiera dane z tabel systemu operacyjnego, które implementują standard Unicode 6,3. W przypadku platformy .NET Core obsługiwana wersja standardu Unicode zależy od bazowego systemu operacyjnego. W przypadku serializowania posortowanych danych z uwzględnieniem kultury, można użyć <xref:System.Globalization.SortVersion> klasy, aby określić, kiedy serializowane dane muszą być sortowane, aby były spójne z programem .NET i porządkiem sortowania systemu operacyjnego. Aby zapoznać się z przykładem, zobacz <xref:System.Globalization.SortVersion> temat Klasa.

Jeśli aplikacja wykonuje obszerne sortowanie danych ciągu, można współpracować z <xref:System.Globalization.SortKey> klasą w celu porównywania ciągów. Klucz sortowania odzwierciedla wagi sortowania specyficzne dla kultury, łącznie z alfabetyczną, wielkością liter i znakami diakrytycznych określonego ciągu. Ponieważ porównania przy użyciu kluczy sortowania są binarne, są one szybsze niż porównania, które używają <xref:System.Globalization.CompareInfo> obiektu niejawnie lub jawnie. Można utworzyć klucz sortowania specyficzny dla kultury dla określonego ciągu, przekazując ciąg do <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metody.

Poniższy przykład jest podobny do poprzedniego przykładu. Jednak zamiast wywołania <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metody, która niejawnie wywołuje <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> metodę, definiuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementację, która porównuje klucze sortowania, które tworzy wystąpienia i przekazuje do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metody.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Unikaj łączenia ciągów

Jeśli jest to możliwe, Unikaj używania złożonych ciągów, które są kompilowane w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają porządek gramatyczny w oryginalnym języku aplikacji, który nie dotyczy innych języków zlokalizowanych.

## <a name="handle-dates-and-times"></a>Obsługa dat i godzin

Sposób obsługi wartości daty i godziny zależy od tego, czy są wyświetlane w interfejsie użytkownika, czy utrwalone. Ta sekcja służy do badania obu użycia. Omówiono w nim również sposób obsługi różnic między strefami czasowymi i operacjami arytmetycznymi podczas pracy z datami i godzinami.

### <a name="display-dates-and-times"></a>Wyświetlanie dat i godzin

Zazwyczaj gdy daty i godziny są wyświetlane w interfejsie użytkownika, należy użyć Konwencji formatowania kultury użytkownika, która jest definiowana przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Właściwość i <xref:System.Globalization.DateTimeFormatInfo> obiekt zwrócony przez `CultureInfo.CurrentCulture.DateTimeFormat` Właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty za pomocą dowolnej z następujących metod:

- Metoda bez parametrów <xref:System.DateTime.ToString?displayProperty=nameWithType>

- <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>Metoda, która zawiera ciąg formatu

- Metoda bez parametrów <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>

- <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Który zawiera ciąg formatu

- Funkcja [formatowania złożonego](../base-types/composite-formatting.md) , gdy jest używana z datami

Poniższy przykład wyświetla dane o wschód i wschód słońca dwa razy dla 11 października 2012. Najpierw ustawia bieżącą kulturę na chorwacki (Chorwacja), a następnie na angielski (Wielka Brytania). W każdym przypadku daty i godziny są wyświetlane w formacie, który jest odpowiedni dla tej kultury.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Utrwalanie dat i godzin

Nigdy nie należy utrwalać danych daty i godziny w formacie, który może się różnić w zależności od kultury. Jest to typowy błąd programistyczny, który powoduje uszkodzenie danych lub wyjątek czasu wykonywania. Poniższy przykład serializacji dwóch dat, 9 stycznia 2013 i 18 sierpnia 2013 jako ciągów przy użyciu Konwencji formatowania kultury angielskiej (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu Konwencji kultury angielskiej (Stany Zjednoczone), zostanie ona pomyślnie przywrócona. Jednak po pobraniu i przeanalizowaniu przy użyciu Konwencji kultury angielskiej (Wielka Brytania) pierwsza data jest błędnie interpretowana jako 1 września, a druga nie można przeanalizować, ponieważ kalendarz gregoriański nie ma osiemnastegoego miesiąca.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Można uniknąć tego problemu na jeden z trzech sposobów:

- Serializować datę i godzinę w formacie binarnym, a nie jako ciąg.

- Zapisz i Przeanalizuj reprezentację ciągu daty i godziny przy użyciu ciągu formatu niestandardowego, który jest taki sam niezależnie od kultury użytkownika.

- Zapisz ciąg przy użyciu Konwencji formatowania niezmiennej kultury.

Poniższy przykład ilustruje ostatnią metodę. Używa Konwencji formatowania kultury niezmiennej zwróconej przez właściwość statyczną <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serializacja i rozpoznawanie strefy czasowej

Wartość daty i godziny może mieć wiele interpretacji, od ogólnego czasu ("sklepy otwarte w dniu 2 stycznia 2013, o godzinie 9:00 rano") do określonego momentu ("Data urodzenia: 2 stycznia 2013 6:32:00)"). Gdy wartość czasu reprezentuje określony moment w czasie i przywracasz ją z serializowanej wartości, należy się upewnić, że reprezentuje ona ten sam moment w czasie, niezależnie od lokalizacji geograficznej użytkownika lub strefy czasowej.

Poniższy przykład ilustruje ten problem. Zapisuje pojedynczą lokalną wartość daty i godziny jako ciąg w trzech [standardowych formatach](../base-types/standard-date-and-time-format-strings.md) ("G" dla daty ogólnej godziny długiej, "s" do sortowania daty/godziny, i "o" dla daty/godziny rundy), jak również w formacie binarnym.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Gdy dane są przywracane w systemie w tej samej strefie czasowej co system, w którym został on Zserializowany, wartości daty i godziny, które zostały rozszeregowane, dokładnie odzwierciedlają pierwotną wartość, ponieważ dane wyjściowe są wyświetlane:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Jeśli jednak przywracasz dane w systemie w innej strefie czasowej, tylko wartość daty i godziny, która była sformatowana przy użyciu standardowego ciągu formatu "o" (Round-Trip), zachowuje informacje o strefie czasowej i w związku z tym reprezentuje to samo natychmiastowe w czasie. Oto dane wyjściowe, gdy dane daty i godziny zostaną przywrócone w systemie w standardowej strefie czasowej

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Aby dokładnie odzwierciedlić wartość daty i godziny, która reprezentuje jeden moment czasu, niezależnie od strefy czasowej systemu, w którym dane są deserializowane, można wykonać jedną z następujących czynności:

- Zapisz wartość jako ciąg przy użyciu ciągu formatu standardowego "o" (Round-Trip). Następnie deserializacji go w systemie docelowym.

- Przekonwertuj go na UTC i Zapisz jako ciąg za pomocą ciągu formatu standardowego "r" (RFC1123). Następnie deserializacji go w systemie docelowym i przekonwertuj go na czas lokalny.

- Przekonwertuj go na UTC i Zapisz jako ciąg za pomocą ciągu formatu standardowego "u". Następnie deserializacji go w systemie docelowym i przekonwertuj go na czas lokalny.

- Przekonwertuj go na UTC i Zapisz w formacie binarnym. Następnie deserializacji go w systemie docelowym i przekonwertuj go na czas lokalny.

Poniższy przykład ilustruje każdą technikę.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Gdy dane są serializowane w systemie w standardowej strefie czasowej pacyficznego i deserializowane w systemie w standardowej strefie czasowej w trybie romańskim, w przykładzie są wyświetlane następujące dane wyjściowe:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Aby uzyskać więcej informacji, zobacz [konwertowanie czasów między strefami czasowymi](../datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Wykonywanie operacji arytmetycznych daty i godziny

<xref:System.DateTime> <xref:System.DateTimeOffset> Typy i obsługują operacje arytmetyczne. Można obliczyć różnicę między dwiema wartościami typu date lub można dodawać lub odejmować określone przedziały czasu do lub z wartości typu Date. Jednak operacje arytmetyczne na wartościach daty i godziny nie uwzględniają stref czasowych i reguł korekty strefy czasowej. Z tego powodu, Data i czas arytmetyczny dla wartości, które reprezentują czas oczekiwania, może zwracać niedokładne wyniki.

Na przykład przejście z czasu standardowego do Pacyfiku czasu pacyficznego do Pacyficzny czas letni występuje w drugim niedzielę marca, czyli 10 marca dla roku 2013. Jak pokazano na poniższym przykładzie, jeśli obliczasz datę i godzinę 48 godzin od 9 marca, 2013 o godz. 10:30 w systemie w normalnych strefach czasowych pacyficznego wynik, 11 marca 2013 o godz. 10:30 rano, nie pobiera zmiany czasu na konto.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Aby zapewnić, że operacja arytmetyczna na wartościach daty i godziny daje dokładne wyniki, wykonaj następujące czynności:

1. Przekonwertuj czas w źródłowej strefie czasowej na czas UTC.

2. Wykonaj operację arytmetyczną.

3. Jeśli wynik jest wartością daty i godziny, przekonwertuj ją z czasu UTC na czas w źródłowej strefie czasowej.

Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że wykonuje następujące trzy kroki, aby poprawnie dodać 48 godzin do 9 marca 2013 o godz. 10:30

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Aby uzyskać więcej informacji, zobacz [wykonywanie operacji arytmetycznych z datami i godzinami](../datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Używaj nazw zależnych od kultury dla elementów daty

W aplikacji może być konieczne wyświetlenie nazwy miesiąca lub dnia tygodnia. W tym celu należy wykonać kod, taki jak poniższe.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Jednak ten kod zawsze zwraca nazwy dni tygodnia w języku angielskim. Kod, który wyodrębnia nazwę miesiąca, jest często jeszcze bardziej elastyczny. Często zakłada się, że kalendarz 12-miesięczny ma nazwy miesięcy w określonym języku.

Używając [niestandardowych ciągów formatu daty i godziny](../base-types/custom-date-and-time-format-strings.md) lub właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu, można łatwo wyodrębnić ciągi, które odzwierciedlają nazwy dni tygodnia lub miesięcy w kulturze użytkownika, jak pokazano w poniższym przykładzie. Zmienia bieżącą kulturę na francuski (Francja) i wyświetla nazwę dnia tygodnia oraz nazwę miesiąca w dniu 1 lipca 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Wartości liczbowe

Obsługa liczb zależy od tego, czy są wyświetlane w interfejsie użytkownika, czy utrwalone. Ta sekcja służy do badania obu użycia.

> [!NOTE]
> W przypadku operacji analizowania i formatowania platforma .NET rozpoznaje tylko podstawowe znaki łacińskie od 0 do 9 (U + 0030 do U + 0039) jako cyfry liczbowe.

### <a name="display-numeric-values"></a>Wyświetl wartości liczbowe

Zazwyczaj gdy liczby są wyświetlane w interfejsie użytkownika, należy użyć Konwencji formatowania kultury użytkownika, która jest zdefiniowana przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Właściwość i <xref:System.Globalization.NumberFormatInfo> obiekt zwrócony przez `CultureInfo.CurrentCulture.NumberFormat` Właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty za pomocą dowolnej z następujących metod:

- Bezparametrowa `ToString` Metoda dowolnego typu liczbowego

- `ToString(String)`Metoda dowolnego typu liczbowego, która zawiera ciąg formatu jako argument

- Funkcja [formatowania złożonego](../base-types/composite-formatting.md) , gdy jest używana z wartościami liczbowymi

W poniższym przykładzie przedstawiono średnią temperaturę miesięcznie w Paryżu, Francja. Najpierw ustawia bieżącą kulturę na francuski (Francja) przed wyświetleniem danych, a następnie ustawia ją na angielski (Stany Zjednoczone). W każdym przypadku nazwy miesięcy i temperatury są wyświetlane w formacie, który jest odpowiedni dla tej kultury. Należy zauważyć, że dwie kultury używają różnych separatorów dziesiętnych w wartości temperatury. Należy również zauważyć, że w przykładzie jest stosowany niestandardowy ciąg formatu daty i godziny "MMMM", aby wyświetlić pełną nazwę miesiąca i przydzielić odpowiednią ilość miejsca dla nazwy miesiąca w ciągu wynikowym przez określenie długości najdłuższej nazwy miesiąca w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> tablicy.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Utrwalaj wartości liczbowe

Nigdy nie należy utrwalać danych liczbowych w formacie specyficznym dla kultury. Jest to typowy błąd programistyczny, który powoduje uszkodzenie danych lub wyjątek czasu wykonywania. Poniższy przykład generuje dziesięć losowych liczb zmiennoprzecinkowych, a następnie serializować je jako ciągi przy użyciu Konwencji formatowania kultury angielskiej (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu Konwencji kultury angielskiej (Stany Zjednoczone), zostanie ona pomyślnie przywrócona. Jednak podczas pobierania i analizowania przy użyciu Konwencji kultury francuskiej (Francja) nie można analizować żadnej liczby, ponieważ kultury używają różnych separatorów dziesiętnych.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Aby uniknąć tego problemu, można użyć jednej z następujących metod:

- Zapisz i Przeanalizuj reprezentację liczby przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.

- Zapisz liczbę jako ciąg przy użyciu Konwencji formatowania kultury niezmiennej, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> Właściwość.

- Serializacja liczby w postaci binarnej, a nie w formacie ciągu.

Poniższy przykład ilustruje ostatnią metodę. Deserializować tablicę <xref:System.Double> wartości, a następnie deserializacji i wyświetla je przy użyciu Konwencji formatowania dla kultur angielskiej (Stany Zjednoczone) i francuski (Francja).

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Serializowanie wartości walutowych jest szczególnym przypadkiem. Ponieważ wartość waluty zależy od jednostki waluty, w której jest wyrażona; nie ma sensu, aby traktować go jako niezależną wartość liczbową. Jednak w przypadku zapisania wartości walutowej jako ciągu sformatowanego zawierającego symbol waluty nie można jej zdeserializować w systemie, którego domyślna kultura używa innego symbolu waluty, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Zamiast tego należy serializować wartość liczbową wraz z niektórymi informacjami kulturowymi, takimi jak nazwa kultury, tak aby wartość i jej symbol waluty mogły być deserializowane niezależnie od bieżącej kultury. W poniższym przykładzie jest to definiujące `CurrencyValue` strukturę z dwoma elementami członkowskimi: <xref:System.Decimal> wartość i nazwa kultury, do której należy wartość.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Pracuj z ustawieniami specyficznymi dla kultury

W programie .NET <xref:System.Globalization.CultureInfo> Klasa reprezentuje określoną kulturę lub region. Niektóre z jej właściwości zwracają obiekty, które zawierają określone informacje dotyczące pewnego aspektu kultury:

- <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Globalization.CompareInfo> obiekt, który zawiera informacje o tym, jak kultura porówna i porządkuje ciągi.

- <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Globalization.DateTimeFormatInfo> obiekt, który dostarcza informacje specyficzne dla kultury używane do formatowania danych daty i godziny.

- <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacje specyficzne dla kultury używane do formatowania danych liczbowych.

- <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Globalization.TextInfo> obiekt, który zawiera informacje o systemie zapisu kultury.

Ogólnie rzecz biorąc nie należy wprowadzać żadnych założeń dotyczących wartości określonych <xref:System.Globalization.CultureInfo> właściwości i ich powiązanych obiektów. Zamiast tego należy wyświetlić dane specyficzne dla kultury, które mogą ulec zmianie, z następujących powodów:

- Poszczególne wartości właściwości podlegają zmianom i poprawkom w miarę upływu czasu, gdy dane są korygowane, będą dostępne lepsze dane lub zmiany w konwencjach specyficznych dla kultury.

- Poszczególne wartości właściwości mogą się różnić w zależności od wersji platformy .NET lub systemu operacyjnego.

- Platforma .NET obsługuje kulturę zamienną. Dzięki temu można zdefiniować nową kulturę niestandardową, która uzupełnia istniejące kultury standardowe lub całkowicie zastępuje istniejącą kulturę standardową.

- W systemach Windows użytkownik może dostosować ustawienia specyficzne dla kultury przy użyciu aplikacji **region i język** w panelu sterowania. Podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu można określić, czy ma on odzwierciedlać te dostosowania użytkownika przez wywołanie <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> konstruktora. Zazwyczaj w przypadku aplikacji użytkownika końcowego należy przestrzegać preferencji użytkownika, tak aby użytkownik miał dane w oczekiwanym formacie.

## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](index.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../base-types/best-practices-strings.md)
