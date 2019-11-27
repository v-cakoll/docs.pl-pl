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
ms.openlocfilehash: 48a36e3ecdef40810ea7a3194e85b5b646154331
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354091"
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
|`attributelist`|Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> -   [publiczny](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [znajomy](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [prywatny](../../../visual-basic/language-reference/modifiers/private.md)<br />- [chronionego przyjaciela](../../language-reference/modifiers/protected-friend.md)<br />- [prywatnej ochrony](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Opcjonalna. Określa zestaw znaków i informacje o przeszukiwaniu plików. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (wartość domyślna)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Opcjonalne, ale muszą być wyświetlane `Sub` lub `Function`. Wskazuje, że procedura zewnętrzna nie zwraca wartości.|
|`Function`|Opcjonalne, ale muszą być wyświetlane `Sub` lub `Function`. Wskazuje, że procedura zewnętrzna zwraca wartość.|
|`name`|Wymagana. Nazwa tego odwołania zewnętrznego. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Wymagana. Wprowadza klauzulę `Lib`, która identyfikuje zewnętrzny plik (DLL lub zasób kodu) zawierający zewnętrzną procedurę.|
|`libname`|Wymagana. Nazwa pliku, który zawiera zadeklarowaną procedurę.|
|`Alias`|Opcjonalna. Wskazuje, że zadeklarowana procedura nie może być identyfikowana w pliku o nazwie określonej w `name`. Tożsamość należy określić w `aliasname`.|
|`aliasname`|Wymagane w przypadku użycia słowa kluczowego `Alias`. Ciąg, który identyfikuje procedurę na jeden z dwóch sposobów:<br /><br /> Nazwa punktu wejścia procedury w obrębie pliku w cudzysłowie (`""`)<br /><br /> —lub—<br /><br /> Znak numeru (`#`) następuje liczba całkowita określająca numer porządkowy punktu wejścia procedury w jego pliku|
|`parameterlist`|Wymagane, jeśli procedura pobiera parametry. Zobacz [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Wymagane, jeśli określono `Function` i `Option Strict` jest `On`. Typ danych wartości zwracanej przez procedurę.|

## <a name="remarks"></a>Uwagi

Czasami konieczne jest wywołanie procedury zdefiniowanej w pliku (na przykład DLL lub zasobu kodu) poza projektem. Gdy to zrobisz, kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury, takich jak miejsce, w którym znajduje się procedura, sposób jej identyfikacji, wywołanie sekwencji wywołań i zwracany typ oraz użyty znak ciągu. Instrukcja `Declare` tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.

`Declare` można używać tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* dla odwołania zewnętrznego musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Odwołania zewnętrzne są domyślne dla dostępu [publicznego](../../../visual-basic/language-reference/modifiers/public.md) . Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.

## <a name="rules"></a>Reguły

- **Attributes.** Atrybuty można zastosować do odwołania zewnętrznego. Każdy stosowany atrybut ma wpływ tylko na projekt, a nie w pliku zewnętrznym.

- **Modyfikatory.** Procedury zewnętrzne są niejawnie [udostępniane](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć słowa kluczowego `Shared` podczas deklarowania odwołania zewnętrznego i nie można zmienić jego stanu udostępnionego.

  Procedura zewnętrzna nie może uczestniczyć w zastępowaniu, implementować składowych interfejsu ani obsługiwać zdarzeń. Z tego powodu nie można użyć słowa kluczowego `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`lub `Handles` w instrukcji `Declare`.

- **Nazwa procedury zewnętrznej.** Nie musisz podawać tego odwołania zewnętrznego o tej samej nazwie (w `name`) jako nazwy punktu wejścia procedury w pliku zewnętrznym (`aliasname`). Aby określić nazwę punktu wejścia, można użyć klauzuli `Alias`. Może to być przydatne, jeśli procedura zewnętrzna ma taką samą nazwę jak zastrzeżony modyfikator Visual Basic lub zmiennej, procedury lub dowolnego innego elementu programistycznego w tym samym zakresie.

  > [!NOTE]
  > Nazwy punktów wejścia w większości bibliotek DLL są rozróżniane wielkości liter.

- **Numer procedury zewnętrznej.** Alternatywnie można użyć klauzuli `Alias`, aby określić numer porządkowy punktu wejścia w tabeli eksportu pliku zewnętrznego. Aby to zrobić, zacznij `aliasname` od znaku numeru (`#`). Może to być przydatne, jeśli dowolny znak w nazwie procedury zewnętrznej nie jest dozwolony w Visual Basic lub jeśli plik zewnętrzny eksportuje procedurę bez nazwy.

## <a name="data-type-rules"></a>Reguły typu danych

- **Typ danych parametru.** Jeśli `Option Strict` jest `On`, należy określić typ danych każdego parametru w `parameterlist`. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. W `parameterlist`Użyj klauzuli `As`, aby określić typ danych argumentu, który ma zostać przesłany do każdego parametru.

  > [!NOTE]
  > Jeśli procedura zewnętrzna nie została zapisywana dla .NET Framework, należy zwrócić uwagę na to, że typy danych odpowiadają. Na przykład, Jeśli zadeklarujesz odwołanie zewnętrzne do procedury Visual Basic 6,0 z parametrem `Integer` (16 bitów w Visual Basic 6,0), należy zidentyfikować odpowiedni argument jako `Short` w instrukcji `Declare`, ponieważ to jest 16-bitowa liczba całkowita w Visual Basic. Podobnie `Long` ma inną szerokość danych w Visual Basic 6,0, a `Date` jest zaimplementowana inaczej.

- **Zwraca typ danych.** Jeśli zewnętrzna procedura jest `Function` i `Option Strict` jest `On`, należy określić typ danych wartości zwracanej do kodu wywołującego. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.

  > [!NOTE]
  > Kompilator Visual Basic nie sprawdza, czy typy danych są zgodne z procedurami zewnętrznymi. Jeśli wystąpi niezgodność, środowisko uruchomieniowe języka wspólnego generuje wyjątek <xref:System.Runtime.InteropServices.MarshalDirectiveException> w czasie wykonywania.

- **Domyślne typy danych.** Jeśli `Option Strict` jest `Off` i nie określisz typu danych parametru w `parameterlist`, kompilator Visual Basic konwertuje odpowiedni argument na [Typ danych obiektu](../../../visual-basic/language-reference/data-types/object-data-type.md). Analogicznie, jeśli nie określisz `returntype`, kompilator Pobiera typ danych zwrotnych do `Object`.

  > [!NOTE]
  > Ponieważ pracujesz z procedurą zewnętrzną, która mogła zostać zapisywana na innej platformie, nie jest to niebezpieczne dla wprowadzania wszelkich założeń dotyczących typów danych lub zezwalania na ich domyślne. Określenie typu danych każdego parametru i wartości zwracanej jest znacznie bezpieczniejsze. Poprawia to również czytelność kodu.

## <a name="behavior"></a>Zachowanie

- **Scope.** Odwołanie zewnętrzne znajduje się w zakresie w całej jego klasy, strukturze lub module.

- **Okres istnienia.** Odwołanie zewnętrzne ma ten sam okres istnienia co Klasa, struktura lub moduł, w którym jest zadeklarowany.

- **Wywoływanie procedury zewnętrznej.** Procedurę zewnętrzną można wywołać w taki sam sposób, jak wywołanie procedury `Function` lub `Sub` — przy użyciu jej w wyrażeniu, jeśli zwraca wartość lub przez określenie jej w [instrukcji Call](../../../visual-basic/language-reference/statements/call-statement.md) , jeśli nie zwróci wartości.

  Argumenty do procedury zewnętrznej należy przekazać dokładnie tak, jak określono przez `parameterlist` w instrukcji `Declare`. Nie należy uwzględniać sposobu, w jaki parametry zostały pierwotnie zadeklarowane w pliku zewnętrznym. Podobnie, jeśli istnieje wartość zwracana, należy użyć jej dokładnie tak, jak określono przez `returntype` w instrukcji `Declare`.

- **Zestawy znaków.** Można określić w `charsetmodifier` sposób, w jaki Visual Basic powinny organizować ciągi podczas wywoływania procedury zewnętrznej. Modyfikator `Ansi` kieruje Visual Basic do kierowania wszystkich ciągów do wartości ANSI, a modyfikator `Unicode` kieruje go do kierowania wszystkich ciągów do wartości Unicode. Modyfikator `Auto` kieruje Visual Basic do kierowania ciągów zgodnie z regułami .NET Framework opartymi na odwołaniach zewnętrznych `name`lub `aliasname`, jeśli zostały określone. Wartość domyślna to `Ansi`.

  `charsetmodifier` określa również, jak Visual Basic powinien wyszukiwać procedurę zewnętrzną w pliku zewnętrznym. `Ansi` i `Unicode` zarówno bezpośrednie Visual Basic do wyszukania, bez modyfikowania jego nazwy podczas wyszukiwania. `Auto` kieruje Visual Basic, aby określić podstawowy zestaw znaków platformy wykonawczej i prawdopodobnie zmodyfikować nazwę procedury zewnętrznej w następujący sposób:

  - Na platformie ANSI, takiej jak Windows 95, Windows 98 lub Windows Millennium Edition, należy najpierw wyszukać zewnętrzną procedurę bez modyfikacji nazwy. Jeśli to się nie powiedzie, Dołącz wartość "A" na końcu nazwy procedury zewnętrznej i sprawdź ją ponownie.

  - Na platformie Unicode, takiej jak Windows NT, Windows 2000 lub Windows XP, należy najpierw wyszukać zewnętrzną procedurę bez modyfikacji nazwy. Jeśli to się nie powiedzie, Dołącz literę "W" do końca nazwy procedury zewnętrznej i sprawdź ją ponownie.

- **Ustanawia.** Visual Basic używa mechanizmu *wywołania platformy* .NET Framework (PInvoke) do rozwiązywania i uzyskiwania dostępu do zewnętrznych procedur. Instrukcja `Declare` i Klasa <xref:System.Runtime.InteropServices.DllImportAttribute> używają tego mechanizmu automatycznie, a użytkownik nie potrzebuje żadnej znajomości funkcji PInvoke. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Jeśli procedura zewnętrzna działa poza środowiskiem uruchomieniowym języka wspólnego (CLR), jest to *kod niezarządzany*. W przypadku wywołania takiej procedury, na przykład funkcji interfejsu API systemu Windows lub metody COM, można uwidocznić swoją aplikację pod kątem zagrożeń bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [zasady bezpiecznego kodowania dla niezarządzanego kodu](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Przykład

Poniższy przykład deklaruje odwołanie zewnętrzne do procedury `Function`, która zwraca bieżącą nazwę użytkownika. Następnie wywołuje procedurę zewnętrzną `GetUserNameA` w ramach procedury `getUser`.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Przykład

<xref:System.Runtime.InteropServices.DllImportAttribute> zapewnia alternatywny sposób używania funkcji w kodzie niezarządzanym. Poniższy przykład deklaruje zaimportowaną funkcję bez użycia instrukcji `Declare`.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call, instrukcja](../../../visual-basic/language-reference/statements/call-statement.md)
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
