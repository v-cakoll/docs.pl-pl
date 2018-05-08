---
title: Dokumentowanie kodu za pomocą komentarze XML
description: Dowiedz się, jak dokumentowanie kodu za pomocą komentarze dokumentacji XML i generowania pliku dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1284f179c7debb323ea3bbd302df1f02bf8b31b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentowanie kodu za pomocą komentarze XML

Komentarze dokumentacji XML to specjalny rodzaj, dodano komentarz powyżej definicji typu zdefiniowanego przez użytkownika lub elementu członkowskiego. Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.
Plik XML wygenerowanego przez kompilator mogą być dystrybuowane wraz z zestawu .NET, dzięki czemu program Visual Studio i innych IDEs może używać IntelliSense do wyświetlenia szybkie informacji na temat typów albo elementów członkowskich. Ponadto można uruchomić plik XML za pomocą takich narzędzi jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) można wygenerować odwołania API witryn sieci Web.

Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze są ignorowane przez kompilator.

W czasie kompilacji można wygenerować plik XML, wykonując jedną z następujących czynności:

- Jeśli tworzysz aplikację z platformą .NET Core w wierszu polecenia, można dodać [elementu DocumentationFile](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` sekcji pliku .csproj projektu. Poniższy przykład generuje plik XML w katalogu projektu o takiej samej nazwie głównego pliku zestawu:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Można również określić dokładną bezwzględną ani względną ścieżkę i nazwę pliku XML. Poniższy przykład generuje plik XML w tym samym katalogu co wersja do debugowania aplikacji:

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- Jeśli tworzysz aplikację przy użyciu programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz **właściwości**. W oknie dialogowym właściwości wybierz **kompilacji** i sprawdź **pliku dokumentacji XML**. Możesz również zmienić lokalizację, do której kompilator zapisuje plik. 

- Jeśli kompilacja aplikacji .NET Framework, w wierszu polecenia, należy dodać [/doc — opcja kompilatora](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.  

Potrójna kreska ułamkowa Użyj komentarze dokumentacji XML (`///`) i treść komentarza sformatowany XML. Na przykład:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Wskazówki

Przejdźmy, dokumentowanie biblioteki matematyczne bardzo podstawowe ułatwia nowe deweloperom zrozumieć współtworzenia i deweloperom użycie innych firm.

Oto kod biblioteki matematyczne prosty:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Biblioteka próbki obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.

Teraz chcesz mieć możliwość utworzenia dokument dokumentacja interfejsu API w kodzie dla deweloperów innych firm, którzy używają biblioteki, ale nie mają dostępu do kodu źródłowego.
Jak wspomniano wcześniej tagów dokumentacji XML może być użyty można to osiągnąć, możesz teraz zostaną wprowadzone do standardowych obsługuje kompilatora tagi C# XML.

### <a name="ltsummarygt"></a>&lt;Podsumowanie&gt;

`<summary>` Tagów dodaje krótki informacji na temat typu lub elementu członkowskiego.
I będzie pokazują jego użycie przez dodanie go do `Math` klasy definicji i pierwszy `Add` metody. Możesz także zastosować je do pozostałej części kodu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Tag jest bardzo ważne i zalecane jest uwzględniania go, ponieważ jego zawartość jest podstawowym źródłem informacji typu lub elementu członkowskiego w IntelliSense lub dokument dokumentacja interfejsu API.

### <a name="ltremarksgt"></a>&lt;Uwagi&gt;

`<remarks>` Tag przedstawiono dodatkowe informacje dotyczące typów albo elementów członkowskich który `<summary>` zawiera tag. W tym przykładzie będzie po prostu dodaj ją do klasy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;Zwraca&gt;

`<returns>` Tag opisuje wartość zwracana w deklaracji metody.
Jak wcześniej, poniższy przykład przedstawia `<returns>` tag pierwszego `Add` metody. Możesz to zrobić na innych metod.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` Tag jest podobny do `<returns>` tagów, z wyjątkiem tego, że używasz dla właściwości.
Zakładając, że Twoje `Math` biblioteka ma właściwości statycznej o nazwie `PI`, Oto jak użyje tego tagu:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Przykład&gt;

Możesz użyć `<example>` znacznik w celu uwzględnienia przykładem w dokumentacji XML.
Obejmuje to przy użyciu elementu podrzędnego `<code>` tagu.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Tag zachowuje podziały wiersza i wcięcia dłuższego przykłady.

### <a name="ltparagt"></a>&lt;Para&gt;

Możesz użyć `<para>` znacznik w celu formatowania zawartości w tagu nadrzędnym. `<para>` jest zwykle używany wewnątrz tagu, takich jak `<remarks>` lub `<returns>`, aby podzielić tekst na akapitów.
Zawartość można sformatować `<remarks>` tag definicji klasy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Pracując nadal na temat formatowania, użyj `<c>` tag znakowania część tekstu jako tekstu zawierającego kod.
Przypomina to `<code>` , ale wbudowany tag. Jest przydatne, gdy chcesz pokazać przykładowego kodu szybkie jako część zawartości tagu.
Ta funkcja pozwala zaktualizować dokumentację dla `Math` klasy.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;Wyjątek&gt;

Za pomocą `<exception>` tagu let deweloperów wiedzieć, że metoda może zgłosić określonych wyjątków.
Spojrzenie na Twojej `Math` biblioteki, można stwierdzić, że oba `Add` metody zgłosić wyjątek, jeśli określony warunek jest spełniony. Nie jest tak oczywiste, że liczba całkowita `Divide` metoda zgłasza, a także jeśli `b` parametru wynosi zero. Teraz należy dodać wyjątek dokumentacji do tej metody.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Atrybut reprezentuje odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu. Kompilator będzie ostrzeżenie, jeśli nie można rozpoznać jego wartość.

### <a name="ltseegt"></a>&lt;Zobacz&gt;

`<see>` Tagu umożliwia tworzenie łączem do strony dokumentacji dla innego elementu kodu. W naszym przykładzie dalej, utworzymy łączem między tymi dwoma `Add` metody.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Jest **wymagane** atrybut, który reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny w bieżącym środowisku kompilacji. Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.

### <a name="ltseealsogt"></a>&lt;SeeAlso&gt;

Możesz użyć `<seealso>` tag w taki sam sposób jak `<see>` tagu. Jedyna różnica polega na tym, że jego zawartość jest zwykle umieszczane w sekcji "Zobacz też". W tym miejscu dodamy `seealso` tagu na liczbę całkowitą `Add` metodę, aby odwoływać się inne metody w klasie, które akceptują parametrów całkowitą:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Atrybut reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.

### <a name="ltparamgt"></a>&lt;Param&gt;

Możesz użyć `<param>` tag do opisywania parametry metody. Oto przykład na podwójnego `Add` — metoda: określono parametr tag opisano w **wymagane** `name` atrybutu.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Możesz użyć `<typeparam>` znacznik, podobnie jak `<param>` tag, ale ogólnym typie lub metodzie deklaracje do opisywania parametru ogólnego.
Dodaj szybka metoda ogólna do Twojej `Math` klasę, aby sprawdzić, czy ilości jest większa od innego.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

Czasami może być środku opisujące, w jakie mogą być czego metody `<summary>` tag, a może chcesz odwołać się do parametru. `<paramref>` Tag jest doskonałym rozwiązaniem dla tego właśnie. Załóżmy na podstawie aktualizacji podsumowanie naszych o podwójnej precyzji `Add` metody. Podobnie jak `<param>` określono nazwę parametru w tagu **wymagane** `name` atrybutu.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Możesz użyć `<typeparamref>` znacznik, podobnie jak `<paramref>` tag, ale ogólnym typie lub metodzie deklaracje do opisywania parametru ogólnego.
Można użyć tej samej metody ogólnej utworzonych wcześniej.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Możesz użyć `<list>` tag do dokumentacji informacji o formacie listy uporządkowanej, Lista nieuporządkowana lub tabeli.
Wprowadź nieuporządkowaną listę każdej operacji matematycznych Twojej `Math` obsługuje biblioteki.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Można wprowadzić listy uporządkowanej lub tabeli, zmieniając `type` atrybutu `number` lub `table`odpowiednio.

### <a name="putting-it-all-together"></a>Składanie wszystkiego razem

Jeśli już zostały wykonane w tym samouczku i zastosować znaczniki w kodzie, w miarę potrzeby, kodu powinna wyglądać podobnie do poniższej:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

W kodzie można wygenerować szczegółowa dokumentacja witryny sieci Web z odsyłacze aktywne. Ale jest skierowany w innym problemów z: kod stał się trudny do odczytania.
Ma tak dużej ilości informacji do przesiania, to ma być nightmare dla Każdy deweloper, który chce przyczyniają się do tego kodu. Brak thankfully tagu XML, które mogą pomóc biznesowych w radzeniu sobie z tym:

### <a name="ltincludegt"></a>&lt;include&gt;

`<include>` Należy odwoływać się do komentarzy w osobnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.

Teraz możesz zacząć Przenieś wszystkie tagi XML do oddzielnego pliku XML o nazwie `docs.xml`. Możesz także nazwę pliku dowolne.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

W powyższym kodzie XML każdy element członkowski komentarzy dokumentacji są wyświetlane bezpośrednio wewnątrz tagu o nazwie po ich działania. Możesz wybrać własne strategii. Teraz, gdy masz komentarz XML w osobnym pliku Zobaczmy, jak kod może się bardziej czytelny przy użyciu `<include>` tagu:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

I mają: naszego kodu jest do jest do odczytu i utracono żadnych informacji w dokumentacji. 

`filename` Atrybut reprezentuje nazwę pliku XML zawierającego w dokumentacji.

`path` Atrybutu reprezentuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) kwerendę `tag name` w określonym `filename`.

`name` Atrybut reprezentuje określenie nazwy w tagu poprzedzający komentarze.

`id` Atrybut, którego można użyć zamiast `name` reprezentuje identyfikator tagu poprzedzający komentarze.

### <a name="user-defined-tags"></a>Tagi zdefiniowane przez użytkownika

Wszystkie znaczniki opisanych powyżej reprezentują te, które są rozpoznawane przez kompilator języka C#. Jednak użytkownik jest bezpłatna do zdefiniowania własnych tagów.
Narzędzia, takie jak Sandcastle Przełącz pomocy technicznej dla dodatkowych tagów, takich jak [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) i obsługa nawet [dokumentowanie przestrzenie nazw](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Niestandardowe lub narzędzia generowania dokumentacji wewnętrznych można również używać razem standardowych znaczników i mogą być obsługiwane wielu danych wyjściowych w formacie HTML do pliku PDF.

## <a name="recommendations"></a>Zalecenia

Dokumentowanie kodu jest zalecane z wielu powodów. Jakie następujące przedstawiono najlepsze rozwiązania, ogólne Użyj scenariuszy przypadków i rzeczy, które należy poznać po użyciu dokumentacji XML tagów w kodzie C#.

* Dla spójności wszystkie typy widocznego publicznie i ich elementy Członkowskie powinny być udokumentowane. Jeśli musisz to zrobić, wykonaj wszystkie.
* Prywatne elementy Członkowskie mogą również opisane przy użyciu komentarze XML. Jednak ten opisuje przebiega (potencjalnie poufnych) biblioteki.
* Co najmniej systemu od zera, typy i ich elementy Członkowskie powinny mieć `<summary>` tagu, ponieważ jego zawartość jest wymagane przez funkcję IntelliSense.
* Tekst dokumentacji powinna być zapisana przy użyciu pełnych zdań kończąc stopnie.
* Klasy częściowe są w pełni obsługiwane, a dokumentacji informacji zostanie łączone w pojedynczy wpis dla tego typu.
* Kompilator sprawdza składnię `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` i `<typeparam>` tagów.
- Kompilator sprawdza poprawność parametrów, które zawierają ścieżki pliku i odwołania do innych części kodu.

## <a name="see-also"></a>Zobacz także
[Komentarze dokumentacji XML (C# przewodnik programowania w języku)](programming-guide/xmldoc/xml-documentation-comments.md)

[Tagi zalecane dla komentarzy do dokumentacji (C# przewodnik programowania w języku)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
