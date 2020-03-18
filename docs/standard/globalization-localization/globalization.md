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
ms.openlocfilehash: fe03bbdd7d037a9f1fb4985b62b447c6ef9c6535
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79174787"
---
# <a name="globalization"></a>Globalizacja

Globalizacja polega na projektowaniu i rozwijaniu aplikacji gotowej na świat, która obsługuje zlokalizowane interfejsy i dane regionalne dla użytkowników w wielu kulturach. Przed rozpoczęciem fazy projektowania należy określić, które kultury będzie obsługiwana przez aplikację. Mimo że aplikacja jest przeznaczona dla pojedynczej kultury lub regionu jako domyślnego, można zaprojektować i napisać go, aby można go było łatwo rozszerzyć na użytkowników w innych kulturach lub regionach.

Jako deweloperzy wszyscy mamy założenia dotyczące interfejsów użytkownika i danych, które są tworzone przez nasze kultury. Na przykład dla anglojęzycznego dewelopera w Stanach Zjednoczonych serializowanie danych daty `MM/dd/yyyy hh:mm:ss` i godziny jako ciągu w formacie wydaje się całkowicie uzasadnione. Jednak deserializing tego ciągu w systemie w innej kulturze <xref:System.FormatException> może zgłosić wyjątek lub wygenerować niedokładne dane. Globalizacja pozwala nam zidentyfikować takie założenia specyficzne dla kultury i upewnić się, że nie mają one wpływu na projekt lub kod naszej aplikacji.

W tym artykule omówiono niektóre z głównych problemów, które należy wziąć pod uwagę i najlepsze rozwiązania, które można wykonać podczas obsługi ciągów, wartości daty i godziny oraz wartości liczbowych w zglobalizowanej aplikacji.

## <a name="strings"></a>Ciągi

Obsługa znaków i ciągów jest centralnym celem globalizacji, ponieważ każda kultura lub region może używać różnych znaków i zestawów znaków i sortować je inaczej. Ta sekcja zawiera zalecenia dotyczące używania ciągów w zglobalizowanych aplikacjach.

### <a name="use-unicode-internally"></a>Używaj unicode wewnętrznie

Domyślnie .NET używa ciągów Unicode. Ciąg Unicode składa się z zero, jeden lub więcej <xref:System.Char> obiektów, z których każdy reprezentuje jednostkę kodu UTF-16. Istnieje reprezentacja Unicode dla prawie każdej postaci w każdym zestawie znaków w użyciu na całym świecie.

Wiele aplikacji i systemów operacyjnych, w tym system operacyjny Windows, może używać również stron kodowych do reprezentowania zestawów znaków. Strony kodowe zazwyczaj zawierają standardowe wartości ASCII od 0x00 do 0x7F i mapują inne znaki na pozostałe wartości od 0x80 do 0xFF. Interpretacja wartości od 0x80 do 0xFF zależy od określonej strony kodowej. Z tego powodu należy unikać używania stron kodowych w zglobalizowanej aplikacji, jeśli to możliwe.

W poniższym przykładzie przedstawiono niebezpieczeństwa związane z interpretacją danych strony kodowej, gdy domyślna strona kodowa w systemie różni się od strony kodowej, na której dane zostały zapisane. (Aby symulować ten scenariusz, w przykładzie jawnie określa różne strony kodowe.) Po pierwsze, w przykładzie definiuje tablicę, która składa się z wielkich liter alfabetu greckiego. Koduje je do tablicy bajtów przy użyciu strony kodowej 737 (znany również jako MS-DOS grecki) i zapisuje tablicy bajtów do pliku. Jeśli plik jest pobierany, a jego tablica bajtów jest dekodowana przy użyciu strony kodowej 737, oryginalne znaki są przywracane. Jeśli jednak plik zostanie pobrany, a jego tablica bajtów zostanie zdekodowana przy użyciu strony kodowej 1252 (lub Systemu Windows-1252, który reprezentuje znaki alfabetu łacińskiego), oryginalne znaki zostaną utracone.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Użycie Unicode zapewnia, że te same jednostki kodu zawsze mapują na te same znaki i że te same znaki są zawsze mapowane na te same tablice bajtowe.

### <a name="use-resource-files"></a>Korzystanie z plików zasobów

