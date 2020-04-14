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
ms.openlocfilehash: c08f4309d7673d7e7fb1c6bd84307e4323411d9e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242689"
---
# <a name="globalization"></a>Globalizacja

Globalizacja polega na projektowaniu i opracowywaniu aplikacji gotowej do użycia na całym świecie, która obsługuje zlokalizowane interfejsy i dane regionalne dla użytkowników w wielu kulturach. Przed rozpoczęciem fazy projektowania należy określić, które kultury będzie obsługiwać aplikacji. Mimo że aplikacja jest domyślna dla jednej kultury lub regionu, można ją zaprojektować i zapisać, aby można ją było łatwo rozszerzyć na użytkowników w innych kulturach lub regionach.

Jako deweloperzy wszyscy mamy założenia dotyczące interfejsów użytkownika i danych, które są tworzone przez nasze kultury. Na przykład dla anglojęzycznego dewelopera w Stanach Zjednoczonych serialowanie danych daty `MM/dd/yyyy hh:mm:ss` i godziny jako ciągu w formacie wydaje się całkowicie uzasadnione. Jednak deserializing tego ciągu w systemie w innej kulturze <xref:System.FormatException> może zgłosić wyjątek lub spowodować niedokładne dane. Globalizacja pozwala nam zidentyfikować takie założenia specyficzne dla kultury i upewnić się, że nie mają one wpływu na projekt lub kod naszej aplikacji.

W tym artykule omówiono niektóre z głównych problemów, które należy wziąć pod uwagę i najlepsze rozwiązania, które można wykonać podczas obsługi ciągów, wartości daty i godziny oraz wartości liczbowych w zglobalizowanej aplikacji.

## <a name="strings"></a>Ciągi

Obsługa znaków i ciągów jest centralnym celem globalizacji, ponieważ każda kultura lub region może używać różnych znaków i zestawów znaków i sortować je inaczej. Ta sekcja zawiera zalecenia dotyczące używania ciągów w zglobalizowanych aplikacjach.

### <a name="use-unicode-internally"></a>Używanie unicode wewnętrznie

Domyślnie program .NET używa ciągów Unicode. Ciąg Unicode składa się z zero, jeden lub więcej <xref:System.Char> obiektów, z których każdy reprezentuje jednostkę kodu UTF-16. Istnieje reprezentacja Unicode dla prawie każdego znaku w każdym znaku ustawionym w użyciu na całym świecie.

Wiele aplikacji i systemów operacyjnych, w tym system operacyjny Windows, może również używać stron kodowych do reprezentowania zestawów znaków. Strony kodowe zazwyczaj zawierają standardowe wartości ASCII od 0x00 do 0x7F i mapują inne znaki na pozostałe wartości od 0x80 do 0xFF. Interpretacja wartości od 0x80 do 0xFF zależy od konkretnej strony kodowej. Z tego powodu należy unikać używania stron kodowych w zglobalizowanej aplikacji, jeśli to możliwe.

Poniższy przykład ilustruje niebezpieczeństwa związane z interpretacją danych strony kodowej, gdy domyślna strona kodowa w systemie różni się od strony kodowej, na której dane zostały zapisane. (Aby symulować ten scenariusz, w przykładzie jawnie określa różne strony kodowe). Po pierwsze przykład definiuje tablicę, która składa się z wielkich liter alfabetu greckiego. Koduje je do tablicy bajtów przy użyciu strony kodowej 737 (znanej również jako MS-DOS greek) i zapisuje tablicę bajtów w pliku. Jeśli plik zostanie pobrany, a jego tablica bajtów zostanie zdekodowana przy użyciu strony kodowej 737, oryginalne znaki zostaną przywrócone. Jeśli jednak plik zostanie pobrany, a jego tablica bajtów zostanie zdekodowana przy użyciu strony kodowej 1252 (lub systemu Windows-1252, która reprezentuje znaki alfabetu łacińskiego), oryginalne znaki zostaną utracone.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Użycie Unicode zapewnia, że te same jednostki kodu zawsze mapują na te same znaki i że te same znaki zawsze są mapowane na te same tablice bajtów.

### <a name="use-resource-files"></a>Używanie plików zasobów

