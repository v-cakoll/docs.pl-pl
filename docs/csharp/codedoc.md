---
title: Dokumentowanie kodu za pomocą komentarzy XML
description: Dowiedz się, jak udokumentować kod za pomocą komentarzy do dokumentacji XML i wygenerować plik dokumentacji XML w czasie kompilacji.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ed39c4733c36b3932fcb85bf50d4f4c0e53aa6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146320"
---
# <a name="document-your-code-with-xml-comments"></a>Dokumentowanie kodu za pomocą komentarzy XML

Komentarze do dokumentacji XML są specjalnym rodzajem komentarza, dodanego powyżej definicji dowolnego typu zdefiniowanego przez użytkownika lub elementu członkowskiego.
Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.
Plik XML wygenerowany przez kompilator może być rozpowszechniany wraz z zestawem .NET, dzięki czemu visual studio i inne identyfikatory mogą używać intelliSense do pokazywania szybkich informacji o typach lub członkach. Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle,](https://github.com/EWSoftware/SHFB) aby wygenerować witryny referencyjne API.

Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze, są ignorowane przez kompilator.

Plik XML można wygenerować w czasie kompilacji, wykonując jedną z następujących czynności:

- Jeśli tworzysz aplikację z .NET Core z wiersza `GenerateDocumentationFile` polecenia, `<PropertyGroup>` możesz dodać element do sekcji pliku projektu csproj. Ścieżkę do pliku dokumentacji można [ `DocumentationFile` ](/visualstudio/msbuild/common-msbuild-project-properties)również określić bezpośrednio za pomocą elementu . Poniższy przykład generuje plik XML w katalogu projektu o tej samej głównej nazwie pliku co zestaw:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   Jest to równoważne z następującymi kwestiami:

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Jeśli tworzysz aplikację za pomocą programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Właściwości**. W oknie dialogowym właściwości wybierz kartę **Kompilacja** i sprawdź **plik dokumentacji XML**. Można również zmienić lokalizację, do której kompilator zapisuje plik.

- Jeśli kompilacja aplikacji .NET Framework z wiersza polecenia, dodaj [opcję kompilatora -doc](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.  

Komentarze do dokumentacji XML`///`używają potrójnych ukośników do przodu ( ) i treści komentarzy w formacie XML. Przykład:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Przewodnik

Przejdźmy przez dokumentowanie bardzo podstawowej biblioteki matematycznej, aby ułatwić nowym deweloperom zrozumienie/przyczynienie się i korzystanie z niej przez programistów innych firm.

Oto kod prostej biblioteki matematycznej:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Przykładowa biblioteka obsługuje cztery główne operacje `subtract` `multiply`arytmetyczne `int` ( `double` `add`, , i `divide`) i typy danych.

Teraz chcesz mieć możliwość tworzenia dokumentu referencyjnego interfejsu API z kodu dla innych deweloperów, którzy korzystają z biblioteki, ale nie mają dostępu do kodu źródłowego.
Jak wspomniano wcześniej tagów dokumentacji XML można użyć do osiągnięcia tego celu. Teraz zostaniewprowadzony do standardowych tagów XML kompilator C# obsługuje.

## <a name="summary"></a>\<summary>

Tag `<summary>` dodaje krótkie informacje o typie lub elecie członkowskim.
Zademonstruję jego użycie, dodając `Math` go do `Add` definicji klasy i pierwszej metody. Możesz zastosować go do reszty kodu.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

Tag `<summary>` jest ważny i zaleca się dołączenie go, ponieważ jego zawartość jest podstawowym źródłem informacji o typie lub członka w intelliSense lub dokumencie referencyjnym interfejsu API.

## <a name="remarks"></a>\<uwagi>

Tag `<remarks>` uzupełnia informacje o typach `<summary>` lub członkach, które zapewnia tag. W tym przykładzie po prostu dodasz go do klasy.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

Tag `<returns>` opisuje wartość zwracaną deklaracji metody.
Podobnie jak poprzednio, w `<returns>` poniższym `Add` przykładzie przedstawiono tag na pierwszej metody. Możesz zrobić to samo na innych metodach.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Tag `<value>` jest podobny `<returns>` do znacznika, z tą różnicą, że używasz go do właściwości.
Zakładając, `Math` że biblioteka ma `PI`statyczną właściwość o nazwie , oto jak użyć tego tagu:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>\<przykład>

Tag służy `<example>` do dołączania przykładu do dokumentacji XML.
Wiąże się to `<code>` z użyciem tagu podrzędnego.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Znacznik `code` zachowuje podziały wierszy i wcięcia dla dłuższych przykładów.

## <a name="para"></a>\<para>

Tag służy `<para>` do formatowania zawartości w tagu nadrzędnym. `<para>`jest zwykle używany wewnątrz znacznika, na przykład `<remarks>` lub `<returns>`, do dzielenia tekstu na akapity.
Zawartość tagu `<remarks>` dla definicji klasy można sformatować.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Nadal na temat formatowania, używasz `<c>` znacznika do oznaczania części tekstu jako kod.
To jak tag, `<code>` ale wbudowany. Jest to przydatne, gdy chcesz pokazać przykład szybkiego kodu jako część zawartości tagu.
Zaktualizujmy dokumentację `Math` dla klasy.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<> wyjątek

Za pomocą `<exception>` tagu, poinformować deweloperów, że metoda może zgłaszać określone wyjątki.
Patrząc na `Math` bibliotekę, można `Add` zobaczyć, że obie metody zgłosić wyjątek, jeśli określony warunek jest spełniony. Nie jest to jednak tak oczywiste, że metoda całkowita `Divide` również zgłasza, jeśli `b` parametr wynosi zero. Teraz dodaj dokumentację wyjątku do tej metody.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Atrybut `cref` reprezentuje odwołanie do wyjątku, który jest dostępny z bieżącego środowiska kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie. Kompilator wyda ostrzeżenie, jeśli jego wartość nie można rozwiązać.

## <a name="see"></a>\<zobacz>

Tag `<see>` umożliwia utworzenie klikalnego łącza do strony dokumentacji dla innego elementu kodu. W następnym przykładzie utworzymy klikalne łącze `Add` między tymi dwiema metodami.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

Jest `cref` **to wymagany** atrybut, który reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny z bieżącego środowiska kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie.

## <a name="seealso"></a>\<>

Tag użyje go `<seealso>` w taki `<see>` sam sposób, jak tag. Jedyną różnicą jest to, że jego zawartość jest zazwyczaj umieszczana w sekcji "Zobacz też". W tym miejscu `seealso` dodamy znacznik metody `Add` całkowitej, aby odwołać się do innych metod w klasie, które akceptują parametry całkowite:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Atrybut `cref` reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny z bieżącego środowiska kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie.

## <a name="param"></a>\<param>

Tag służy `<param>` do opisywania parametrów metody. Oto przykład na double `Add` metody: Parametr tag opisuje jest określony w **wymaganym** `name` atrybutem.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<> typeparam

Tag `<typeparam>` jest używany `<param>` tak jak tag, ale dla deklaracji typu ogólnego lub metody do opisania parametru ogólnego.
Dodaj szybką metodę `Math` rodzajową do klasy, aby sprawdzić, czy jedna ilość jest większa niż inna.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref>

Czasami może być w środku opisujące, co metoda `<summary>` robi w co może być tag i może chcesz odwołać się do parametru. Tag `<paramref>` jest świetny tylko do tego. Zaktualizujmy podsumowanie naszej metody `Add` podwójnej. Podobnie `<param>` jak tag, nazwa parametru jest określona w **wymaganym** `name` atrybucie.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typparamref>

Tag `<typeparamref>` jest używany `<paramref>` tak jak tag, ale dla deklaracji typu ogólnego lub metody do opisania parametru ogólnego.
Można użyć tej samej metody ogólnej, która została utworzona wcześniej.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<> listy

Tag służy `<list>` do formatowania informacji o dokumentacji jako uporządkowanej listy, nieuporządkowanej listy lub tabeli. Zrób nieuporządkowaną listę wszystkich operacji `Math` matematycznych, które obsługuje biblioteka.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Można spoinować listę lub tabelę, zmieniając `type` atrybut odpowiednio na `number` lub `table`, .

## <a name="inheritdoc"></a>\<> dziedziczenia

Tag służy `<inheritdoc>` do dziedziczenia komentarzy XML z klas podstawowych, interfejsów i podobnych metod. Eliminuje to niepożądane kopiowanie i wklejanie zduplikowanych komentarzy XML i automatycznie synchronizuje komentarze XML.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Zebranie wszystkich elementów

Jeśli w razie potrzeby zastosowano ten samouczek i zastosowano tagi do kodu, kod powinien teraz wyglądać podobnie do następującego:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z kodu można wygenerować szczegółową stronę internetową dokumentacji wraz z klikalnymi odsyłaczem. Ale masz do czynienia z innym problemem: twój kod stał się trudny do odczytania.
Jest tak wiele informacji, aby przesiać przez to, że to będzie koszmar dla każdego dewelopera, który chce przyczynić się do tego kodu.
Na szczęście istnieje tag XML, który może pomóc ci poradzić sobie z tym:

## <a name="include"></a>\<obejmują>

Tag `<include>` umożliwia odwoływanie się do komentarzy w oddzielnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do umieszczania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.

Teraz przeniesiesz wszystkie znaczniki XML do oddzielnego `docs.xml`pliku XML o nazwie . Możesz nazwać plik, co chcesz.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

W powyższym pliku XML komentarze dokumentacji każdego członka są wyświetlane bezpośrednio wewnątrz tagu o nazwie po tym, co robią. Możesz wybrać własną strategię.
Teraz, gdy masz komentarze XML w osobnym pliku, zobaczmy, jak kod `<include>` może być bardziej czytelny za pomocą tagu:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

I masz to: nasz kod powraca do czytelni i żadne informacje o dokumentacji nie zostały utracone.

Atrybut `file` reprezentuje nazwę pliku XML zawierającego dokumentację.

Atrybut `path` reprezentuje kwerendę [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) `tag name` do teraźniejszości w `file`określonym .

Atrybut `name` reprezentuje specyfikator nazw w tagu, który poprzedza komentarze.

Atrybut, `id` który może być używany `name`w miejsce , reprezentuje identyfikator tagu, który poprzedza komentarze.

### <a name="user-defined-tags"></a>Tagi zdefiniowane przez użytkownika

Wszystkie znaczniki opisane powyżej reprezentują te, które są rozpoznawane przez kompilator C#. Jednak użytkownik może swobodnie definiować własne tagi.
Narzędzia takie jak Sandcastle przynieść wsparcie dla dodatkowych tagów, takich jak [ \<>zdarzeń](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) i [ \<>pamiętać, ](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)a nawet wsparcie [dokumentowania przestrzeni nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Niestandardowe lub w domu narzędzia do generowania dokumentacji mogą być również używane ze standardowymi tagami i wiele formatów wyjściowych od HTML do PDF mogą być obsługiwane.

## <a name="recommendations"></a>Zalecenia

Dokumentowanie kodu jest zalecane z wielu powodów. Oto niektóre najlepsze rozwiązania, scenariusze przypadków użycia ogólnego i rzeczy, które należy wiedzieć podczas używania tagów dokumentacji XML w kodzie Języka C#.

- W celu zachowania spójności należy udokumentować wszystkie publicznie widoczne typy i ich elementy członkowskie. Jeśli musisz to zrobić, zrób to wszystko.
- Członkowie prywatni mogą być również dokumentowane za pomocą komentarzy XML. Jednak to naraża wewnętrzne (potencjalnie poufne) funkcjonowanie biblioteki.
- Co najmniej, typy i ich członkowie `<summary>` powinni mieć tag, ponieważ jego zawartość jest potrzebna dla IntelliSense.
- Tekst dokumentacji powinien być napisany przy użyciu pełnych zdań kończących się pełnymi zatrzymaniami.
- Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji zostaną połączone w jeden wpis dla tego typu.
- Kompilator weryfikuje `<exception>`składnię `<param>`, `<seealso>` `<include>`, `<typeparam>` , `<see>`, i tagów.
- Kompilator sprawdza poprawność parametrów, które zawierają ścieżki plików i odwołania do innych części kodu.

## <a name="see-also"></a>Zobacz też

- [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](programming-guide/xmldoc/index.md)
- [Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