Nawet jeśli tworzysz aplikację, która jest przeznaczona dla pojedynczej kultury lub regionu, należy użyć plików zasobów do przechowywania ciągów i innych zasobów, które są wyświetlane w interfejsie użytkownika. Nigdy nie należy dodawać ich bezpośrednio do kodu. Korzystanie z plików zasobów ma wiele zalet:

- Wszystkie ciągi znajdują się w jednej lokalizacji. Nie trzeba wyszukiwać w całym kodzie źródłowym, aby zidentyfikować ciągi do modyfikowania dla określonego języka lub kultury.

- Nie ma potrzeby duplikowania ciągów. Deweloperzy, którzy nie używają plików zasobów często definiują ten sam ciąg w wielu plikach kodu źródłowego. To powielanie zwiększa prawdopodobieństwo, że co najmniej jedno wystąpienie zostanie pominięte po zmodyfikowaniu ciągu.

- W pliku zasobów zamiast przechowywać je w oddzielnym pliku autonomicznym można uwzględnić zasoby niebędące ciągami, takie jak obrazy lub dane binarne, aby można je było łatwo pobrać.

Korzystanie z plików zasobów ma szczególne zalety podczas tworzenia zlokalizowanej aplikacji. Podczas wdrażania zasobów w zestawach satelickich środowisko uruchomieniowe języka wspólnego automatycznie wybiera zasób odpowiedni <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> dla kultury na podstawie bieżącej kultury interfejsu użytkownika zgodnie z definicją właściwości. Tak długo, jak podać odpowiedni zasób specyficzne dla <xref:System.Resources.ResourceManager> kultury i poprawnie utworzyć wystąpienia obiektu lub użyć klasy zasobów silnie typizowany, czas wykonywania obsługuje szczegóły pobierania odpowiednich zasobów.

