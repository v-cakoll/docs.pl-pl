---
title: Declare — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 021805508a8a053ccc8fab6f1013109bece4b6f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404774"
---
# <a name="declare-statement"></a>Declare — Instrukcja

Deklaruje odwołanie do procedury zaimplementowanej w zewnętrznym pliku.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).|
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Społeczeństwo](../modifiers/public.md)<br />-   [Chronione](../modifiers/protected.md)<br />-   [Osoby](../modifiers/friend.md)<br />-   [Użytek](../modifiers/private.md)<br />- [Chroniony znajomy](../modifiers/protected-friend.md)<br />- [Prywatne chronione](../modifiers/private-protected.md)<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).|
|`charsetmodifier`|Opcjonalny. Określa zestaw znaków i informacje o przeszukiwaniu plików. Może być jedną z następujących czynności:<br /><br /> -   [ANSI](../modifiers/ansi.md) (domyślnie)<br />-   [Unicode](../modifiers/unicode.md)<br />-   [Automatycznie](../modifiers/auto.md)|
|`Sub`|Opcjonalne, ale `Sub` lub `Function` muszą pojawić się. Wskazuje, że procedura zewnętrzna nie zwraca wartości.|
|`Function`|Opcjonalne, ale `Sub` lub `Function` muszą pojawić się. Wskazuje, że procedura zewnętrzna zwraca wartość.|
|`name`|Wymagany. Nazwa tego odwołania zewnętrznego. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Wymagany. Wprowadza `Lib` klauzulę identyfikującą zewnętrzny plik (DLL lub zasób kodu) zawierający zewnętrzną procedurę.|
|`libname`|Wymagany. Nazwa pliku, który zawiera zadeklarowaną procedurę.|
|`Alias`|Opcjonalny. Wskazuje, że zadeklarowana procedura nie może być identyfikowana w pliku o nazwie określonej w `name` . Należy określić swój identyfikator w `aliasname` .|
|`aliasname`|Wymagane w przypadku użycia `Alias` słowa kluczowego. Ciąg, który identyfikuje procedurę na jeden z dwóch sposobów:<br /><br /> Nazwa punktu wejścia procedury w pliku w cudzysłowie ( `""` )<br /><br /> -lub-<br /><br /> Znak numeru ( `#` ), po którym następuje liczba całkowita określająca numer porządkowy punktu wejścia procedury w jego pliku|
|`parameterlist`|Wymagane, jeśli procedura pobiera parametry. Zobacz [listę parametrów](parameter-list.md).|
|`returntype`|Wymagane `Function` , jeśli jest określony i `Option Strict` ma `On` . Typ danych wartości zwracanej przez procedurę.|

## <a name="remarks"></a>Uwagi

Czasami konieczne jest wywołanie procedury zdefiniowanej w pliku (na przykład DLL lub zasobu kodu) poza projektem. Gdy to zrobisz, kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury, takich jak miejsce, w którym znajduje się procedura, sposób jej identyfikacji, wywołanie sekwencji wywołań i zwracany typ oraz użyty znak ciągu. `Declare`Instrukcja tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.

Można używać `Declare` tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* dla odwołania zewnętrznego musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Odwołania zewnętrzne są domyślne dla dostępu [publicznego](../modifiers/public.md) . Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu.

## <a name="rules"></a>Reguły

- **Attributes.** Atrybuty można zastosować do odwołania zewnętrznego. Każdy stosowany atrybut ma wpływ tylko na projekt, a nie w pliku zewnętrznym.

- **Modyfikatory.** Procedury zewnętrzne są niejawnie [udostępniane](../modifiers/shared.md). Nie można użyć `Shared` słowa kluczowego podczas deklarowania odwołania zewnętrznego i nie można zmienić jego stanu udostępnionego.

  Procedura zewnętrzna nie może uczestniczyć w zastępowaniu, implementować składowych interfejsu ani obsługiwać zdarzeń. Z tego powodu nie można użyć `Overrides` `Overridable` słowa kluczowego,,,, `NotOverridable` `MustOverride` `Implements` lub `Handles` w `Declare` instrukcji.