Nawet w przypadku tworzenia aplikacji, która jest przeznaczona dla jednej kultury lub regionu, należy użyć plików zasobów do przechowywania ciągów i innych zasobów, które są wyświetlane w interfejsie użytkownika. Nigdy nie należy dodawać ich bezpośrednio do kodu. Korzystanie z plików zasobów ma wiele zalet:

- Wszystkie ciągi znajdują się w jednej lokalizacji. Nie trzeba wyszukiwać w całym kodzie źródłowym, aby zidentyfikować ciągi, aby zmodyfikować dla określonego języka lub kultury.

- Nie ma potrzeby duplikowania ciągów. Deweloperzy, którzy nie używają plików zasobów często definiują ten sam ciąg w wielu plikach kodu źródłowego. To duplikacja zwiększa prawdopodobieństwo, że jedno lub więcej wystąpień zostaną pominięte, gdy ciąg zostanie zmodyfikowany.

- Zasoby niebędące ciągami, takie jak obrazy lub dane binarne, można uwzględnić w pliku zasobów zamiast przechowywania ich w oddzielnym pliku autonomicznym, dzięki czemu można je łatwo pobrać.

Korzystanie z plików zasobów ma szczególne zalety, jeśli tworzysz zlokalizowaną aplikację. Podczas wdrażania zasobów w zestawach satelickich środowiska wykonawczego języka wspólnego automatycznie wybiera zasobów odpowiednich dla kultury na <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> podstawie bieżącej kultury interfejsu użytkownika, zgodnie z definicją właściwości. Tak długo, jak podać odpowiedni zasób specyficzne <xref:System.Resources.ResourceManager> dla kultury i poprawnie utworzyć wystąpienie obiektu lub użyć klasy zasobów silnie typizowane, środowisko wykonawcze obsługuje szczegóły pobierania odpowiednich zasobów.