Aby uzyskać więcej informacji na temat tworzenia plików zasobów, zobacz [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Aby uzyskać informacje dotyczące tworzenia i wdrażania zestawów satelickich, zobacz [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) oraz [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Wyszukiwanie i porównywanie ciągów

Jeśli to możliwe, należy obsługiwać ciągi jako całe ciągi zamiast obsługiwać je jako serię pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów, aby zapobiec problemom związanym z analizowaniem połączonych znaków.

> [!TIP]
> Klasa służy <xref:System.Globalization.StringInfo> do pracy z elementami tekstowymi, a nie poszczególnych znaków w ciągu.

W wyszukiwaniach ciągów i porównaniach typowym błędem jest traktowanie ciągu jako kolekcji <xref:System.Char> znaków, z których każdy jest reprezentowany przez obiekt. W rzeczywistości pojedynczy znak może być utworzony przez <xref:System.Char> jeden, dwa lub więcej obiektów. Takie znaki znajdują się najczęściej w ciągach z kultur, których alfabety składają się ze znaków spoza zakresu znaków łacińskich Unicode Basic (Od U+0021 do U+007E). Poniższy przykład próbuje znaleźć indeks litery ŁACIŃSKIEJ litery A z pochylnym znakiem (U +00C0) w ciągu. Jednak ten znak może być reprezentowany na dwa różne sposoby: jako pojedyncza jednostka kodu (U + 00C0) lub jako znak złożony (dwie jednostki kodu: U + 0041 i U + 0300). W takim przypadku znak jest reprezentowany w wystąpieniu ciągu przez dwa <xref:System.Char> obiekty, U + 0041 i U + 0300. Przykładowy kod <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> wywołuje <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> i przeciążenia, aby znaleźć pozycję tego znaku w wystąpieniu ciągu, ale te zwracają różne wyniki. Pierwsze wywołanie metody <xref:System.Char> ma argument; wykonuje porównanie szeregowe i dlatego nie może znaleźć dopasowania. Drugie wywołanie <xref:System.String> ma argument; wykonuje porównanie zależne od kultury i w związku z tym znajdzie dopasowanie.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Można uniknąć niektórych niejednoznaczności tego przykładu (wywołania dwóch podobnych przeciążeń metody zwracania różnych wyników), wywołując przeciążenie, które zawiera <xref:System.StringComparison> parametr, takich jak <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.

Jednak wyszukiwania nie zawsze są zależne od kultury. Jeśli celem wyszukiwania jest podjęcie decyzji o zabezpieczeniu lub zezwolenie lub niezezwalanie na dostęp do niektórych zasobów, porównanie powinno być liczbami, jak omówiono w następnej sekcji.

### <a name="test-strings-for-equality"></a>Testowanie ciągów równości

Jeśli chcesz przetestować dwa ciągi równości, a nie określić, jak <xref:System.String.Equals%2A?displayProperty=nameWithType> porównują się w <xref:System.String.Compare%2A?displayProperty=nameWithType> kolejności <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>sortowania, należy użyć metody zamiast metody porównywania ciągów, takich jak lub .

Porównania równości są zazwyczaj wykonywane w celu uzyskania dostępu do niektórych zasobów warunkowo. Na przykład można wykonać porównanie równości, aby zweryfikować hasło lub potwierdzić, że plik istnieje. Takie porównania niejęzykowe powinny być zawsze stosowane, a nie kulturowe. Ogólnie rzecz biorąc należy <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wywołać metodę <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wystąpienia lub <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> metodę statyczną z wartością dla <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> ciągów, takich jak hasła i wartością dla ciągów, takich jak nazwy plików lub identyfikatory URI.

Porównania równości czasami obejmują wyszukiwania lub porównania podciągów, a nie wywołania <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. W niektórych przypadkach można użyć wyszukiwania podciągu, aby ustalić, czy ten podciąg jest równy innemu ciągowi. Jeśli cel tego porównania jest niejęzykowy, wyszukiwanie powinno być również posuwne, a nie zależne od kultury.

Poniższy przykład ilustruje niebezpieczeństwo wyszukiwania zależnego od kultury na danych niejęzykowych. Metoda `AccessesFileSystem` ma na celu zakazanie dostępu do systemu plików URI, które zaczynają się od podciągu "PLIK". W tym celu wykonuje porównanie z uwzględnieniem kultury, bez uwzględniania wielkości liter na początku identyfikatora URI z ciągiem "FILE". Ponieważ identyfikator URI, który uzyskuje dostęp do systemu plików, może zaczynać się od "FILE:" lub "file:", niejawne założenie jest takie, że "i" (U+0069) jest zawsze niewielkim odpowiednikiem "I" (U+0049). Jednak w języku tureckim i azerbejdżańsko, wielkie litery "i" jest "İ" (U + 0130). Z powodu tej rozbieżności porównanie zależne od kultury umożliwia dostęp do systemu plików, gdy powinno być zabronione.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Ten problem można uniknąć, wykonując porównanie liczba mięsień, która ignoruje case, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Porządkować i sortować ciągi znaków

Zazwyczaj uporządkowane ciągi, które mają być wyświetlane w interfejsie użytkownika powinny być sortowane na podstawie kultury. W przeważającej części takie porównania ciągów są obsługiwane niejawnie przez .NET podczas <xref:System.Array.Sort%2A?displayProperty=nameWithType> wywoływania metody, która sortuje ciągi, takie jak lub <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Domyślnie ciągi są sortowane przy użyciu konwencji sortowania bieżącej kultury. Poniższy przykład ilustruje różnicę, gdy tablica ciągów jest sortowana przy użyciu konwencji kultury angielskiej (Stany Zjednoczone) i kultury szwedzkiej (Szwecja).

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Porównanie ciągów zależnych od <xref:System.Globalization.CompareInfo> kultury jest zdefiniowany przez obiekt, który jest zwracany przez <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> właściwość każdej kultury. Porównania ciągów zależne od <xref:System.String.Compare%2A?displayProperty=nameWithType> kultury, które używają <xref:System.Globalization.CompareInfo> przeciążenia metody również użyć obiektu.

.NET używa tabel do wykonywania sortowania zależne od kultury na danych ciągów. Zawartość tych tabel, które zawierają dane dotyczące wagi sortowania i normalizacji ciągów, jest określana przez wersję standardu Unicode zaimplementowanej przez określoną wersję .NET. W poniższej tabeli wymieniono wersje Unicode zaimplementowane przez określone wersje programu .NET Framework i .NET Core. Należy zauważyć, że ta lista obsługiwanych wersji Unicode ma zastosowanie tylko do porównywania znaków i sortowania; nie ma zastosowania do klasyfikacji znaków Unicode według kategorii. Aby uzyskać więcej informacji, zobacz sekcję "Ciągi i <xref:System.String> Standard Unicode" w artykule.

|Wersja programu .NET Framework|System operacyjny|Wersja Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Wszystkie systemy operacyjne|Kod Unicode 4.1|
|.NET Framework 3.0|Wszystkie systemy operacyjne|Kod Unicode 4.1|
|Program .NET Framework 3,5|Wszystkie systemy operacyjne|Kod Unicode 4.1|
|Program .NET Framework 4|Wszystkie systemy operacyjne|Unicode 5.0|
|.NET Framework 4.5 i nowszych w systemie Windows 7|Unicode 5.0|
|.NET Framework 4.5 i nowszych w systemach operacyjnych Windows 8 i nowszych|Unicode 6.3.0|
|.NET Core (wszystkie wersje)|Zależy od wersji Standardu Unicode obsługiwanej przez podstawowy system operacyjny.|

Począwszy od .NET Framework 4.5 i we wszystkich wersjach programu .NET Core, porównanie ciągów i sortowanie zależy od systemu operacyjnego. Program .NET Framework 4.5 i nowszy uruchomiony w systemie Windows 7 pobiera dane z własnych tabel implementowanych przez Unicode 5.0. Program .NET Framework 4.5 i nowszy uruchomiony w systemie Windows 8 i nowszych pobiera dane z tabel systemu operacyjnego, które implementują Unicode 6.3. W .NET Core obsługiwana wersja Unicode zależy od podstawowego systemu operacyjnego. Jeśli serializujesz dane posortowane z uwzględnieniem kultury, można użyć <xref:System.Globalization.SortVersion> klasy do określenia, kiedy dane serializowane muszą być sortowane, tak aby były zgodne z .NET i kolejności sortowania systemu operacyjnego. Na przykład zobacz <xref:System.Globalization.SortVersion> temat klasy.

Jeśli aplikacja wykonuje rozbudowane rodzaje danych ciągów specyficzne dla <xref:System.Globalization.SortKey> kultury, można pracować z klasą, aby porównać ciągi. Klucz sortowania odzwierciedla wagi sortowania specyficzne dla kultury, w tym wagi alfabetyczne, wielkości liter i znaków diakrytycznych określonego ciągu. Ponieważ porównania przy użyciu kluczy sortowania są binarne, są one szybsze niż porównania, które używają <xref:System.Globalization.CompareInfo> obiektu niejawnie lub jawnie. Klucz sortowania specyficzny dla kultury jest tworzony dla określonego <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> ciągu, przekazując ciąg do metody.

Poniższy przykład jest podobny do poprzedniego przykładu. Jednak zamiast wywoływania <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metody, która niejawnie wywołuje <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> metodę, definiuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementację, która porównuje klucze sortowania, które tworzy i przekazuje do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metody.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Unikaj łączenia ciągów

Jeśli to możliwe, należy unikać używania ciągów złożonych, które są tworzone w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często przyjmują kolejność gramatyczną w oryginalnym języku aplikacji, która nie ma zastosowania do innych zlokalizowanych języków.

## <a name="handle-dates-and-times"></a>Obsługa dat i godzin

Sposób obsługi wartości daty i godziny zależy od tego, czy są one wyświetlane w interfejsie użytkownika lub utrwalił. W tej sekcji przeanalizowano oba zastosowania. Omówiono również, jak można obsługiwać różnice stref czasowych i operacji arytmetycznych podczas pracy z datami i godzinami.

### <a name="display-dates-and-times"></a>Wyświetlanie dat i godzin

Zazwyczaj, gdy daty i godziny są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury użytkownika, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> który jest <xref:System.Globalization.DateTimeFormatInfo> zdefiniowany przez `CultureInfo.CurrentCulture.DateTimeFormat` właściwość i przez obiekt zwrócony przez właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty przy użyciu dowolnej z następujących metod:

- Metoda bez <xref:System.DateTime.ToString?displayProperty=nameWithType> parametrów

- Metoda, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> która zawiera ciąg formatu

- Metoda bez <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> parametrów

- Przycisk <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, który zawiera ciąg formatu

- Funkcja [formatowania kompozytowego,](../../../docs/standard/base-types/composite-formatting.md) gdy jest używana z datami

Poniższy przykład wyświetla dane o wschodzie i zachodzie słońca dwa razy dla 11 października 2012. Najpierw ustawia obecną kulturę na chorwacką (Chorwację), a następnie na angielski (Wielka Brytania). W każdym przypadku daty i godziny są wyświetlane w formacie, który jest odpowiedni dla tej kultury.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Utrwalić daty i godziny

Nigdy nie należy utrwalić dane daty i godziny w formacie, który może się różnić w zależności od kultury. Jest to typowy błąd programowania, który powoduje uszkodzenie danych lub wyjątek w czasie wykonywania. Poniższy przykład serializuje dwie daty, 9 stycznia 2013 i 18 sierpnia 2013 r., jako ciągi przy użyciu konwencji formatowania kultury angielskiej (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu konwencji kultury angielski (Stany Zjednoczone), jest pomyślnie przywracany. Jednak gdy jest pobierana i analizowana przy użyciu konwencji kultury angielskiej (Zjednoczone Królestwo), pierwsza data jest błędnie interpretowana jako 1 września, a druga nie przeanalizuje, ponieważ kalendarz gregoriański nie ma osiemnastego miesiąca.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Ten problem można uniknąć na trzy sposoby:

- Serializuj datę i godzinę w formacie binarnym, a nie jako ciąg znaków.

- Zapisz i przeanalizować reprezentację ciągu daty i godziny przy użyciu niestandardowego ciągu formatu, który jest taki sam, niezależnie od kultury użytkownika.

- Zapisz ciąg, używając konwencji formatowania kultury niezmiennej.

Poniższy przykład ilustruje ostatnie podejście. Używa konwencji formatowania kultury niezmiennej zwracanej przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwość statyczną.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serializacja i świadomość stref czasowych

Wartość daty i godziny może mieć wiele interpretacji, począwszy od czasu ogólnego ("Sklepy otwarte 2 stycznia 2013 r., o godzinie 9:00") do określonego momentu w czasie ("Data urodzenia: 2 stycznia 2013 r. 06:32:00"). Gdy wartość czasu reprezentuje określony moment w czasie i przywrócić go z serializowanej wartości, należy upewnić się, że reprezentuje ten sam moment w czasie, niezależnie od lokalizacji geograficznej użytkownika lub strefy czasowej.

Poniższy przykład ilustruje ten problem. Zapisuje pojedynczą lokalną wartość daty i godziny jako ciąg w trzech [standardowych formatach](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" dla ogólnej daty długiej godziny, "s" dla posortowalnej daty / godziny i "o" dla daty/godziny podróży w obie strony), a także w formacie binarnym.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Po przywróceniu danych w systemie w tej samej strefie czasowej co system, w którym został serializowany, wartości dat i godzin aserializowanych dokładnie odzwierciedlają oryginalną wartość, jak pokazuje dane wyjściowe:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Jednak jeśli przywrócisz dane w systemie w innej strefie czasowej, tylko wartość daty i godziny, która została sformatowana za pomocą standardowego ciągu formatu "o" (w obie strony), zachowuje informacje o strefie czasowej i w związku z tym reprezentuje ten sam moment w czasie. Oto dane wyjściowe po przywróceniu danych daty i godziny w systemie w strefie czasowej Romance Standard:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Aby dokładnie odzwierciedlić wartość daty i godziny, która reprezentuje pojedynczy moment czasu, niezależnie od strefy czasowej systemu, w którym dane są deserializowane, można wykonać dowolną z następujących czynności:

- Zapisz wartość jako ciąg, używając standardowego ciągu formatu "o" (w obie strony). Następnie deserialize go w systemie docelowym.

- Przekonwertuj go na UTC i zapisz jako ciąg, używając standardowego ciągu formatu "r" (RFC1123). Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

- Przekonwertuj go na utc i zapisz go jako ciąg, używając standardowego ciągu formatu "u" (uniwersalny sortowalny). Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

- Przekonwertuj go na UTC i zapisz go w formacie binarnym. Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

Poniższy przykład ilustruje każdą technikę.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Gdy dane są serializowane w systemie w strefie czasowej Standard Pacyfiku i deserializowane w systemie w strefie czasowej Romance Standard, w przykładzie są wyświetlane następujące dane wyjściowe:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Aby uzyskać więcej informacji, zobacz [Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Wykonywanie arytmetyki daty i godziny

Zarówno <xref:System.DateTime> typy, jak i <xref:System.DateTimeOffset> typy obsługują operacje arytmetyczne. Można obliczyć różnicę między dwiema wartościami daty lub dodać lub odjąć określone interwały czasowe do lub od wartości daty. Jednak operacje arytmetyczne na wartości daty i godziny nie biorą pod uwagę stref czasowych i reguł dostosowania strefy czasowej. Z tego powodu arytmetyka daty i godziny wartości reprezentujących momenty w czasie może zwracać niedokładne wyniki.

Na przykład przejście z czasu standardowego Pacyfiku do czasu letniego pacyfiku następuje w drugą niedzielę marca, czyli 10 marca w roku 2013. Jak pokazano w poniższym przykładzie, jeśli zostanie obliczona data i godzina, która jest 48 godzin po 9 marca 2013 r. o godzinie 10:30. w systemie w strefie czasowej Standard pacyfiku, wynik, 11 marca 2013 o godzinie 10:30, nie uwzględnia interwencji w zakresie dostosowania czasu.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Aby upewnić się, że operacja arytmetyczna w wartościach daty i godziny daje dokładne wyniki, wykonaj następujące kroki:

1. Konwertowanie czasu w źródłowej strefie czasowej na utc.

2. Wykonaj operację arytmetyczną.

3. Jeśli wynik jest wartością daty i godziny, przekonwertuj go z czasu UTC na czas w źródłowej strefie czasowej.

Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że następujące trzy kroki, aby poprawnie dodać 48 godzin do 9 marca 2013 o godzinie 10:30.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Używanie nazw zależnych od kultury dla elementów daty

Aplikacja może być konieczne wyświetlenie nazwy miesiąca lub dnia tygodnia. Aby to zrobić, kod, taki jak następujące jest wspólne.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Jednak ten kod zawsze zwraca nazwy dni tygodnia w języku angielskim. Kod, który wyodrębnia nazwę miesiąca jest często jeszcze bardziej nieelastyczny. Często zakłada dwunastomiesięczny kalendarz z nazwami miesięcy w określonym języku.

Za pomocą [niestandardowych ciągów formatu daty](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) <xref:System.Globalization.DateTimeFormatInfo> i godziny lub właściwości obiektu, jest łatwe wyodrębnianie ciągów, które odzwierciedlają nazwy dni tygodnia lub miesięcy w kulturze użytkownika, jak pokazano w poniższym przykładzie. Zmienia obecną kulturę na francuską (Francja) i wyświetla nazwę dnia tygodnia i nazwę miesiąca dla 1 lipca 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Wartości liczbowe

Obsługa liczb zależy od tego, czy są one wyświetlane w interfejsie użytkownika lub utrwalił. W tej sekcji przeanalizowano oba zastosowania.

> [!NOTE]
> W operacjach analizy i formatowania program .NET rozpoznaje tylko podstawowe znaki łacińskie od 0 do 9 (Od U+0030 do U+0039) jako cyfry.

### <a name="display-numeric-values"></a>Wyświetlanie wartości liczbowych

Zazwyczaj, gdy numery są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury użytkownika, który <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jest zdefiniowany przez właściwość i przez <xref:System.Globalization.NumberFormatInfo> obiekt zwrócony przez `CultureInfo.CurrentCulture.NumberFormat` właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty przy użyciu dowolnej z następujących metod:

- Metoda bezparametrów `ToString` dowolnego typu numerycznego

- Metoda `ToString(String)` dowolnego typu liczbowego, która zawiera ciąg formatu jako argument

- Funkcja [formatowania kompozytowego,](../../../docs/standard/base-types/composite-formatting.md) gdy jest używana z wartościami liczbowymi

Poniższy przykład pokazuje średnią temperaturę miesięcznie w Paryżu, Francja. Najpierw ustawia bieżącą kulturę na francuską (Francja) przed wyświetleniem danych, a następnie ustawia ją na język angielski (Stany Zjednoczone). W każdym przypadku nazwy miesięcy i temperatury są wyświetlane w formacie odpowiednim dla tej kultury. Należy zauważyć, że obie kultury używają różnych separatorów dziesiętnych w wartości temperatury. Należy również zauważyć, że w przykładzie użyto niestandardowego ciągu "MMMM" daty i godziny formatu, aby wyświetlić pełną nazwę miesiąca i że przydziela <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> odpowiednią ilość miejsca dla nazwy miesiąca w ciągu wyników, określając długość nazwy najdłuższego miesiąca w tablicy.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Utrwalanie wartości liczbowych

Nigdy nie należy utrzymywać dane liczbowe w formacie specyficznym dla kultury. Jest to typowy błąd programowania, który powoduje uszkodzenie danych lub wyjątek w czasie wykonywania. Poniższy przykład generuje dziesięć losowych liczb zmiennoprzecinkowych, a następnie serializuje je jako ciągi, używając konwencji formatowania kultury angielskiej (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu konwencji kultury angielski (Stany Zjednoczone), jest pomyślnie przywracany. Jednak gdy jest pobierana i analizowana przy użyciu konwencji kultury francuskiej (Francja), żadna z liczb nie może być przeanalizowana, ponieważ kultury używają różnych separatorów dziesiętnych.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Aby uniknąć tego problemu, można użyć jednej z następujących technik:

- Zapisz i przeanalizować reprezentację ciągu liczby przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.

- Zapisz liczbę jako ciąg, używając konwencji formatowania kultury niezmiennej, która jest <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zwracana przez właściwość.

- Serializuj liczbę w formacie binarnym zamiast ciągu.

Poniższy przykład ilustruje ostatnie podejście. Serializuje tablicy <xref:System.Double> wartości, a następnie deserializes i wyświetla je przy użyciu konwencji formatowania angielski (Stany Zjednoczone) i francuski (Francja) kultur.

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Serializacja wartości waluty jest szczególnym przypadkiem. Ponieważ wartość waluty zależy od jednostki waluty, w której jest wyrażona; nie ma sensu traktować go jako niezależnej wartości liczbowej. Jeśli jednak wartość waluty zostanie zapisana jako sformatowany ciąg zawierający symbol waluty, nie będzie można jej deserializować w systemie, którego domyślna kultura używa symbolu innej waluty, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Zamiast tego należy serializować wartość liczbową wraz z niektórych informacji kulturowych, takich jak nazwa kultury, tak aby wartość i jej symbol waluty mogą być deserializowane niezależnie od bieżącej kultury. Poniższy przykład robi to, `CurrencyValue` definiując strukturę <xref:System.Decimal> z dwoma członkami: wartość i nazwa kultury, do której należy wartość.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Praca z ustawieniami specyficznymi dla kultury

W .NET <xref:System.Globalization.CultureInfo> klasa reprezentuje określonej kultury lub regionu. Niektóre z jego właściwości zwracają obiekty, które zawierają określone informacje o pewnym aspekcie kultury:

- Właściwość <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.CompareInfo> obiekt, który zawiera informacje o tym, jak kultura porównuje i porządkuciągi.

- Właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.DateTimeFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używane w formatowaniu danych daty i godziny.

- Właściwość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używane w formatowaniu danych liczbowych.

- Właściwość <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.TextInfo> obiekt, który zawiera informacje o systemie pisania kultury.

Ogólnie rzecz biorąc nie należy wprowadzać żadnych <xref:System.Globalization.CultureInfo> założeń dotyczących wartości określonych właściwości i ich powiązanych obiektów. Zamiast tego należy wyświetlić dane specyficzne dla kultury jako mogąbyć zmiany, z następujących powodów:

- Poszczególne wartości właściwości mogą ulec zmianie i poprawce wraz z urazem, gdy dane są korygowane, dostępne stają się lepsze dane lub zmieniają się konwencje specyficzne dla kultury.

- Poszczególne wartości właściwości mogą się różnić w zależności od wersji programu .NET lub wersji systemu operacyjnego.

- .NET obsługuje kultury wymiany. Umożliwia to zdefiniowanie nowej kultury niestandardowej, która uzupełnia istniejące kultury standardowe lub całkowicie zastępuje istniejącą kulturę standardową.

- W systemach Windows użytkownik może dostosować ustawienia specyficzne dla kultury za pomocą aplikacji **Region i Język** w Panelu sterowania. Podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu, można określić, czy odzwierciedla te dostosowania użytkownika, wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora. Zazwyczaj w przypadku aplikacji dla użytkowników końcowych należy przestrzegać preferencji użytkownika, aby użytkownikowi przedstawiono dane w formacie, którego oczekują.

## <a name="see-also"></a>Zobacz też

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
