---
title: Dokumentowanie kodu za pomocą komentarzy XML
description: Dowiedz się, jak udokumentować kod za pomocą komentarzy dokumentacji XML i generować plik dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: b6744921f4703f53a16b6bdadcfbf375c2fb3332
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104771"
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentowanie kodu za pomocą komentarzy XML

Komentarze dokumentacji XML są specjalnym rodzajem komentarza, który został dodany powyżej definicji dowolnego typu lub elementu członkowskiego zdefiniowanego przez użytkownika.
Są one specyficzne, ponieważ mogą być przetwarzane przez kompilator w celu wygenerowania pliku dokumentacji XML w czasie kompilacji.
Plik XML wygenerowany przez kompilator może być dystrybuowany wraz z zestawem .NET, dzięki czemu program Visual Studio i inne środowisk IDE mogą używać funkcji IntelliSense do wyświetlania szybkich informacji o typach lub elementach członkowskich. Ponadto plik XML mogą być uruchamiane za pomocą takich narzędzi [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do generowania dokumentacja interfejsu API witryn sieci Web.

Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze, są ignorowane przez kompilator.

Plik XML można wygenerować w czasie kompilacji, wykonując jedną z następujących czynności:

- Jeśli tworzysz aplikację przy użyciu platformy .NET Core z wiersza polecenia, możesz dodać [element DocumentationFile](/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` sekcji pliku projektu. csproj. Poniższy przykład generuje plik XML w katalogu projektu z tą samą nazwą pliku głównego co zestaw:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Można również określić dokładną ścieżkę bezwzględną lub względną i nazwę pliku XML. Poniższy przykład generuje plik XML w tym samym katalogu, w którym znajduje się wersja do debugowania aplikacji:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Jeśli tworzysz aplikację przy użyciu programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. W oknie dialogowym właściwości wybierz kartę **kompilacja** i sprawdź **plik dokumentacji XML**. Możesz również zmienić lokalizację, w której kompilator zapisuje plik.

- Jeśli kompilujesz aplikację .NET Framework z wiersza polecenia, należy dodać [opcję kompilatora/doc](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.  

Komentarze dokumentacji XML używają potrójnych ukośników (`///`) i treści komentarzy w formacie XML. Na przykład:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Instruktaż

Zapoznaj się z dokumentem bardzo podstawową bibliotekę matematyczną, aby ułatwić nowym deweloperom zrozumienie/współtworzenie i współdziałanie z innymi programistami.

Oto kod dla prostej biblioteki matematycznej:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Biblioteka Przykładowa obsługuje cztery główne operacje `add`arytmetyczne, `multiply` `subtract`, `divide` oraz `int` typy `double` danych i.

Teraz chcesz mieć możliwość utworzenia dokumentu referencyjnego interfejsu API na podstawie kodu dla deweloperów innych firm, którzy korzystają z biblioteki, ale nie mają dostępu do kodu źródłowego.
Jak wspomniano wcześniej Tagi dokumentacji XML, można użyć w tym celu. Teraz będziesz wprowadzać do standardowych tagów XML obsługiwanych przez C# kompilator.

## <a name="summary"></a>\<summary>

`<summary>` Tag dodaje krótkie informacje dotyczące typu lub składowej.
Pokażę swoje użycie przez dodanie go do `Math` definicji klasy i pierwszej `Add` metody. Śmiało, aby zastosować go do pozostałej części kodu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Tag jest bardzo istotny i zalecamy dołączenie go, ponieważ jego zawartość jest podstawowym źródłem informacji o typie lub elemencie członkowskim w technologii IntelliSense lub dokumentacji interfejsu API.

## <a name="remarks"></a>\<uwagi >

Tag uzupełnia informacje o typach lub elementach członkowskich udostępnianych `<summary>` przez tag. `<remarks>` W tym przykładzie wystarczy dodać go do klasy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

`<returns>` Tag opisuje wartość zwracaną deklaracji metody.
Tak jak wcześniej Poniższy przykład ilustruje `<returns>` tag w pierwszej `Add` metodzie. Można to zrobić w innych metodach.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Tag jest podobny `<returns>` do znacznika, z tą różnicą, że jest używany do właściwości. `<value>`
Zakładając, że w `PI` bibliotecezostaławywołanawłaściwośćstatyczna,Otojakużywaćtegotagu:`Math`

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<przykład >

`<example>` Używasz znacznika, aby dołączyć przykład do dokumentacji XML.
Obejmuje to użycie znacznika podrzędnego `<code>` .

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Tag zachowuje podziały wierszy i wcięcia dla dłuższych przykładów.

## <a name="para"></a>\<para>

`<para>` Tag służy do formatowania zawartości w tagu nadrzędnym. `<para>`jest zwykle używany wewnątrz tagu, takiego jak `<remarks>` lub `<returns>`, aby podzielić tekst na akapity.
Można sformatować zawartość `<remarks>` tagu w definicji klasy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Nadal w temacie formatowania, `<c>` używasz znacznika do oznaczania części tekstu jako kodu.
Jest to takie samo `<code>` , jak tag, ale wbudowane. Jest to przydatne, gdy chcesz pokazać przykładowy kod jako część zawartości znacznika.
Zaktualizujmy dokumentację dla `Math` klasy.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<> wyjątku

Korzystając ze `<exception>` znacznika, poinformuj deweloperów, że metoda może zgłosić określone wyjątki.
Patrząc na `Math` bibliotekę, można zobaczyć, że obie metody `Add` zgłaszają wyjątek w przypadku spełnienia określonego warunku. Chociaż nie jest to oczywiste, jest to, `Divide` że metoda Integer zgłasza również, `b` Jeśli parametr ma wartość zero. Teraz Dodaj dokumentację wyjątku do tej metody.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Ten `cref` atrybut reprezentuje odwołanie do wyjątku, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie. Kompilator wyświetli ostrzeżenie, jeśli nie można rozpoznać jego wartości.

## <a name="see"></a>\<see>

`<see>` Tag umożliwia utworzenie linku kliknięcia do strony dokumentacji dla innego elementu kodu. W następnym przykładzie utworzymy link do kliknięcia między tymi dwoma `Add` metodami.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

Jest to wymagany atrybut, który reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji. `cref`
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.

## <a name="seealso"></a>\<seealso>

Używasz znacznika w taki sam sposób `<see>` jak tag. `<seealso>` Jedyną różnicą jest to, że jej zawartość jest zwykle umieszczana w sekcji "Zobacz też". Tutaj dodamy `seealso` znacznik metody całkowitej `Add` , aby odwołać się do innych metod w klasie, która akceptuje parametry całkowite:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Ten `cref` atrybut reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.

## <a name="param"></a>\<param>

`<param>` Tag służy do opisywania parametrów metody. Oto przykładowa Metoda podwójna `Add` : Parametr opisany w opisie jest określony w **wymaganym** `name` atrybucie.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

Używasz znacznika podobnie jak tag, `<param>` ale dla typu ogólnego lub deklaracji metody, aby opisać parametr generyczny. `<typeparam>`
Dodaj szybką metodę rodzajową do `Math` klasy, aby sprawdzić, czy jedna ilość jest większa niż inna.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref>

Czasami może być w środku opisującym opisywanie metody, która może być `<summary>` tagiem, i można utworzyć odwołanie do parametru. Ten `<paramref>` tag jest świetny dla samego siebie. Zaktualizujmy podsumowanie naszej metody opartej na `Add` podwójnej precyzji. Podobnie jak `<param>` w przypadku znacznika Nazwa parametru jest określona w **wymaganym** `name` atrybucie.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref>

Używasz znacznika podobnie jak tag, `<paramref>` ale dla typu ogólnego lub deklaracji metody, aby opisać parametr generyczny. `<typeparamref>`
Możesz użyć tej samej metody generycznej, która została wcześniej utworzona.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<list>

`<list>` Tag służy do formatowania informacji dokumentacji jako listy uporządkowanej, listy nieuporządkowanej lub tabeli.
Utwórz nieuporządkowaną listę każdej operacji matematycznej obsługiwanej `Math` przez bibliotekę.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Można utworzyć uporządkowaną listę lub tabelę, zmieniając `type` odpowiednio atrybut na `number` lub `table`.

### <a name="putting-it-all-together"></a>Umieszczanie wszystkich razem

Jeśli wykonano ten samouczek i zastosowano znaczniki do kodu w razie potrzeby, kod powinien teraz wyglądać podobnie do poniższego:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z poziomu kodu można wygenerować szczegółową witrynę sieci Web, która została ukończona z kliknięciami odwołania krzyżowego. Ale nastąpiło inne zagadnienie: Twój kod stał się trudno odczytać.
Istnieje dużo informacji do przesiania przez to, że jest to okropnej dla każdego dewelopera, który chce współtworzyć ten kod.
Thankfully istnieje tag XML, który może pomóc Ci w poradzić sobie z:

## <a name="include"></a>\<Uwzględnij >

`<include>` Tag umożliwia odwoływanie się do komentarzy w osobnym pliku XML, który opisuje typy i elementy członkowskie w kodzie źródłowym, zamiast umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.

Teraz można przenieść wszystkie tagi XML do oddzielnego pliku XML o nazwie `docs.xml`. Możesz nawiązać dowolną nazwę pliku.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

W powyższym kodzie XML komentarze dokumentacji każdego członka są wyświetlane bezpośrednio wewnątrz tagu o nazwie po tym, co robią. Możesz wybrać własną strategię.
Teraz, gdy masz Komentarze XML w osobnym pliku, zobaczmy, jak kod może być bardziej czytelny przy użyciu `<include>` tagu:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Jest to możliwe: kod jest z powrotem odczytywany, a informacje o dokumentacji nie zostały utracone.

Ten `file` atrybut reprezentuje nazwę pliku XML zawierającego dokumentację.

Ten `path` atrybut reprezentuje zapytanie [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) do `tag name` elementu obecnego w określonym `file`.

Ten `name` atrybut reprezentuje specyfikator nazwy w tagu, który poprzedza Komentarze.

Atrybut, który może być użyty zamiast `name` reprezentuje identyfikator tagu, który poprzedza Komentarze. `id`

### <a name="user-defined-tags"></a>Tagi zdefiniowane przez użytkownika

Wszystkie Tagi podane powyżej reprezentują te, które są rozpoznawane przez C# kompilator. Jednak użytkownik może definiować własne znaczniki.
Narzędzia takie jak Sandcastle zapewniają obsługę dodatkowych tagów, [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm)takich [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) jak, a nawet obsługują [dokumentowanie przestrzeni nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Niestandardowe i wewnętrzne narzędzia do generowania dokumentacji mogą również być używane ze znacznikami standardowymi i można obsługiwać wiele formatów wyjściowych z formatu HTML do pliku PDF.

## <a name="recommendations"></a>Zalecenia

Dokumentowanie kodu jest zalecane z wielu powodów. Poniżej przedstawiono niektóre najlepsze rozwiązania, ogólne scenariusze przypadków użycia i informacje, które należy znać w przypadku używania tagów dokumentacji XML w C# kodzie.

- Ze względu na spójność wszystkich publicznie widocznych typów i ich członków należy udokumentować. Jeśli to konieczne, zrób wszystko.
- Prywatne elementy członkowskie mogą być również udokumentowane przy użyciu komentarzy XML. Jednak spowoduje to uwidocznienie wewnętrznej (potencjalnie poufnej) pracy biblioteki.
- W przypadku braku systemu operacyjnego typy i ich elementy członkowskie powinny mieć `<summary>` tag, ponieważ jego zawartość jest wymagana przez funkcję IntelliSense.
- Tekst dokumentacji należy napisać przy użyciu kompletnych zdań kończących się pełnym zatrzymywaniem.
- Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji są łączone w jeden wpis dla tego typu.
- Kompilator weryfikuje `<exception>`składnię tagów, `<include>`, `<param>`, `<see>` `<seealso>` i .`<typeparam>`
- Kompilator sprawdza poprawność parametrów zawierających ścieżki plików i odwołania do innych części kodu.

## <a name="see-also"></a>Zobacz także

- [Komentarze dokumentacji XML (C# Przewodnik programowania)](programming-guide/xmldoc/index.md)
- [Zalecane Tagi dla komentarzy do dokumentacjiC# (Przewodnik programowania)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