- **Nazwa procedury zewnętrznej.** Nie musisz podawać tego odwołania zewnętrznego o tej samej nazwie (w `name` ) jak nazwa punktu wejścia procedury w pliku zewnętrznym ( `aliasname` ). Możesz użyć klauzuli, `Alias` Aby określić nazwę punktu wejścia. Może to być przydatne, jeśli procedura zewnętrzna ma taką samą nazwę jak zastrzeżony modyfikator Visual Basic lub zmiennej, procedury lub dowolnego innego elementu programistycznego w tym samym zakresie.

  > [!NOTE]
  > Nazwy punktów wejścia w większości bibliotek DLL są rozróżniane wielkości liter.

- **Numer procedury zewnętrznej.** Alternatywnie można użyć `Alias` klauzuli, aby określić numer porządkowy punktu wejścia w tabeli eksportu pliku zewnętrznego. W tym celu należy zacząć od `aliasname` znaku cyfry ( `#` ). Może to być przydatne, jeśli dowolny znak w nazwie procedury zewnętrznej nie jest dozwolony w Visual Basic lub jeśli plik zewnętrzny eksportuje procedurę bez nazwy.

## <a name="data-type-rules"></a>Reguły typu danych

- **Typ danych parametru.** Jeśli `Option Strict` jest `On` , należy określić typ danych każdego parametru w `parameterlist` . Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. W programie należy `parameterlist` użyć `As` klauzuli, aby określić typ danych argumentu, który ma zostać przesłany do każdego parametru.

  > [!NOTE]
  > Jeśli procedura zewnętrzna nie została zapisywana dla .NET Framework, należy zwrócić uwagę na to, że typy danych odpowiadają. Na przykład, Jeśli zadeklarujesz odwołanie zewnętrzne do procedury Visual Basic 6,0 z `Integer` parametrem (16 bitów w Visual Basic 6,0), należy zidentyfikować odpowiadający argument `Short` w `Declare` instrukcji, ponieważ to jest 16-bitowa liczba całkowita w Visual Basic. Podobnie `Long` ma inną szerokość danych w Visual Basic 6,0 i `Date` jest zaimplementowana inaczej.

- **Zwraca typ danych.** Jeśli zewnętrzna procedura to `Function` a i `Option Strict` jest `On` , należy określić typ danych wartości zwracanej do kodu wywołującego. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.

  > [!NOTE]
  > Kompilator Visual Basic nie sprawdza, czy typy danych są zgodne z procedurami zewnętrznymi. Jeśli wystąpi niezgodność, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Runtime.InteropServices.MarshalDirectiveException> wyjątek w czasie wykonywania.

- **Domyślne typy danych.** Jeśli `Option Strict` jest `Off` i nie określisz typu danych parametru w `parameterlist` , kompilator Visual Basic konwertuje odpowiedni argument na [Typ danych obiektu](../data-types/object-data-type.md). Analogicznie, jeśli nie zostanie określony `returntype` , kompilator Pobiera zwracany typ danych `Object` .

  > [!NOTE]
  > Ponieważ pracujesz z procedurą zewnętrzną, która mogła zostać zapisywana na innej platformie, nie jest to niebezpieczne dla wprowadzania wszelkich założeń dotyczących typów danych lub zezwalania na ich domyślne. Określenie typu danych każdego parametru i wartości zwracanej jest znacznie bezpieczniejsze. Poprawia to również czytelność kodu.

## <a name="behavior"></a>Zachowanie

- **Scope.** Odwołanie zewnętrzne znajduje się w zakresie w całej jego klasy, strukturze lub module.

- **Okres istnienia.** Odwołanie zewnętrzne ma ten sam okres istnienia co Klasa, struktura lub moduł, w którym jest zadeklarowany.

