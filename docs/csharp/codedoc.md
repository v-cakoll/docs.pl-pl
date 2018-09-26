---
title: Dokumentowanie kodu przy użyciu komentarzy XML
description: Dowiedz się, jak dokumentowanie kodu za pomocą komentarzy dokumentacji XML do generowania pliku dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: e211543a6a5cc5f6f29d8c195492b474eb24a38d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47115097"
---
# <a name="documenting-your-code-with-xml-comments"></a>Dokumentowanie kodu przy użyciu komentarzy XML

Komentarze dokumentacji XML są specjalnym rodzajem komentarz, dodanych wcześniej definicji typu zdefiniowanego przez użytkownika lub elementu członkowskiego.
Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.
Plik XML wygenerowanego przez kompilator mogą być dystrybuowane wraz z Twojego zestawu platformy .NET tak, aby program Visual Studio i innych środowisk IDE umożliwia IntelliSense Wyświetlanie skróconych informacji dotyczących typów ani elementów członkowskich. Ponadto plik XML mogą być uruchamiane za pomocą takich narzędzi [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do generowania dokumentacja interfejsu API witryn sieci Web.

Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze są ignorowane przez kompilator.

Aby wygenerować plik XML w czasie kompilacji, wykonując jedną z następujących czynności:

- Jeśli tworzysz aplikację za pomocą programu .NET Core z poziomu wiersza polecenia, możesz dodać [elementu DocumentationFile](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` sekcji w pliku projektu csproj. Poniższy przykład generuje plik XML w katalogu projektu o takiej samej nazwie głównego pliku zestawu:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   Można również określić dokładną bezwzględną lub względną ścieżkę i nazwę pliku XML. Poniższy przykład generuje plik XML, w tym samym katalogu co wersja do debugowania aplikacji:

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- Jeśli tworzysz aplikację przy użyciu programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. W oknie dialogowym właściwości wybierz **kompilacji** kartę i sprawdź **pliku dokumentacji XML**. Można również zmienić lokalizację, do której kompilator zapisuje plik.

- Jeśli kompilujesz aplikację .NET Framework z poziomu wiersza polecenia Dodaj [/doc — opcja kompilatora](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania kodu.  

Komentarze dokumentacji XML używać Potrójna ukośników (`///`) i XML sformatowane treść komentarza. Na przykład:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Przewodnik

Przejdźmy teraz przez dokumentowanie biblioteki matematyczne wykraczającego poza podstawowe ułatwia zrozumienie współtworzyć także nowych deweloperów i deweloperzy innych firm mogą korzystać.

Oto kod biblioteki matematyczne proste:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Biblioteka przykładowe obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.

Teraz chcesz mieć możliwość tworzenia dokument referencyjny dotyczący interfejsu API z poziomu kodu dla deweloperów innych firm, którzy użyj biblioteki, ale nie masz dostępu do kodu źródłowego.
Jak wspomniano wcześniej tagów dokumentacji XML może służyć do można to osiągnąć, możesz teraz zostaną wprowadzone w standard obsługuje kompilator znaczników języka C# XML.

### <a name="ltsummarygt"></a>&lt;Podsumowanie&gt;

`<summary>` Znacznik dodaje krótki informacji na temat typu lub elementu członkowskiego.
Zademonstruję jego użycie przez dodanie jej do `Math` klasy definicji i pierwszy `Add` metody. Możesz zastosować je do pozostałej części kodu.

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

`<summary>` Tag jest bardzo ważna, a firma Microsoft zaleca, aby uwzględniać go, ponieważ jego zawartość jest podstawowym źródłem informacji typu lub elementu członkowskiego w technologii IntelliSense lub dokument referencyjny dotyczący interfejsu API.

### <a name="ltremarksgt"></a>&lt;Uwagi&gt;

`<remarks>` Tag uzupełnia informacje dotyczące typów ani elementów członkowskich, `<summary>` zawiera tag. W tym przykładzie będzie po prostu dodaj go do klasy.

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a>&lt;Zwraca&gt;

`<returns>` Tagu w tym artykule opisano wartość zwracaną deklaracji metody.
Jak poprzednio, w poniższym przykładzie pokazano `<returns>` tag pierwszego `Add` metody. Możesz tworzyć takie same, o innych metodach.

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` Tag jest podobne do `<returns>` tagów, z tą różnicą, że zostanie on użyty do właściwości.
Zakładając, że Twoje `Math` biblioteki miały statyczny właściwość o nazwie `PI`, poniżej przedstawiono, jak skorzystać z tego tagu:

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a>&lt;Przykład&gt;

Możesz użyć `<example>` tag, aby uwzględnić przykładem w dokumentacji XML.
Wiąże się to przy użyciu elementu podrzędnego `<code>` tagu.

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

`code` Tag zachowuje podziały wierszy i wcięć przykłady dłużej.

### <a name="ltparagt"></a>&lt;para&gt;

Możesz użyć `<para>` tag, aby formatować takiej treści, w ramach jego tagu nadrzędnym. `<para>` jest zazwyczaj używany wewnątrz znacznik, taki jak `<remarks>` lub `<returns>`, aby podzielić tekstu akapitów.
Zawartość można formatować `<remarks>` tag dla swojej definicji klasy.

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a>&lt;c&gt;

Pracując nadal na temat formatowania, użyj `<c>` tag do oznaczania część tekstu jako kod.
Jest on podobny do `<code>` tagu, ale wbudowanego. Może to być przydatne, gdy chcesz wyświetlić przykład szybki kod jako część zawartości tagu.
Zaktualizujmy w dokumentacji dotyczącej `Math` klasy.

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a>&lt;wyjątek&gt;

Za pomocą `<exception>` tagu, umożliwiają deweloperom wiedzieć, czy metoda może zgłosić określonych wyjątków.
Spojrzenie na Twoje `Math` biblioteki, możesz zobaczyć, że oba `Add` metody zgłosić wyjątek, jeśli określony warunek jest spełniony. Nie jest tak oczywiste, że całkowitą `Divide` metoda generuje również Jeśli `b` parametr ma wartość zero. Teraz należy dodać wyjątek dokumentacji do tej metody.

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

`cref` Atrybutu reprezentuje odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu. Kompilator zgłosi ostrzeżenie, jeśli jego wartość nie jest możliwe.

### <a name="ltseegt"></a>&lt;Zobacz&gt;

`<see>` Tagu umożliwia tworzenie łączem do strony dokumentacji dla innego elementu kodu. W naszym następnym przykładzie utworzymy łączem między tymi dwoma `Add` metody.

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` Jest **wymagane** atrybut, który reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.

### <a name="ltseealsogt"></a>&lt;SeeAlso —&gt;

Możesz użyć `<seealso>` tagu w taki sam sposób jak `<see>` tagu. Jedyna różnica polega na tym, że jego zawartość zwykle znajduje się w sekcji "Zobacz też". W tym miejscu dodamy `seealso` tagiem na liczbę całkowitą `Add` metodę, aby odwoływać się do innych metod w klasie, które akceptują parametry liczby całkowitej:

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

`cref` Atrybutu reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.

### <a name="ltparamgt"></a>&lt;param&gt;

Możesz użyć `<param>` tag do opisania parametrów metody. Poniżej przedstawiono przykład podwójnego `Add` metoda: określono parametr, w tym artykule opisano tagu w **wymagane** `name` atrybutu.

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

Możesz użyć `<typeparam>` tag, podobnie jak `<param>` tagu, ale dla ogólnego deklaracji typu lub metody do opisania parametr ogólny.
Szybkie metodę rodzajową, aby dodać swoje `Math` klasy, aby sprawdzić, czy jeden ilość jest większy niż inny.

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

Czasami może być w trakcie opisujące metoda wykonuje w jakie mogą być `<summary>` tagu, na które może chcieć odwołać się do parametru. `<paramref>` Tag jest doskonale sprawdza się właśnie to. Spróbujmy na podstawie aktualizacji podsumowania naszych double `Add` metody. Podobnie jak `<param>` Nazwa parametru jest określona w tagu **wymagane** `name` atrybutu.

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

Możesz użyć `<typeparamref>` tag, podobnie jak `<paramref>` tagu, ale dla ogólnego deklaracji typu lub metody do opisania parametr ogólny.
Można użyć tej samej metody rodzajowej, utworzone wcześniej.

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a>&lt;list&gt;

Możesz użyć `<list>` tag o dokumentacji formatu listy uporządkowanej, listę nieuporządkowaną lub tabeli.
Wprowadź nieuporządkowaną listę każdej operacji matematycznych swoje `Math` biblioteka obsługuje.

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Można wprowadzić uporządkowanej liście lub tabeli, zmieniając `type` atrybutu `number` lub `table`, odpowiednio.

### <a name="putting-it-all-together"></a>Łączenie wszystkiego razem

Jeśli już a następnie w tym samouczku i zastosowano tagów w kodzie, gdy jest to konieczne, kodu powinien teraz wyglądać podobnie do poniższej:

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

W kodzie można wygenerować szczegółową dokumentację witryny sieci Web z odsyłacze możesz klikać. Ale one zmierzyła się z innym problemem: kod stał się trudny do odczytania.
Istnieje wiele informacji do przesiania, że będzie to być okropnej dla każdego dewelopera, który chce przyczyniają się do tego kodu.
Szczęście jest tag XML, które mogą ułatwić pracę z tym:

### <a name="ltincludegt"></a>&lt;include&gt;

`<include>` Znacznik umożliwia Zobacz komentarze w osobnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.

Teraz możesz zacząć przenieść wszystkie tagi XML w osobnym pliku XML o nazwie `docs.xml`. Swobodnie nazwę pliku, co tylko chcesz.

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

W powyższym kodzie XML komentarze dokumentacji każdego elementu członkowskiego są wyświetlane bezpośrednio wewnątrz tagu o nazwie po ich działania. Możesz wybrać własne strategii.
Teraz, gdy komentarz XML w oddzielnym pliku, zobaczmy, jak Twój kod może się bardziej czytelny przy użyciu `<include>` tag:

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

I są dostępne: naszego kodu jest do odczytu i utracono żadnych informacji o dokumentacji.

`filename` Atrybut reprezentuje nazwę pliku XML zawierającego dokumentację.

`path` Atrybutu reprezentuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) zapytania `tag name` obecne w określonym `filename`.

`name` Atrybut reprezentuje określenie nazwy w tagu, który poprzedza komentarze.

`id` Atrybut, który może być używany zamiast `name` reprezentuje identyfikator tagu, który poprzedza komentarze.

### <a name="user-defined-tags"></a>Tagi zdefiniowane przez użytkownika

Wszystkie tagi opisanych powyżej reprezentują te, które są rozpoznawane przez kompilator języka C#. Jednak użytkownik będzie mógł zdefiniować własne tagi.
Narzędzia, takie jak rozwiązania Sandcastle przenieść pomocy technicznej dla dodatkowego tagów, takich jak [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) nawet pomocy technicznej i [dokumentowanie przestrzenie nazw](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Niestandardowy lub narzędzia do generowania dokumentacji wewnętrznych można również za pomocą standardowych tagów i może być obsługiwanych wiele formatów danych wyjściowych z kodu HTML na format PDF.

## <a name="recommendations"></a>Zalecenia

Dokumentowanie kodu jest zalecane w przypadku wielu powodów. Poniżej przedstawiono kilka najlepszych zasad, ogólnych scenariuszy przypadków użycia, rzeczy, które przydatnych podczas korzystając z dokumentacji XML tagów w kodzie języka C#.

* Dla spójności wszystkie publicznie widoczne typy i składowe powinny być udokumentowane. Jeśli musisz to zrobić, wykonaj to wszystko.
* Prywatne elementy członkowskie można również opisane, przy użyciu komentarzy XML. Jednak to uwidacznia przebiega (potencjalnie poufnych) biblioteki.
* W ramach absolutnego minimum, typy i składowe powinny mieć `<summary>` tag, ponieważ jego zawartość jest wymagane dla funkcji IntelliSense.
* Tekst dokumentacji zapisywane są postaci kompletnych zdań, kończąc na stopnie.
* Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji, będą połączone w pojedynczy wpis dla danego typu.
* Kompilator sprawdza składnię `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` i `<typeparam>` tagów.
- Kompilator sprawdza poprawność parametrów, które zawierają ścieżki do plików i odwołań pozwalającą na inne części kodu.

## <a name="see-also"></a>Zobacz także

* [Komentarze dokumentacji XML (C# Programming Guide)](programming-guide/xmldoc/xml-documentation-comments.md)
* [Tagi zalecane dla komentarzy do dokumentacji (C# Programming Guide)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
