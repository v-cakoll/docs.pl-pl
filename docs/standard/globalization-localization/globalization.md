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
ms.openlocfilehash: 2f3bf29b9b4d216483ea0c81cc787c80fc8b9e6f
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453362"
---
# <a name="globalization"></a>Globalizacja
Globalizacja obejmuje projektowania i opracowywania aplikacji gotowej dla całego świata, która obsługuje dane regionalne i zlokalizowane interfejsy dla użytkowników w wielu kulturach. Przed rozpoczęciem fazy projektowania, należy określić, które kultury Twoja aplikacja będzie obsługiwać. Mimo że aplikacja jest przeznaczona na jednej kulturze lub regionie jako domyślnej, można projektować i zapisać go tak, aby łatwo mogła zostać rozszerzona do użytkowników innych kultur lub regionów.  
  
 Jako programiści wszyscy mamy założenia dotyczące interfejsów użytkownika i danych, które są tworzone przez nasze kultury. Na przykład dla anglojęzycznego dewelopera w Stanach Zjednoczonych serializacja danych daty i godziny jako ciąg w formacie `MM/dd/yyyy hh:mm:ss` wydaje się całkowicie uzasadnione. Jednakże podczas deserializacji tego ciągu w systemie w innej kulturze będzie prawdopodobnie zgłaszany <xref:System.FormatException> wyjątek lub generowane niedokładne dane. Globalizacja pozwala nam identyfikować takie założenia specyficzne dla kultury i upewnij się, że nie wpływają na projekt lub kod naszej aplikacji.  
  
 W poniższych sekcjach omówiono niektóre z najważniejszych problemów, które należy wziąć pod uwagę i najlepsze rozwiązania, które można zastosować podczas obsługi ciągów, dat i wartości czasu oraz wartości liczbowych w aplikacji zglobalizowanej.  
  