- **Wywoływanie procedury zewnętrznej.** Procedurę zewnętrzną można wywołać w taki sam sposób, jak `Function` wywołanie `Sub` procedury lub, przy użyciu jej w wyrażeniu, jeśli zwraca wartość lub przez określenie jej w [instrukcji Call](call-statement.md) , jeśli nie zwróci wartości.

  Argumenty do procedury zewnętrznej są przekazywane dokładnie tak, jak określono `parameterlist` w `Declare` instrukcji. Nie należy uwzględniać sposobu, w jaki parametry zostały pierwotnie zadeklarowane w pliku zewnętrznym. Podobnie, jeśli istnieje wartość zwracana, należy użyć jej dokładnie tak, jak określono `returntype` w `Declare` instrukcji.

- **Zestawy znaków.** Można określić, w `charsetmodifier` jaki sposób Visual Basic powinien zorganizować ciągi podczas wywoływania procedury zewnętrznej. `Ansi`Modyfikator kieruje Visual Basic do kierowania wszystkich ciągów do wartości ANSI, a `Unicode` modyfikator kieruje go do skierowania wszystkich ciągów do wartości Unicode. `Auto`Modyfikator kieruje Visual Basic do organizowania ciągów zgodnie z regułami .NET Framework na podstawie odwołania zewnętrznego lub w `name` `aliasname` przypadku określenia. Wartość domyślna to `Ansi`.

  `charsetmodifier`określa również sposób, w jaki Visual Basic powinien wyszukiwać procedurę zewnętrzną w pliku zewnętrznym. `Ansi`i `Unicode` obie Visual Basic bezpośrednie, aby je wyszukać bez modyfikowania jego nazwy podczas wyszukiwania. `Auto`kieruje Visual Basic, aby określić podstawowy zestaw znaków platformy wykonawczej i prawdopodobnie zmodyfikować nazwę procedury zewnętrznej w następujący sposób:

  - Na platformie ANSI, takiej jak Windows 95, Windows 98 lub Windows Millennium Edition, należy najpierw wyszukać zewnętrzną procedurę bez modyfikacji nazwy. Jeśli to się nie powiedzie, Dołącz wartość "A" na końcu nazwy procedury zewnętrznej i sprawdź ją ponownie.

  - Na platformie Unicode, takiej jak Windows NT, Windows 2000 lub Windows XP, należy najpierw wyszukać zewnętrzną procedurę bez modyfikacji nazwy. Jeśli to się nie powiedzie, Dołącz literę "W" do końca nazwy procedury zewnętrznej i sprawdź ją ponownie.

- **Ustanawia.** Visual Basic używa mechanizmu *wywołania platformy* .NET Framework (PInvoke) do rozwiązywania i uzyskiwania dostępu do zewnętrznych procedur. `Declare`Instrukcja i <xref:System.Runtime.InteropServices.DllImportAttribute> Klasa używają tego mechanizmu automatycznie, a użytkownik nie potrzebuje żadnej wiedzy o funkcji PInvoke. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie interfejsów API systemu Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Jeśli procedura zewnętrzna działa poza środowiskiem uruchomieniowym języka wspólnego (CLR), jest to *kod niezarządzany*. W przypadku wywołania takiej procedury, na przykład funkcji interfejsu API systemu Windows lub metody COM, można uwidocznić swoją aplikację pod kątem zagrożeń bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [zasady bezpiecznego kodowania dla niezarządzanego kodu](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Przykład

Poniższy przykład deklaruje odwołanie zewnętrzne do `Function` procedury, która zwraca bieżącą nazwę użytkownika. Następnie wywołuje procedurę zewnętrzną `GetUserNameA` w ramach `getUser` procedury.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Przykład

<xref:System.Runtime.InteropServices.DllImportAttribute>Zapewnia alternatywny sposób używania funkcji w kodzie niezarządzanym. Poniższy przykład deklaruje zaimportowaną funkcję bez użycia `Declare` instrukcji.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports — Instrukcja (.NET Namespace i Type)](imports-statement-net-namespace-and-type.md)
- [AddressOf, operator](../operators/addressof-operator.md)
- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Lista parametrów](parameter-list.md)
- [Call, instrukcja](call-statement.md)
- [Przewodnik: Wywoływanie interfejsów API systemu Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)
