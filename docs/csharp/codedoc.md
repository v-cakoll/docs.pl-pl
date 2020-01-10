---
title: Dokumentowanie kodu za pomocą komentarzy XML
description: Dowiedz się, jak udokumentować kod za pomocą komentarzy dokumentacji XML i generować plik dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 6aa52030e20f61b26311347a57629658ebe0e609
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713941"
---
# <a name="document-your-code-with-xml-comments"></a>Dokumentowanie kodu za pomocą komentarzy XML

Komentarze dokumentacji XML są specjalnym rodzajem komentarza, który został dodany powyżej definicji dowolnego typu lub elementu członkowskiego zdefiniowanego przez użytkownika.
Są one specyficzne, ponieważ mogą być przetwarzane przez kompilator w celu wygenerowania pliku dokumentacji XML w czasie kompilacji.
Plik XML wygenerowany przez kompilator może być dystrybuowany wraz z zestawem .NET, dzięki czemu program Visual Studio i inne środowisk IDE mogą używać funkcji IntelliSense do wyświetlania szybkich informacji o typach lub elementach członkowskich. Ponadto plik XML mogą być uruchamiane za pomocą takich narzędzi [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do generowania dokumentacja interfejsu API witryn sieci Web.

Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze, są ignorowane przez kompilator.

Plik XML można wygenerować w czasie kompilacji, wykonując jedną z następujących czynności:

- Jeśli tworzysz aplikację przy użyciu platformy .NET Core z wiersza polecenia, możesz dodać element `GenerateDocumentationFile` do sekcji `<PropertyGroup>` pliku projektu. csproj. Możesz również określić ścieżkę do pliku dokumentacji bezpośrednio przy użyciu [elementu`DocumentationFile`](/visualstudio/msbuild/common-msbuild-project-properties). Poniższy przykład generuje plik XML w katalogu projektu z tą samą nazwą pliku głównego co zestaw:

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   Jest to równoważne z następującymi:
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Jeśli tworzysz aplikację przy użyciu programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. W oknie dialogowym właściwości wybierz kartę **kompilacja** i sprawdź **plik dokumentacji XML**. Możesz również zmienić lokalizację, w której kompilator zapisuje plik.

- Jeśli kompilujesz aplikację .NET Framework z wiersza polecenia, Dodaj [opcję kompilatora-doc](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.  

Komentarze dokumentacji XML używają potrójnych ukośników (`///`) i treści komentarza w formacie XML. Na przykład:

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Przewodnik

Zapoznaj się z dokumentem bardzo podstawową bibliotekę matematyczną, aby ułatwić nowym deweloperom zrozumienie/współtworzenie i współdziałanie z innymi programistami.

Oto kod dla prostej biblioteki matematycznej:

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

Biblioteka Przykładowa obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.

Teraz chcesz mieć możliwość utworzenia dokumentu odniesienia interfejsu API z kodu dla deweloperów innych firm, którzy korzystają z biblioteki, ale nie mają dostępu do kodu źródłowego.
Jak wspomniano wcześniej Tagi dokumentacji XML, można użyć w tym celu. Teraz będziesz wprowadzać do standardowych tagów XML obsługiwanych przez C# kompilator.

## <a name="summary"></a>\<summary>

Tag `<summary>` dodaje krótkie informacje dotyczące typu lub składowej.
Pokażę swoje użycie przez dodanie go do definicji klasy `Math` i pierwszej metody `Add`. Śmiało, aby zastosować go do pozostałej części kodu.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

Tag `<summary>` jest bardzo istotny i zalecamy dołączenie go, ponieważ jego zawartość jest podstawowym źródłem informacji o typie lub elemencie członkowskim w technologii IntelliSense lub dokumentacji interfejsu API.

## <a name="remarks"></a>\<uwagi >

Tag `<remarks>` uzupełnia informacje o typach lub elementach członkowskich udostępnianych przez tag `<summary>`. W tym przykładzie wystarczy dodać go do klasy.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a>\<returns>

Tag `<returns>` opisuje wartość zwracaną deklaracji metody.
Tak jak wcześniej Poniższy przykład ilustruje tag `<returns>` na pierwszej `Add` metodzie. Można to zrobić w innych metodach.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a>\<value>

Tag `<value>` jest podobny do tagu `<returns>`, z tą różnicą, że jest używany do właściwości.
Zakładając, że biblioteka `Math` ma właściwość statyczną o nazwie `PI`, poniżej przedstawiono sposób użycia tego tagu:

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a>przykład \<

Używasz znacznika `<example>`, aby dołączyć przykład do dokumentacji XML.
Obejmuje to użycie znacznika `<code>` podrzędnego.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

Tag `code` zachowuje podziały wierszy i wcięcia dla dłuższych przykładów.

## <a name="para"></a>\<para>

Aby sformatować zawartość w tagu nadrzędnym, Użyj znacznika `<para>`. `<para>` jest zwykle używany wewnątrz tagu, takiego jak `<remarks>` lub `<returns>`, aby podzielić tekst na akapity.
Można sformatować zawartość tagu `<remarks>` w definicji klasy.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a>\<c>

Nadal w temacie formatowania, używasz znacznika `<c>` do oznaczania części tekstu jako kodu.
Przypomina znacznik `<code>`, ale wbudowany. Jest to przydatne, gdy chcesz pokazać przykładowy kod jako część zawartości znacznika.
Zaktualizujmy dokumentację klasy `Math`.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a>\<wyjątek >

Przy użyciu znacznika `<exception>` pozwalasz deweloperom znać, że metoda może zgłosić określone wyjątki.
Przeglądając bibliotekę `Math`, można zobaczyć, że obie metody `Add` zgłaszają wyjątek, jeśli spełniony jest określony warunek. Chociaż nie jest to oczywiste, jest to, że metoda `Divide` Integer zwraca również, jeśli parametr `b` ma wartość zero. Teraz Dodaj dokumentację wyjątku do tej metody.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

Atrybut `cref` reprezentuje odwołanie do wyjątku, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie. Kompilator wyświetli ostrzeżenie, jeśli nie można rozpoznać jego wartości.

## <a name="see"></a>\<see>

Tag `<see>` umożliwia utworzenie linku kliknięcia do strony dokumentacji dla innego elementu kodu. W następnym przykładzie utworzysz link do kliknięcia między dwoma `Add` metodami.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` jest **wymaganym** atrybutem, który reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.

## <a name="seealso"></a>\<seealso>

Używasz znacznika `<seealso>` w taki sam sposób jak tag `<see>`. Jedyną różnicą jest to, że jej zawartość jest zwykle umieszczana w sekcji "Zobacz też". Tutaj dodamy znacznik `seealso` w metodzie `Add` Integer, aby odwołać się do innych metod w klasie, która akceptuje parametry całkowite:

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

Atrybut `cref` reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.
Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.

## <a name="param"></a>\<param>

Za pomocą tagu `<param>` można opisać parametry metody. Oto przykład dotyczący metody Double `Add`: parametr opisany w opisie jest określony w **wymaganym** atrybucie `name`.

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a>\<typeparam >

Używasz tagu `<typeparam>`, podobnie jak tag `<param>`, ale dla deklaracji typu ogólnego lub metody, aby opisać parametr generyczny.
Dodaj szybką metodę rodzajową do klasy `Math`, aby sprawdzić, czy jedna ilość jest większa niż inna.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a>\<paramref>

Czasami może być w środku opisującym opisywanie metody w tym, co może być tagiem `<summary>` i można utworzyć odwołanie do parametru. Tag `<paramref>` jest świetny dla samego siebie. Zaktualizujmy podsumowanie naszej metody `Add` opartej na podwójnej precyzji. Podobnie jak w przypadku znacznika `<param>` Nazwa parametru jest określona w **wymaganym** atrybucie `name`.

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a>\<typeparamref>

Używasz tagu `<typeparamref>`, podobnie jak tag `<paramref>`, ale dla deklaracji typu ogólnego lub metody, aby opisać parametr generyczny.
Możesz użyć tej samej metody generycznej, która została wcześniej utworzona.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a>\<list>

Tag `<list>` służy do formatowania informacji dokumentacji jako listy uporządkowanej, nieuporządkowanej listy lub tabeli.
Utwórz nieuporządkowaną listę każdej operacji matematycznej obsługiwanej przez bibliotekę `Math`.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Można utworzyć uporządkowaną listę lub tabelę, zmieniając atrybut `type` na odpowiednio `number` lub `table`.

### <a name="put-it-all-together"></a>Zebranie wszystkich elementów

Jeśli wykonano ten samouczek i zastosowano znaczniki do kodu w razie potrzeby, kod powinien teraz wyglądać podobnie do poniższego:

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

Z poziomu kodu można wygenerować szczegółową witrynę sieci Web, która została ukończona z kliknięciami odwołania krzyżowego. Ale nastąpiło inne zagadnienie: Twój kod stał się trudno odczytać.
Istnieje dużo informacji do przesiania przez to, że jest to okropnej dla każdego dewelopera, który chce współtworzyć ten kod.
Thankfully istnieje tag XML, który może pomóc Ci w poradzić sobie z:

## <a name="include"></a>\<Uwzględnij >

Tag `<include>` umożliwia odwoływanie się do komentarzy w osobnym pliku XML, który opisuje typy i elementy członkowskie w kodzie źródłowym, zamiast umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.

Teraz można przenieść wszystkie tagi XML do oddzielnego pliku XML o nazwie `docs.xml`. Możesz nawiązać dowolną nazwę pliku.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

W powyższym kodzie XML komentarze dokumentacji każdego członka są wyświetlane bezpośrednio wewnątrz tagu o nazwie po tym, co robią. Możesz wybrać własną strategię.
Teraz, gdy masz Komentarze XML w osobnym pliku, zobaczmy, jak kod może być bardziej czytelny przy użyciu tagu `<include>`:

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Jest to możliwe: kod jest z powrotem odczytywany, a informacje o dokumentacji nie zostały utracone.

Atrybut `file` reprezentuje nazwę pliku XML zawierającego dokumentację.

Atrybut `path` reprezentuje zapytanie [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) do `tag name` obecne w określonym `file`.

Atrybut `name` reprezentuje specyfikator Name w tagu, który poprzedza Komentarze.

Atrybut `id`, który może być użyty zamiast `name` reprezentuje identyfikator tagu, który poprzedza Komentarze.

### <a name="user-defined-tags"></a>Tagi zdefiniowane przez użytkownika

Wszystkie Tagi podane powyżej reprezentują te, które są rozpoznawane przez C# kompilator. Jednak użytkownik może definiować własne znaczniki.
Narzędzia takie jak Sandcastle zapewniają obsługę dodatkowych tagów, takich jak [\<> zdarzeń](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) i [\<zanotować >](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), a nawet obsługują [dokumentowanie przestrzeni nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Niestandardowe i wewnętrzne narzędzia do generowania dokumentacji mogą również być używane ze znacznikami standardowymi i można obsługiwać wiele formatów wyjściowych z formatu HTML do pliku PDF.

## <a name="recommendations"></a>Zalecenia

Dokumentowanie kodu jest zalecane z wielu powodów. Poniżej przedstawiono niektóre najlepsze rozwiązania, ogólne scenariusze przypadków użycia i informacje, które należy znać w przypadku używania tagów dokumentacji XML w C# kodzie.

- Ze względu na spójność wszystkich publicznie widocznych typów i ich członków należy udokumentować. Jeśli to konieczne, zrób wszystko.
- Prywatne elementy członkowskie mogą być również udokumentowane przy użyciu komentarzy XML. Jednak spowoduje to uwidocznienie wewnętrznej (potencjalnie poufnej) pracy biblioteki.
- W przypadku braku systemu operacyjnego typy i ich elementy członkowskie powinny mieć tag `<summary>`, ponieważ jego zawartość jest wymagana przez funkcję IntelliSense.
- Tekst dokumentacji należy napisać przy użyciu kompletnych zdań kończących się pełnym zatrzymywaniem.
- Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji są łączone w jeden wpis dla tego typu.
- Kompilator weryfikuje składnię tagów `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`i `<typeparam>`.
- Kompilator sprawdza poprawność parametrów zawierających ścieżki plików i odwołania do innych części kodu.

## <a name="see-also"></a>Zobacz także

- [Komentarze dokumentacji XML (C# Przewodnik programowania)](programming-guide/xmldoc/index.md)
- [Zalecane Tagi dla komentarzy do dokumentacjiC# (Przewodnik programowania)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