-   [Obsługa ciągów](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Użyj wewnętrznie Unicode](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Użyj plików zasobów](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Wyszukiwanie i porównywanie ciągów ](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Testowanie ciągów pod kątem równości](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Szeregowanie i sortowania ciągów ](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Unikaj łączenia ciągów](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Obsługa daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Przechowywanie daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Wyświetlanie daty i godziny](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Serializacja i świadomości strefy czasowej](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Data i czas operacji arytmetycznych](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Obsługa wartości numerycznych](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Wyświetlanie wartości numerycznych](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Przechowywanie wartości numerycznych](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Praca z ustawieniami specyficzne dla kultury](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Obsługa ciągów  
 Obsługa znaków i ciągów jest podstawowym elementem globalizacji, ponieważ każda kultura lub region może używać różnych znaków oraz zestawów znaków i inaczej je sortować. Ta sekcja zawiera zalecenia dotyczące używania ciągów znaków w uniwersalnych aplikacjach.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Użyj wewnętrznie Unicode  
 Domyślnie program .NET Framework używa ciągów Unicode. Ciąg Unicode zawiera zero, co najmniej jeden <xref:System.Char> obiektów, z których każdy reprezentuje jednostkę kodu UTF-16. Brak reprezentację w formacie Unicode prawie każdy znak w każdym zestawie znaków stosowanym na świecie.  
  
 Wiele aplikacji i systemów operacyjnych, łącznie z systemem operacyjnym Windows może równiez używać stron kodowe do reprezentowania zestawów znaków. Strony kodowe zazwyczaj zawierają standardowe wartości ASCII od 0x00 poprzez 0x7F i mapują inne znaki do pozostałych wartości od 0x80 poprzez 0xFF. Interpretacja wartości od 0x80 do 0xFF zależy od konkretnej strony kodowej. W związku z tym należy unikać używania stron kodowych w aplikacji zglobalizowanej, jeśli jest to możliwe.  
  
 Poniższy przykład ilustruje niebezpieczeństwa interpretacji danych strony kodowej, gdy domyślna strona kodowa w systemie różni się od strony kodowej, na którym zapisano dane. (Aby zasymulować ten scenariusz, przykład jawnie określa różne strony kodowe.) Po pierwsze w przykładzie zdefiniowano tablicę, która składa się z wielkich liter alfabetu greckiego. On koduje je w tablicy bajtów przy użyciu kodu strony 737 (MS-DOS Greek) i zapisuje tablicę bajtów w pliku. Jeśli plik jest pobierany i jego tablica bajtowej jest dekodowana przy użyciu strony kodowej 737, zostaną przywrócone oryginalne znaki. Jednakże jeśli plik jest pobierany i jego tablica bajtowej jest dekodowana przy użyciu strony kodowej 1252 (lub Windows-1252, która reprezentuje znaki alfabetu łacińskiego), oryginalne znaki zostaną utracone.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Zastosowanie formatu Unicode zapewnia, że te same jednostki kodu są zawsze mapowane na te same znaki oraz że te same znaki są zawsze mapowane na te same tablice bajtowe.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Użyj plików zasobów  
 Nawet wtedy, gdy jest tworzona aplikacja, która dotyczy pojedynczej kultury lub regionu, należy użyć plików zasobów do przechowywania ciągów i innych zasobów, które są wyświetlane w interfejsie użytkownika. Nigdy nie należy dodawać bezpośrednio w kodzie. Korzystanie z plików zasobów ma szereg zalet:  
  
-   Wszystkie ciągi znajdują się w obrębie jednej lokalizacji. Nie trzeba przeszukiwać kodu źródłowego, aby zidentyfikować ciągi do modyfikacji dla określonego języka lub kultury.  
  
-   Nie ma potrzeby duplikowania ciągów. Deweloperzy, którzy nie korzystają z plików zasobów często zdefiniować te same parametry w wielu plikach kodu źródłowego. Ta duplikacja zwiększa prawdopodobieństwo, że jedna lub więcej wystąpień pominięcia podczas modyfikacji ciągu.  
  
-   W pliku zasobów zamiast przechowywania ich w oddzielnych autonomiczny plik, dzięki czemu mogą być pobierane łatwo można dołączyć zasobów niebędących ciągami, takich jak obrazy lub dane binarne.  
  
 Korzystanie z plików zasobów jest szczególnie przydatne w przypadku tworzenia aplikacji zlokalizowanych. Podczas wdrażania zasobów w zestawach satelickich, środowisko uruchomieniowe języka wspólnego automatycznie wybiera zasób odpowiedni kulturowo w oparciu o bieżącą kulturę Interfejsu użytkownika zgodnie z definicją <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Tak długo, jak zapewnić odpowiedni zasób specyficzny dla kultury oraz poprawne wystąpienia <xref:System.Resources.ResourceManager> obiektu lub użyć silnie typizowanej klasy zasobów, środowisko wykonawcze obsługuje Szczegóły pobierania odpowiednich zasobów.  
  
 Aby uzyskać więcej informacji na temat tworzenia plików zasobów, zobacz [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Aby uzyskać informacje o tworzeniu i wdrażaniu zestawów satelickich, zobacz [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) i [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Wyszukiwanie i porównywanie ciągów  
 Jeśli to możliwe, należy obsługiwać ciągi, a nie ich obsługę jako serię pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów, aby uniknąć problemów z związane z przetwarzaniem znaków łączonych.  
  
> [!TIP]
>  Możesz użyć <xref:System.Globalization.StringInfo> klasy, aby pracować z elementami tekstowymi zamiast pojedynczych znaków w ciągu.  
  
 W wyszukiwaniach i porównaniach ciągów, powszechnym błędem jest traktowanie ciągu jako zbioru znaków, z których każdy jest reprezentowany przez <xref:System.Char> obiektu. W rzeczywistości pojedynczy znak może zostać utworzona przez jeden, dwa lub więcej <xref:System.Char> obiektów. Takie znaki najczęściej znajdują się w ciągach z kultur, w których alfabety składają się ze znaków spoza zakresu znaków Łaciński podstawowy Unicode (U + 0021 do U + 007E). Poniższy przykład próbuje znaleźć indeks znaku LATIN CAPITAL LETTER A WITH GRAVE (U + 00C 0) w ciągu. Jednak ten znak może być reprezentowany na dwa sposoby: jako jedna jednostka kodu (U + 00C 0) lub znak złożony (dwie jednostki kodu: U + 0021 i U + 007E). W tym przypadku znak jest reprezentowany w wystąpieniu ciągu przez dwa <xref:System.Char> obiekty, U + 0021 i U + 007E. Kod przykładowy wywołuje <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> i <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> przeciążenia, aby znaleźć położenie tego znaku w wystąpieniu ciągu, ale te zwracać różne wyniki. Pierwsze wywołanie metody ma <xref:System.Char> argument; go wykonuje porównanie porządkowe i dlatego nie może znaleźć dopasowania. Drugie wywołanie ma <xref:System.String> argument; wykonuje ono zależne od kultury porównanie i dlatego znajduje odpowiednik.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Można uniknąć niektórych niejasności w tym przykładzie (wywołania dwóch podobnych przeciążeń metody zwracają różne wyniki), wywołując przeciążenie obejmujące <xref:System.StringComparison> parametrów, takich jak <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 Jednak wyszukiwania nie zawsze są wrażliwe na ustawienia kulturowe. Jeśli celem wyszukiwania jest podjęcie decyzji zabezpieczeń lub umożliwianie albo uniemożliwianie dostępu do niektórych zasobów, porównanie powinno być porządkowe, zgodnie z opisem w następnej sekcji.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Testowanie ciągów pod kątem równości  
 Jeśli chcesz przetestować dwa ciągi na równość zamiast określać ich porównanie w porządku sortowania użyj <xref:System.String.Equals%2A?displayProperty=nameWithType> metody zamiast metody porównania ciągów, takich jak <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Porównania dla równości są zazwyczaj wykonywane dostęp do niektórych zasobów warunkowo. Na przykład może przeprowadzić porównanie równości, aby zweryfikować hasło lub potwierdź, że plik istnieje. Takie porównania nielingwistyczne powinny zawsze być porządkowe, a nie zależne od kultury. Ogólnie rzecz biorąc, należy wywołać wystąpienie <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> lub metody statycznej <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody z wartością <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> dla ciągów takich jak hasła, a wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla ciągów takich jak nazwy plików lub identyfikatory URI.  
  
 Porównania dla równości niekiedy dotyczą wyszukiwania lub porównań podciągów zamiast wywołań <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. W niektórych przypadkach może użyć wyszukiwania podciągu do określenia, czy podciąg jest równy innemu ciągowi. Jeśli cel tego porównania jest niejęzykowy, wyszukiwanie należy również porządkowe a nie zależne od kultury.  
  
 Poniższy przykład ilustruje niebezpieczeństwo wyszukiwania wrażliwość na ustawienia kulturowe nielingwistyczne danych. `AccessesFileSystem` Metoda jest przeznaczona do Stanów Zjednoczonych zabraniają dostępu do systemu plików dla identyfikatorów URI, które zaczynają się od podciągu "FILE". Aby to zrobić, wykonuje porównanie zależne od kultury, bez uwzględniania wielkości liter początku identyfikatora URI z ciągiem "FILE". Ponieważ identyfikator URI, który uzyskuje dostęp do systemu plików może zaczynać "pliku:" lub "pliku:", niejawne zakłada się, że "i" (U + 0069) jest zawsze litery odpowiednikiem "I" (U + 0049). Jednak w turecki i Azerbejdżański, wersję z wielkimi literami "i" to "İ" (U + 0130). Ze względu na tę rozbieżność porównanie zależne od kultury umożliwia dostęp do systemu plików, czy powinno być zabronione.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Można uniknąć tego problemu, wykonując porównanie porządkowe, które ignoruje wielkość liter, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Szeregowanie i sortowania ciągów  
 Zazwyczaj zamówione ciągi, które mają być wyświetlane w interfejsie użytkownika powinny być sortowane w oparciu o kultury. W większości przypadków takie porównania ciągów są obsługiwane niejawnie przez program .NET Framework po wywołaniu metody, która sortuje ciągi znaków, takich jak <xref:System.Array.Sort%2A?displayProperty=nameWithType> lub <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Domyślnie ciągi są sortowane za pomocą konwencji sortowania bieżącej kultury. Poniższy przykład ilustruje tę różnicę, gdy tablica ciągów są sortowane przy użyciu konwencji kultury angielski (Stany Zjednoczone) i kultury szwedzki (Szwecja).  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Porównania ciągów zależne od kultury jest definiowany przez <xref:System.Globalization.CompareInfo> obiektu, który jest zwracany przez każda kultura <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> właściwości. Porównania ciągów wrażliwość na ustawienia kulturowe, które używają <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążenia metod również użycie <xref:System.Globalization.CompareInfo> obiektu.  
  
 .NET Framework używa tabel do zależnego kultury sortowania danych ciągów. Zawartość tych tabel, które zawierają dane dotyczące wag sortowania i normalizacji ciągów, jest określana przez wersję standard Unicode zaimplementowany przy użyciu określonej wersji programu .NET Framework. Poniższa tabela zawiera listę wersji standardu Unicode implementowanych przez określone wersje programu .NET Framework. Należy zauważyć, że ta lista obsługiwanych wersji standardu Unicode dotyczy znaków porównywanie i sortowanie. nie ma zastosowania do klasyfikacji znaków Unicode w według kategorii. Aby uzyskać więcej informacji, zobacz sekcję "Ciągów i Unicode Standard" w <xref:System.String> artykułu.  
  
|Wersja programu .NET Framework|System operacyjny|Wersja Unicode|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Wszystkie systemy operacyjne|Unicode 4.1|  
|.NET Framework 3.0|Wszystkie systemy operacyjne|Unicode 4.1|  
|Program .NET Framework 3,5|Wszystkie systemy operacyjne|Unicode 4.1|  
|Program .NET Framework 4|Wszystkie systemy operacyjne|Standard Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Standard Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Zestaw znaków Unicode 6.0|  
  
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], porównywanie i sortowanie ciągów zależy od systemu operacyjnego. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systemem [!INCLUDE[win7](../../../includes/win7-md.md)] pobiera dane z własnych tabel, które implementują standard Unicode 5.0. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systemem [!INCLUDE[win8](../../../includes/win8-md.md)] pobiera dane z tabel systemu operacyjnego, które implementują standard Unicode 6.0. Jeśli serializujesz posortowane dane wrażliwe na ustawienia kulturowe, można użyć <xref:System.Globalization.SortVersion> klasę, aby określić, gdy potrzebuje serializowane dane mają być sortowane, tak aby były zgodne z .NET Framework i porządek sortowania systemu operacyjnego. Aby uzyskać przykład, zobacz <xref:System.Globalization.SortVersion> temat poświęcony klasie.  
  
 Jeśli Twoja aplikacja wykonuje rozległe specyficzne dla kultury sortowania danych ciągów, można pracować z <xref:System.Globalization.SortKey> klasy do porównywania ciągów znaków. Klucz sortowania odzwierciedla wagi sortowania specyficzne dla kultury, włącznie z alfabetycznym, sprawy i znaków diakrytycznych określonego ciągu. Ponieważ porównania przy użyciu kluczy sortowania są binarne, są one szybsze niż porównania, które używają <xref:System.Globalization.CompareInfo> obiektu jawnie lub niejawnie. Utwórz klucz sortowania specyficznego dla kultury dla określonego ciągu, przekazując ciąg do <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metody.  
  
 Poniższy przykład jest podobny do poprzedniego przykładu. Jednak zamiast wywołania <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metody, która wywołuje niejawnie <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> definiuje metodę <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementację, która porównuje klucze sortowania, których tworzy wystąpienia i przekazuje do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metody.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Unikaj łączenia ciągów  
 Jeśli to możliwe Unikaj złożonych ciągów, które są kompilowane w czasie wykonywania z wyrażeń połączonych. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają porządek gramatyczny w oryginalnym języku aplikacji, która nie ma zastosowania do innych języków.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Obsługa daty i godziny  
 Jak obsługa daty i godziny zależy od tego, czy są wyświetlane w interfejsie użytkownika czy utrwalone. W tej części są rozpatrywane oba zastosowania. Omówiono również, jak można obsługiwać operacje arytmetyczne i różnice stref czasowych podczas pracy z datami i godzinami.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Wyświetlanie daty i godziny  
 Zazwyczaj, gdy daty i godziny są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury użytkownika, która jest zdefiniowana przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości i <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez `CultureInfo.CurrentCulture.DateTimeFormat` właściwości. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty za pomocą jednej z następujących metod:  
  
-   Bez parametrów <xref:System.DateTime.ToString?displayProperty=nameWithType> — metoda  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Metody, która zawiera ciąg formatu  
  
-   Bez parametrów <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> — metoda  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Który zawiera ciąg formatu  
  
-   [Formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) funkcji, gdy jest używany z datami  
  
 Poniższy przykład wyświetla wschodzie i zachodzie słońca dane dwa razy dla daty 11 października 2012. Najpierw Ustawia bieżącą kulturę na Chorwacką (Chorwacja), a następnie na angielski (Zjednoczone Królestwo). W każdym przypadku daty i godziny są wyświetlane w formacie, który jest odpowiedni dla tej kultury.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Przechowywanie daty i godziny  
 Nigdy nie należy utrwalać danych daty i godziny w formacie, który może się różnić od kultury. Jest to częsty błąd programowania powodujący uszkodzenie danych lub wyjątek czasu wykonywania. Poniższy przykład szereguje dwie daty, 9 stycznia 2013 i 18 sierpnia 2013 r., jako ciągi przy użyciu konwencji formatowania kultury angielski (Stany Zjednoczone). Gdy dane są pobierane i analizowane za pomocą Konwencji kultury angielski (Stany Zjednoczone), są pomyślnie przywracane. Jednakże gdy są pobierane i analizowane za pomocą Konwencji kultury angielski (Zjednoczone Królestwo), pierwsza data jest niewłaściwie interpretowana jako 1 września, a druga nie można przeanalizować ponieważ kalendarz gregoriański nie ma osiemnastego miesiąca.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Można uniknąć tego problemu, w dowolnej z trzech sposobów:  
  
-   Serializuj datę i godzinę w formacie binarnym, a nie jako ciąg.  
  
-   Zapisz i przeanalizuj reprezentację daty i godziny przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.  
  
-   Zapisz ciąg przy użyciu konwencji formatowania kultury niezmiennej.  
  
 Poniższy przykład ilustruje najnowsze podejście. Używa ona Konwencji formatowania z kulturą niezmienną zwróconą przez statyczną <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Serializacja i świadomości strefy czasowej  
 Wartość daty i godziny może mieć wiele interpretacji, począwszy od czasu ogólnego ("sklepy otwierane są 2 stycznia 2013 r. o godzinie 9:00") określony moment w czasie ("Data urodzenia: 2 stycznia 2013 r. o 6:32:00"). Jeśli określony moment w czasie reprezentowany przez wartość czasu i przywracana z serializowanej wartości, należy upewnić się, że stanowi ten sam moment w czasie, niezależnie od lokalizacji geograficznej lub strefy czasowej użytkownika.  
  
 Poniższy przykład ilustruje ten problem. Zapisuje pojedynczy lokalny wartość daty i godziny jako ciąg w trzech [standardowych formatów](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" Ogólne Data Godzina długa, "s" Sortowalna data/godzina i "o" dla przesłania danych Data/godzina) jak również w formacie binarnym.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Po przywróceniu danych w systemie w tej samej strefie czasowej co system, na którym zostały zaszeregowane po deserializacji wartości daty i godziny dokładnie odzwierciedlają wartość pierwotną, tak jak pokazano w danych wyjściowych:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Jednak w przypadku przywracania danych w systemie w innej strefie czasowej, tylko wartości daty i godziny którą sformatowano przy użyciu ciągu formatu standardowego "o" (Runda) zachowuje informacje o strefie czasowej i reprezentuje zatem takie same błyskawiczny w czasie. Oto dane wyjściowe po przywróceniu danych daty i godziny w systemie w strefie Romans (czas standardowy):  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Aby dokładnie odzwierciedlać wartość daty i godziny, która reprezentuje jeden moment w czasie, niezależnie od strefy czasowej systemu, na którym rozszeregowano dane, wykonaj następujące czynności:  
  
-   Zapisz wartość jako ciąg znaków za pomocą ciągu formatu standardowego (konwersji obustronnej) "o". Następnie zdeserializuj ją w systemie docelowym.  
  
-   Przekonwertuj go na UTC i zapisz go jako ciąg znaków za pomocą ciągu formatu standardowego "r" (RFC1123). Następnie zdeserializuj ją w systemie docelowym i przekonwertuj go na czas lokalny.  
  
-   Przekonwertuj go na UTC i zapisz go jako ciąg znaków za pomocą ciągu formatu standardowego "u" (uniwersalny sortowalny). Następnie zdeserializuj ją w systemie docelowym i przekonwertuj go na czas lokalny.  
  
-   Przekonwertuj go na UTC i zapisz go w formacie binarnym. Następnie zdeserializuj ją w systemie docelowym i przekonwertuj go na czas lokalny.  
  
 Poniższy przykład ilustruje każdą z technik.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Gdy dane są szeregowane w systemie w strefie standardowego czasu pacyficznego, a następnie wykonać deserializacji w systemie w strefie Romański czas standardowy, przykładzie są wyświetlane następujące dane wyjściowe:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Aby uzyskać więcej informacji, zobacz [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Wykonywanie działań arytmetycznych daty i czasu  
 Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> typy obsługują operacje arytmetyczne. Można obliczyć różnicę między dwiema wartościami dat lub można dodawać lub odejmować określone odstępy czasu do lub z wartości daty. Jednak operacje arytmetyczne na wartości daty i godziny nie uwzględniają stref czasowych i reguł dopasowania stref czasowych konta. W związku z tym daty i godziny arytmetycznych na wartościach, które reprezentują momenty w czasie może zwracać nieprecyzyjne wyniki.  
  
 Na przykład przejście od standardowego czasu do czasu pacyficznego występuje w drugą niedzielę marca, czyli 10 marca w roku 2013. W poniższym przykładzie ukazuje, że jeśli obliczasz datę i godzinę, która jest 48 godzin od 9 marca 2013 o 10:30:00 w systemie w strefie standardowego czasu pacyficznego wynik 11 marca 2013 r. o 10:30:00, nie przyjmuje pośredniczące uwzględnia czasu interwencji.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Aby upewnić się, że operacja arytmetyczna na wartości daty i godziny tworzy dokładne wyniki, wykonaj następujące kroki:  
  
1.  Konwertuj czas w źródłowej strefie czasowej UTC.  
  
2.  Wykonywanie operacji arytmetycznej.  
  
3.  Jeśli wynik jest wartością daty i godziny, przekonwertuj go z czasu UTC na czas w źródłowej strefie czasowej.  
  
 Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że wykonuje trzy kroki, aby poprawnie dodać 48 godzin do 9 marca 2013 o 10:30:00  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Aby uzyskać więcej informacji, zobacz [wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Korzystając z nazw wrażliwych na ustawienia kulturowe do elementów daty  
 Aplikacja może być konieczne do wyświetlania nazwy miesiąca lub dnia tygodnia. Aby to zrobić, poniższy kod jest wspólne.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Jednak ten kod zawsze zwraca nazwy dni tygodnia w języku angielskim. Kod, który wyodrębnia nazwę miesiąca jest często jeszcze bardziej sztywny. Zakłada się często kalendarz dwunastu miesięcy z nazwami miesięcy w określonym języku.  
  
 Za pomocą [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) lub właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu, można łatwo wyodrębniać ciągi, które odzwierciedlają nazwy dni tygodni lub miesięcy w kulturze użytkownika, tak jak pokazano w poniższym przykładzie. On zmienia bieżącą kultury na francuską (Francja) i wyświetla nazwę dnia tygodnia i nazwa miesiąca dla 1 lipca 2013.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Obsługa wartości numerycznych  
 Obsługa liczb zależy od tego, czy są wyświetlane w interfejsie użytkownika czy utrwalone. W tej części są rozpatrywane oba zastosowania.  
  
> [!NOTE]
>  Podczas analizowania i operacjach formatowania, .NET Framework rozpoznaje tylko podstawowe znaki łacińskie od 0 do 9 (U + 0030 do U + 0039) jako cyfry.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Wyświetlanie wartości numerycznych  
 Zazwyczaj, gdy liczby są wyświetlane w interfejsie użytkownika, należy użyć konwencji formatowania kultury użytkownika, która jest zdefiniowana przez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości i <xref:System.Globalization.NumberFormatInfo> obiektu zwróconego przez `CultureInfo.CurrentCulture.NumberFormat` właściwości. Konwencje formatowania bieżącej kultury są automatycznie używane podczas formatowania daty za pomocą jednej z następujących metod:  
  
-   Bez parametrów `ToString` metoda dowolnego typu liczbowego  
  
-   `ToString(String)` Metoda dowolnego typu liczbowego, który zawiera ciąg formatu jako argument  
  
-   [Formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) funkcji, gdy jest używany z wartościami liczbowymi  
  
 Poniższy przykład wyświetla średnią temperatury miesięczną w Paryżu. Najpierw Ustawia bieżącą kulturę na francuską (Francja) przed wyświetleniem danych, a następnie ustawia angielski (Stany Zjednoczone). W każdym przypadku nazwy miesięcy i temperatury są wyświetlane w formacie, który jest odpowiedni dla tej kultury. Należy pamiętać, że dwie kultury używają różnych separatorów w wartości temperatury. Należy również zauważyć, że w przykładzie użyto "MMMM" Niestandardowa data i godzina, ciąg formatu, aby wyświetlić pełną nazwę miesiąca, i że zapewnia on odpowiednią ilość miejsca dla nazwy miesiąca w ciągu wyniku określając długość najdłuższej nazwy miesiąca w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>tablicy.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Przechowywanie wartości numerycznych  
 Nigdy nie należy utrwalać danych liczbowych w formacie specyficzne dla kultury. Jest to częsty błąd programowania powodujący uszkodzenie danych lub wyjątek czasu wykonywania. Poniższy przykład generuje dziesięć losowych liczb zmiennoprzecinkowych i szereguje je jako ciągi przy użyciu konwencji formatowania kultury angielski (Stany Zjednoczone). Gdy dane są pobierane i analizowane za pomocą Konwencji kultury angielski (Stany Zjednoczone), są pomyślnie przywracane. Jednakże gdy są pobierane i analizowane za pomocą Konwencji kultury francuskiej (Francja), żadnej z liczb można analizować, ponieważ kultura używa innych separatorów dziesiętnych.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 Aby uniknąć tego problemu, można użyć jednej z poniższych metod:  
  
-   Zapisz i przeanalizuj reprezentację liczby w postaci ciągu przy użyciu ciągu formatu niestandardowego, który jest taki sam, niezależnie od kultury użytkownika.  
  
-   Zapisz liczbę jako ciąg przy użyciu konwencji formatowania kultury niezmiennej, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Serializuj liczbę w formacie binarnym zamiast formatu ciągu.  
  
 Poniższy przykład ilustruje najnowsze podejście. To szereguje tablicę <xref:System.Double> wartości, a następnie deserializuje i wyświetla je przy użyciu konwencji formatowania kultury francuski (Francja) i angielski (Stany Zjednoczone).  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Serializacja wartości walut jest przypadkiem szczególnym. Ponieważ wartość waluty zależy od jednostki walutowej, w której jest wyrażona; sens traktowanie jej jako niezależnej wartości liczbowej. Jednakże jeśli wartość waluty zostanie zapisana jako sformatowany ciąg, który zawiera symbol waluty, nie można zdeserializować w systemie, którego domyślna kultura używa innego symbolu waluty, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Zamiast tego należy serializować wartość liczbowa oraz informacje dotyczące kultury, takie jak nazwa kultury, tak aby wartość i symbolu waluty mogą być zdeserializowane niezależnie od bieżącej kultury. Poniższy przykład robi to poprzez zdefiniowanie `CurrencyValue` struktury z dwoma elementami członkowskimi: <xref:System.Decimal> i nazwą kultury, do którego należy ta wartość.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Praca z ustawieniami specyficznymi dla kultury  
 W .NET Framework <xref:System.Globalization.CultureInfo> klasa reprezentuje określoną kulturę lub region. Niektóre właściwości zwracają obiekty, które zawierają szczegółowe informacje dotyczące pewnych aspektów kultury:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Globalization.CompareInfo> obiektu, który zawiera informacje dotyczące sposobu porównywania i porządkowania ciągów w kultury.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Globalization.DateTimeFormatInfo> obiektu, który dostarcza informacje specyficzne dla kultury, używane do formatowania danych daty i godziny.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Globalization.NumberFormatInfo> obiektu, który dostarcza informacje specyficzne dla kultury, używane do formatowania danych liczbowych.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Globalization.TextInfo> systemie pisma obiektu, który dostarcza informacje o kulturze.  
  
 Ogólnie rzecz biorąc, nie należy czynić żadnych założeń o wartościach konkretnych <xref:System.Globalization.CultureInfo> właściwości oraz ich obiektach pokrewnych. Zamiast tego należy wyświetlić dane specyficzne dla kultury mogą ulec zmianie, z tych powodów:  
  
-   Pojedyncze wartości właściwości podlegają zmianie i poprawkom w czasie, ponieważ dane są poprawiane, lepsze dane stają się dostępne lub zmienia się ich Konwencja specyficzne dla kultury.  
  
-   Pojedyncze wartości właściwości mogą się różnić w różnych wersjach wersji .NET Framework lub systemu operacyjnego.  
  
-   .NET Framework obsługuje kultury zamienne. Pozwala na zdefiniowanie nowej niestandardowej kultury, która stanowi uzupełnienie istniejących standardowych kultur lub całkowitą zamianę istniejącej standardowej kultury.  
  
-   Użytkownik może dostosować ustawienia właściwe dla kultury za pomocą **Region i język** aplikacji w Panelu sterowania. Podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu, można określić, czy odzwierciedla te modyfikacje użytkownika, wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora. Zazwyczaj dla aplikacji użytkownika końcowego należy przestrzegać preferencji użytkownika tak, aby użytkownik zobaczy z danymi w formacie, który użytkownik oczekuje.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)  
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