Aby uzyskać więcej informacji na temat tworzenia plików zasobów, zobacz [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Aby uzyskać informacje na temat tworzenia i wdrażania zestawów satelickich, zobacz [Tworzenie zestawów satelitalnych oraz](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Wyszukiwanie i porównywanie ciągów

Jeśli to możliwe, należy obsługiwać ciągi jako całe ciągi zamiast obsługi ich jako serii pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów, aby zapobiec problemom związanym z analizowaniem połączonych znaków.

> [!TIP]
> <xref:System.Globalization.StringInfo> Klasy można używać do pracy z elementami tekstowymi, a nie z poszczególnymi znakami w ciągu.

W wyszukiwaniach i porównaniach ciągów typowym błędem jest traktowanie ciągu jako kolekcji <xref:System.Char> znaków, z których każdy jest reprezentowany przez obiekt. W rzeczywistości pojedynczy znak może być utworzony przez <xref:System.Char> jeden, dwa lub więcej obiektów. Takie znaki znajdują się najczęściej w ciągach z kultur, których alfabety składają się ze znaków spoza zakresu znaków łacińskich Unicode Basic (Od U +0021 do U +007E). W poniższym przykładzie próbuje znaleźć indeks łacińskiej wielkiej litery A z znakiem GRAVE (U + 00C0) w ciągu. Jednak ten znak może być reprezentowany na dwa różne sposoby: jako pojedyncza jednostka kodu (U + 00C0) lub jako znak złożony (dwie jednostki kodu: U + 0041 i U + 0300). W takim przypadku znak jest reprezentowany w <xref:System.Char> wystąpieniu ciągu przez dwa obiekty, U + 0041 i U + 0300. Przykładowy kod <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> wywołuje <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> i przeciążenia, aby znaleźć położenie tego znaku w wystąpieniu ciągu, ale te zwracają różne wyniki. Pierwsze wywołanie metody <xref:System.Char> ma argument; wykonuje porównanie porządkowe i dlatego nie można znaleźć dopasowania. Drugie wywołanie <xref:System.String> ma argument; wykonuje porównanie zależne od kultury i w związku z tym znajduje dopasowanie.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Można uniknąć niektórych niejednoznaczności w tym przykładzie (wywołania dwóch podobnych przeciążeń metody zwracanie różnych wyników), wywołując przeciążenie, które zawiera <xref:System.StringComparison> parametr, takich jak <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.

Jednak wyszukiwania nie zawsze są wrażliwe na kulturę. Jeśli celem wyszukiwania jest podjęcie decyzji o zabezpieczeniach lub zezwolenie lub nie zezwalanie na dostęp do niektórych zasobów, porównanie powinno być porządkowe, jak omówiono w następnej sekcji.

### <a name="test-strings-for-equality"></a>Ciągi testowe dla równości

Jeśli chcesz przetestować dwa ciągi równości, a nie określić, <xref:System.String.Equals%2A?displayProperty=nameWithType> jak porównują się w <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>kolejności sortowania, użyj metody zamiast metody porównywania ciągów, takiej jak lub .

Porównania równości są zazwyczaj wykonywane w celu uzyskania warunkowego dostępu do niektórych zasobów. Na przykład można wykonać porównanie równości, aby zweryfikować hasło lub potwierdzić, że plik istnieje. Takie porównania nielingwiskowe powinny być zawsze porządkowe, a nie wrażliwe na kulturę. Ogólnie rzecz biorąc należy <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wywołać metodę <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wystąpienia lub metodę <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> statyczną z wartością dla ciągów, takich jak hasła i wartością <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> ciągów, takich jak nazwy plików lub identyfikatory URI.

Porównania równości czasami obejmują wyszukiwania lub porównania podciągów, a nie wywołania <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. W niektórych przypadkach można użyć wyszukiwania podciągów, aby ustalić, czy ten podciąg jest równy innemu ciągowi. Jeśli celem tego porównania jest nielingwistyczna, wyszukiwanie powinno być również porządkowe, a nie wrażliwe na kulturę.

Poniższy przykład ilustruje niebezpieczeństwo wyszukiwania kultury wrażliwe na dane nielingwistyczno.The following example illustrates the danger of a culture-sensitive search on non-linguistic data. Metoda `AccessesFileSystem` ta ma na celu zabronić dostępu do systemu plików dla identyfikatorów URI, które zaczynają się od podciągu "FILE". W tym celu wykonuje uwzględniające kulturę, niewrażliwe na wielkość liter porównanie początku identyfikatora URI z ciągiem "FILE". Ponieważ identyfikator URI, który uzyskuje dostęp do systemu plików, może zaczynać się od "FILE:" lub "file:", niejawne założenie jest takie, że "i" (U+0069) jest zawsze odpowiednikiem małych liter "I" (U +0049). Jednak w języku tureckim i azerbejdżańskim, wielka wersja liter "i" jest "İ" (U + 0130). Z powodu tej rozbieżności porównanie zależne od kultury umożliwia dostęp do systemu plików, gdy powinno być zabronione.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Można uniknąć tego problemu, wykonując porównanie porządkowe, które ignoruje przypadek, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Ciągi porządkowania i sortowania

Zazwyczaj uporządkowane ciągi, które mają być wyświetlane w interfejsie użytkownika powinny być sortowane na podstawie kultury. W przeważającej części takie porównania ciągów są obsługiwane niejawnie przez .NET podczas <xref:System.Array.Sort%2A?displayProperty=nameWithType> wywoływania metody sortowania ciągów, takich jak lub <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Domyślnie ciągi są sortowane przy użyciu konwencji sortowania bieżącej kultury. Poniższy przykład ilustruje różnicę, gdy tablica ciągów jest sortowana przy użyciu konwencji kultury angielskiej (Stany Zjednoczone) i kultury szwedzkiej (Szwecja).

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Porównanie ciągów zależne od <xref:System.Globalization.CompareInfo> kultury jest definiowane przez <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> obiekt, który jest zwracany przez właściwość każdej kultury. Porównania ciągów zależne od <xref:System.String.Compare%2A?displayProperty=nameWithType> kultury, które używają <xref:System.Globalization.CompareInfo> przeciążenia metody również użyć obiektu.

.NET używa tabel do wykonywania sortów wrażliwych na kulturę na danych ciągów. Zawartość tych tabel, które zawierają dane dotyczące wagi sortowania i normalizacji ciągów, jest określana przez wersję standardu Unicode zaimplementowaną przez określoną wersję platformy .NET. W poniższej tabeli wymieniono wersje programu Unicode zaimplementowane przez określone wersje programu .NET Framework i programu .NET Core. Należy zauważyć, że ta lista obsługiwanych wersji Unicode ma zastosowanie tylko do porównywania znaków i sortowania; nie ma zastosowania do klasyfikacji znaków Unicode według kategorii. Aby uzyskać więcej informacji, zobacz sekcję "Ciągi <xref:System.String> i standard Unicode" w artykule.

|Wersja programu .NET Framework|System operacyjny|Wersja Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Wszystkie systemy operacyjne|Unicode 4.1|
|.NET Framework 3.0|Wszystkie systemy operacyjne|Unicode 4.1|
|Program .NET Framework 3,5|Wszystkie systemy operacyjne|Unicode 4.1|
|Program .NET Framework 4|Wszystkie systemy operacyjne|Unicode 5.0|
|Program .NET Framework 4.5 lub nowszy w systemie Windows 7|Unicode 5.0|
|.NET Framework 4.5 i nowsze w systemach operacyjnych Windows 8 i nowszych|Unicode 6.3.0|
|.NET Core (wszystkie wersje)|Zależy od wersji standardu Unicode obsługiwanego przez podstawowy system operacyjny.|

Począwszy od programu .NET Framework 4.5 i we wszystkich wersjach programu .NET Core, porównanie i sortowanie ciągów zależy od systemu operacyjnego. Program .NET Framework 4.5 i nowsze działające w systemie Windows 7 pobierają dane z własnych tabel implementujących unicode 5.0. Program .NET Framework 4.5 lub nowszych działających w systemie Windows 8 i nowszych pobiera dane z tabel systemu operacyjnego implementujących unicode 6.3. W programie .NET Core obsługiwana wersja programu Unicode zależy od podstawowego systemu operacyjnego. Jeśli serializujesz dane posortowane z <xref:System.Globalization.SortVersion> uwzględnieniem kultury, można użyć tej klasy do określenia, kiedy dane szeregowane muszą być sortowane tak, aby były zgodne z programem .NET i kolejnością sortowania systemu operacyjnego. Na przykład zobacz <xref:System.Globalization.SortVersion> temat klasy.

Jeśli aplikacja wykonuje obszerne typy ciągów specyficzne dla <xref:System.Globalization.SortKey> kultury, można pracować z klasy, aby porównać ciągi. Klucz sortowania odzwierciedla wagi sortowania specyficzne dla kultury, w tym wagi alfabetyczne, wielkość liter i wagi diakrytyczne określonego ciągu. Ponieważ porównania przy użyciu kluczy sortowania są binarne, są szybsze niż porównania, które używają <xref:System.Globalization.CompareInfo> obiektu niejawnie lub jawnie. Utworzyć klucz sortowania specyficzne dla kultury dla określonego ciągu, przekazując ciąg do <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metody.

Poniższy przykład jest podobny do poprzedniego przykładu. Jednak zamiast wywoływania <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metody, która niejawnie wywołuje <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> metodę, <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> definiuje implementację, która porównuje klucze sortowania, które wywołuje wystąpienia i przekazuje do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metody.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Unikaj łączenia ciągów

Jeśli w ogóle jest to możliwe, należy unikać używania ciągów kompozytowych, które są budowane w czasie wykonywania z łączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają kolejność gramatyczną w oryginalnym języku aplikacji, który nie ma zastosowania do innych zlokalizowanych języków.

## <a name="handle-dates-and-times"></a>Obsługa dat i godzin

Sposób obsługi wartości daty i godziny zależy od tego, czy są one wyświetlane w interfejsie użytkownika lub utrwalone. W tej sekcji sprawdza się zarówno użycia. Omówiono również, jak można obsługiwać różnice stref czasowych i operacje arytmetyczne podczas pracy z datami i godzinami.

### <a name="display-dates-and-times"></a>Wyświetlanie dat i godzin

Zazwyczaj, gdy daty i godziny są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> użytkownika, który <xref:System.Globalization.DateTimeFormatInfo> jest zdefiniowany przez właściwość i przez obiekt zwrócony `CultureInfo.CurrentCulture.DateTimeFormat` przez właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty przy użyciu dowolnej z następujących metod:

- Metoda bez <xref:System.DateTime.ToString?displayProperty=nameWithType> parametrów

- Metoda, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> która zawiera ciąg formatu

- Metoda bez <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> parametrów

- Ciąg <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>formatu , który zawiera ciąg formatu

- Funkcja [formatowania kompozytowego,](../../../docs/standard/base-types/composite-formatting.md) gdy jest używana z datami

W poniższym przykładzie są wyświetlane dwa razy dane o wschodzie i zachodzie słońca dla 11 października 2012 r. Najpierw ustawia obecną kulturę na chorwacki (Chorwacja), a następnie na angielski (Wielka Brytania). W każdym przypadku daty i godziny są wyświetlane w formacie, który jest odpowiedni dla tej kultury.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Utrwalić daty i godziny

Nigdy nie należy zachowywać danych daty i godziny w formacie, który może się różnić w zależności od kultury. Jest to typowy błąd programowania, który powoduje uszkodzone dane lub wyjątek w czasie wykonywania. Poniższy przykład serializuje dwie daty, 9 stycznia 2013 r. i 18 sierpnia 2013 r. jako ciągi znaków przy użyciu konwencji formatowania kultury języka angielskiego (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu konwencji kultury angielskiej (Stany Zjednoczone), zostanie pomyślnie przywrócone. Jednak po pobraniu i przeanalizowaniu przy użyciu konwencji kultury angielskiej (Wielka Brytania) pierwsza data jest błędnie interpretowana jako 1 września, a druga nie może analizować, ponieważ kalendarz gregoriański nie ma osiemnastego miesiąca.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Ten problem można uniknąć na jeden z trzech sposobów:

- Serializuj datę i godzinę w formacie binarnym, a nie jako ciąg.

- Zapisz i przesiemaj reprezentację ciągu daty i godziny przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.

- Zapisz ciąg przy użyciu konwencji formatowania kultury niezmiennej.

Poniższy przykład ilustruje ostatnie podejście. Używa konwencji formatowania kultury niezmiennej zwracanej przez właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> statyczną.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serializacja i rozpoznawanie stref czasowych

Wartość daty i godziny może mieć wiele interpretacji, od ogólnego czasu ("Sklepy otwarte 2 stycznia 2013 r., o godzinie 9:00") do określonego momentu w czasie ("Data urodzenia: 2 stycznia 2013 r. 6:32:00 rano"). Gdy wartość czasu reprezentuje określony moment w czasie i przywrócić go z wartości serializowanej, należy upewnić się, że reprezentuje ten sam moment w czasie, niezależnie od lokalizacji geograficznej użytkownika lub strefy czasowej.

Poniższy przykład ilustruje ten problem. Zapisuje pojedynczą lokalną wartość daty i godziny jako ciąg w trzech [standardowych formatach](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" dla ogólnej daty długiej, "s" dla sortowania daty/godziny i "o" dla daty/godziny w obie strony), a także w formacie binarnym.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Po przywróceniu danych w systemie w tej samej strefie czasowej co system, w którym został serializowany, wartości daty i godziny deserializowane dokładnie odzwierciedlają oryginalną wartość, jak pokazuje dane wyjściowe:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Jeśli jednak przywrócisz dane w systemie w innej strefie czasowej, tylko wartość daty i godziny, która została sformatowana za pomocą ciągu standardowego formatu "o" (round-trip), zachowuje informacje o strefie czasowej i dlatego reprezentuje ten sam moment w czasie. Oto dane wyjściowe, gdy dane daty i godziny są przywracane w systemie w strefie czasowej Romance Standard:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Aby dokładnie odzwierciedlić wartość daty i godziny, która reprezentuje pojedynczy moment czasu, niezależnie od strefy czasowej systemu, w którym dane są deserializowane, można wykonać dowolną z następujących czynności:

- Zapisz wartość jako ciąg znaków przy użyciu ciągu w formacie standardowym "o" (round-trip). Następnie deserialize go w systemie docelowym.

- Przekonwertować go do UTC i zapisać go jako ciąg przy użyciu ciągu w formacie standardowym "r" (RFC1123). Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

- Przekonwertować go do UTC i zapisać go jako ciąg za pomocą "u" (uniwersalny sortowania) standardowy ciąg formatu. Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

- Przekonwertuj go na UTC i zapisz w formacie binarnym. Następnie deserialize go w systemie docelowym i przekonwertować go na czas lokalny.

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

Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> typy obsługują operacje arytmetyczne. Można obliczyć różnicę między dwiema wartościami daty lub dodać lub odjąć określone przedziały czasu do lub od wartości daty. Jednak operacje arytmetyczne dotyczące wartości daty i godziny nie uwzględniają stref czasowych i reguł korekty strefy czasowej. Z tego powodu arytmetyka daty i godziny na wartości, które reprezentują momenty w czasie może zwrócić niedokładne wyniki.

Na przykład przejście z pacyficznego czasu standardowego do czasu letniego pacyfiku odbywa się w drugą niedzielę marca, czyli 10 marca dla roku 2013. Jak pokazano w poniższym przykładzie, jeśli obliczysz datę i godzinę, która jest 48 godzin po 9 marca 2013 r. o godzinie 10:30. w systemie w strefie czasowej standardu Pacyfiku, wynik, 11 marca 2013 o 10:30, nie uwzględnia interweniującego dostosowania czasu.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Aby upewnić się, że operacja arytmetyczna na wartości daty i godziny daje dokładne wyniki, wykonaj następujące kroki:

1. Konwertuj czas w źródłowej strefie czasowej na UTC.

2. Wykonaj operację arytmetyczną.

3. Jeśli wynik jest wartością daty i godziny, przekonwertuj go z czasu UTC na czas w źródłowej strefie czasowej.

Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że następuje te trzy kroki, aby poprawnie dodać 48 godzin do 9 marca 2013 o 10:30.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Używanie nazw wrażliwych na kulturę dla elementów daty

Aplikacja może wymagać wyświetlenia nazwy miesiąca lub dnia tygodnia. Aby to zrobić, kod, takich jak następujące jest wspólne.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Jednak ten kod zawsze zwraca nazwy dni tygodnia w języku angielskim. Kod, który wyodrębnia nazwę miesiąca jest często jeszcze bardziej nieelastyczny. Często zakłada dwunastomiesięczny kalendarz z nazwami miesięcy w określonym języku.

Za pomocą [niestandardowych ciągów formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) lub właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu, można łatwo wyodrębnić ciągi, które odzwierciedlają nazwy dni tygodnia lub miesięcy w kulturze użytkownika, jak pokazano w poniższym przykładzie. Zmienia bieżącą kulturę na francuski (Francja) i wyświetla nazwę dnia tygodnia i nazwę miesiąca na 1 lipca 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Wartości liczbowe

Obsługa liczb zależy od tego, czy są one wyświetlane w interfejsie użytkownika, czy utrwalone. W tej sekcji sprawdza się zarówno użycia.

> [!NOTE]
> W operacjach analizowania i formatowania .NET rozpoznaje tylko podstawowe znaki łacińskie od 0 do 9 (od U +0030 do U+0039) jako cyfry.

### <a name="display-numeric-values"></a>Wyświetlanie wartości liczbowych

Zazwyczaj, gdy numery są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury użytkownika, który <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jest zdefiniowany przez właściwość i <xref:System.Globalization.NumberFormatInfo> przez obiekt zwrócony `CultureInfo.CurrentCulture.NumberFormat` przez właściwość. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty przy użyciu dowolnej z następujących metod:

- Metoda bez `ToString` parametrów dowolnego typu liczbowego

- Metoda `ToString(String)` dowolnego typu liczbowego, która zawiera ciąg formatu jako argument

- Funkcja [formatowania złożonego,](../../../docs/standard/base-types/composite-formatting.md) gdy jest używana z wartościami liczbowymi

W poniższym przykładzie wyświetlana jest średnia temperatura miesięcznie w Paryżu we Francji. Najpierw ustawia bieżącą kulturę na francuski (Francja) przed wyświetleniem danych, a następnie ustawia go na angielski (Stany Zjednoczone). W każdym przypadku nazwy miesięcy i temperatury są wyświetlane w formacie, który jest odpowiedni dla tej kultury. Należy zauważyć, że dwie kultury używają różnych separatorów dziesiętnych w wartości temperatury. Należy również zauważyć, że w przykładzie użyto niestandardowego ciągu formatu daty i godziny "MMMM", aby wyświetlić pełną nazwę miesiąca i że przydziela odpowiednią <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> ilość miejsca dla nazwy miesiąca w ciągu wyników, określając długość najdłuższej nazwy miesiąca w tablicy.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Utrwalanie wartości liczbowych

Nigdy nie należy utrwalać danych liczbowych w formacie specyficznym dla kultury. Jest to typowy błąd programowania, który powoduje uszkodzone dane lub wyjątek w czasie wykonywania. Poniższy przykład generuje dziesięć losowych liczb zmiennoprzecinkowych, a następnie serializuje je jako ciągi przy użyciu konwencji formatowania kultury języka angielskiego (Stany Zjednoczone). Gdy dane są pobierane i analizowane przy użyciu konwencji kultury angielskiej (Stany Zjednoczone), zostanie pomyślnie przywrócone. Jednak po pobraniu i przeanalizowaniu przy użyciu konwencji kultury francuskiej (Francja) żadna z liczb nie może być analizowana, ponieważ kultury używają różnych separatorów dziesiętnych.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Aby uniknąć tego problemu, można użyć jednej z następujących technik:

- Zapisz i przesiemaj reprezentację ciągu liczby przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.

- Zapisz liczbę jako ciąg przy użyciu konwencji formatowania kultury niezmiennej, która jest <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zwracana przez właściwość.

- Serializuj liczbę w formacie binarnym zamiast w formacie ciągu.

Poniższy przykład ilustruje ostatnie podejście. Serializuje tablicę <xref:System.Double> wartości, a następnie deserializes i wyświetla je przy użyciu konwencji formatowania kultur angielski (Stany Zjednoczone) i francuski (Francja).

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Serializowanie wartości walut jest szczególnym przypadkiem. Ponieważ wartość waluty zależy od jednostki waluty, w której jest wyrażona; nie ma sensu traktować go jako niezależnej wartości liczbowej. Jeśli jednak wartość waluty zostanie zabezpieczona jako sformatowany ciąg zawierający symbol waluty, nie można jej zdesysalializować w systemie, którego domyślna kultura używa innego symbolu waluty, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Zamiast tego należy serializować wartość liczbową wraz z niektórymi informacjami kulturowymi, takimi jak nazwa kultury, tak aby wartość i jej symbol waluty mogły być deserializowane niezależnie od bieżącej kultury. Poniższy przykład powoduje, że `CurrencyValue` przez zdefiniowanie <xref:System.Decimal> struktury z dwóch elementów członkowskich: wartość i nazwę kultury, do której należy wartość.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Praca z ustawieniami specyficznymi dla kultury

W .NET <xref:System.Globalization.CultureInfo> klasa reprezentuje określonej kultury lub regionu. Niektóre z jego właściwości zwracają obiekty, które zawierają określone informacje o pewnym aspekcie kultury:

- Właściwość <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.CompareInfo> obiekt, który zawiera informacje o tym, jak kultury porównuje i porządku ciągi.

- Właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.DateTimeFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używane w formatowaniu danych daty i godziny.

- Właściwość <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który zawiera informacje specyficzne dla kultury używane w formatowaniu danych liczbowych.

- Właściwość <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> zwraca <xref:System.Globalization.TextInfo> obiekt, który zawiera informacje o systemie zapisu kultury.

Ogólnie rzecz biorąc, nie należy wprowadzać <xref:System.Globalization.CultureInfo> żadnych założeń dotyczących wartości określonych właściwości i ich powiązanych obiektów. Zamiast tego należy wyświetlić dane specyficzne dla kultury jako mogą ulec zmianie, z następujących powodów:

- Poszczególne wartości właściwości mogą ulec zmianie i rewizji w czasie, jak dane są korygowane, lepsze dane stają się dostępne lub zmiany konwencji specyficzne dla kultury.

- Poszczególne wartości właściwości mogą się różnić w zależności od wersji platformy .NET lub wersji systemu operacyjnego.

- .NET obsługuje kultury zastępowania. Dzięki temu można zdefiniować nową kulturę niestandardową, która uzupełnia istniejące kultury standardowe lub całkowicie zastępuje istniejącą kulturę standardową.

- W systemach Windows użytkownik może dostosować ustawienia specyficzne dla kultury za pomocą aplikacji **Region i Język** w Panelu sterowania. Podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu, można określić, czy odzwierciedla te dostosowania <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> użytkownika, wywołując konstruktora. Zazwyczaj w przypadku aplikacji użytkownika końcowego należy przestrzegać preferencji użytkownika, tak aby użytkownik był prezentowany z danymi w formacie, którego oczekują.

## <a name="see-also"></a>Zobacz też

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Najważniejsze wskazówki dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
