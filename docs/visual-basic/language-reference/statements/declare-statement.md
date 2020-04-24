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
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646385"
---
# <a name="declare-statement"></a>Declare — Instrukcja

Deklaruje odwołanie do procedury zaimplementowanej w pliku zewnętrznym.

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
|`attributelist`|Element opcjonalny. Zobacz [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Element opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Publicznego](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Przyjaciel](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatny](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Chroniony przyjaciel](../../language-reference/modifiers/protected-friend.md)<br />- [Prywatna ochrona](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Element opcjonalny. Zobacz [Cienie](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Element opcjonalny. Określa informacje o zestawie znaków i wyszukiwaniu plików. Może być jedną z następujących czynności:<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (domyślnie)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Opcjonalnie, ale `Sub` `Function` albo musi się pojawić. Wskazuje, że procedura zewnętrzna nie zwraca wartości.|
|`Function`|Opcjonalnie, ale `Sub` `Function` albo musi się pojawić. Wskazuje, że procedura zewnętrzna zwraca wartość.|
|`name`|Wymagany. Nazwa tego odwołania zewnętrznego. Aby uzyskać więcej informacji, zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Wymagany. Wprowadza klauzulę, `Lib` która identyfikuje plik zewnętrzny (DLL lub zasób kodu), który zawiera procedurę zewnętrzną.|
|`libname`|Wymagany. Nazwa pliku zawierającego procedurę zadeklarowanej.|
|`Alias`|Element opcjonalny. Wskazuje, że deklarowana procedura nie może być zidentyfikowana `name`w jego pliku przez nazwę określoną w programie . Jego identyfikację `aliasname`należy określić w pliku .|
|`aliasname`|Wymagane, jeśli używasz słowa kluczowego. `Alias` Ciąg identyfikujące procedurę na jeden z dwóch sposobów:<br /><br /> Nazwa punktu wejścia procedury w jego pliku,`""`w cudzysłowie ( )<br /><br /> — lub —<br /><br /> Znak liczbowy`#`( ), po którym następuje liczba całkowita określająca numer porządkowy punktu wejścia procedury w jego pliku|
|`parameterlist`|Wymagane, jeśli procedura przyjmuje parametry. Zobacz [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Wymagane, `Function` jeśli jest `Option Strict` `On`określony i jest . Typ danych wartości zwracanej przez procedurę.|

## <a name="remarks"></a>Uwagi

Czasami należy wywołać procedurę zdefiniowaną w pliku (na przykład biblioteki DLL lub zasobu kodu) poza projektem. Po wykonaniu tej funkcji kompilator języka Visual Basic nie ma dostępu do informacji, których potrzebuje do prawidłowego wywołania procedury, takich jak miejsce, w którym znajduje się procedura, sposób jej identyfikacji, jego sekwencja wywołania i typ zwracany oraz używany zestaw znaków ciągu. Instrukcja `Declare` tworzy odniesienie do procedury zewnętrznej i dostarcza tych niezbędnych informacji.

Można używać `Declare` tylko na poziomie modułu. Oznacza *to,* że kontekst deklaracji dla odwołania zewnętrznego musi być klasą, strukturą lub modułem i nie może być plikiem źródłowym, obszarem nazw, interfejsem, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [Konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Odwołania zewnętrzne domyślnie [public](../../../visual-basic/language-reference/modifiers/public.md) dostęp. Można dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu.

## <a name="rules"></a>Reguły

- **Atrybuty.** Atrybuty można zastosować do odwołania zewnętrznego. Każdy atrybut, który stosujesz ma wpływ tylko w projekcie, a nie w pliku zewnętrznym.

- **Modyfikatorów.** Procedury zewnętrzne są niejawnie [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md). Nie można `Shared` użyć słowa kluczowego podczas deklarowania odwołania zewnętrznego i nie można zmienić jego stanu udostępnionego.

  Procedura zewnętrzna nie może uczestniczyć w zastępowanie, implementowanie elementów członkowskich interfejsu lub obsługi zdarzeń. W związku z tym `Overrides` `Overridable`nie `NotOverridable` `MustOverride`można `Implements`użyć `Handles` słowa `Declare` kluczowego w instrukcji , , , lub .

- **Nazwa procedury zewnętrznej.** Nie trzeba nadawać temu zewnętrznemu odwołaniu `name`tej nazwy (w) co nazwa punktu`aliasname`wejścia procedury w jej pliku zewnętrznym ( ). Można użyć `Alias` klauzuli, aby określić nazwę punktu wejścia. Może to być przydatne, jeśli procedura zewnętrzna ma taką samą nazwę jak modyfikator zastrzeżony języka Visual Basic lub zmienna, procedura lub inny element programowania w tym samym zakresie.

  > [!NOTE]
  > W większości dll jest rozróżniana wielkość liter.

- **Numer procedury zewnętrznej.** Alternatywnie można użyć `Alias` klauzuli, aby określić numer porządkowy punktu wejścia w tabeli eksportu pliku zewnętrznego. Aby to zrobić, `aliasname` należy rozpocząć`#`od znaku numerycznego ( ). Może to być przydatne, jeśli dowolny znak w nazwie procedury zewnętrznej nie jest dozwolony w języku Visual Basic lub jeśli plik zewnętrzny eksportuje procedurę bez nazwy.

## <a name="data-type-rules"></a>Reguły typu danych

- **Typy danych parametrów.** Jeśli `Option Strict` `On`tak, należy określić typ danych `parameterlist`każdego parametru w pliku . Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. W `parameterlist`programie , `As` można użyć klauzuli, aby określić typ danych argumentu, który ma być przekazywany do każdego parametru.

  > [!NOTE]
  > Jeśli procedura zewnętrzna nie została napisana dla programu .NET Framework, należy zadbać o to, aby typy danych odpowiadały. Na przykład jeśli deklarujesz odwołanie zewnętrzne do procedury Visual Basic `Integer` 6.0 z parametrem (16 bitów w języku `Short` Visual `Declare` Basic 6.0), należy zidentyfikować odpowiedni argument, jak w instrukcji, ponieważ jest to 16-bitowy typ liczby całkowitej w języku Visual Basic. Podobnie `Long` ma inną szerokość danych w języku Visual Basic `Date` 6.0 i jest implementowana inaczej.

- **Zwraca typ danych.** Jeśli procedura zewnętrzna `Function` `Option Strict` jest `On`i jest , należy określić typ danych wartości zwróconej do kodu wywołującego. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.

  > [!NOTE]
  > Kompilator języka Visual Basic nie sprawdza, czy typy danych są zgodne z typami procedur zewnętrznych. Jeśli istnieje niezgodność, środowisko wykonawcze języka wspólnego <xref:System.Runtime.InteropServices.MarshalDirectiveException> generuje wyjątek w czasie wykonywania.

- **Domyślne typy danych.** Jeśli `Option Strict` `Off` jest i nie określono typu danych `parameterlist`parametru w programie, kompilator języka Visual Basic konwertuje odpowiedni argument na [typ danych obiektu](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobnie, jeśli nie określisz `returntype`, kompilator przyjmuje typ `Object`zwracania danych.

  > [!NOTE]
  > Ponieważ masz do czynienia z procedurą zewnętrzną, która mogła zostać napisana na innej platformie, niebezpieczne jest wprowadzanie wszelkich założeń dotyczących typów danych lub zezwalanie im na domyślne. Jest znacznie bezpieczniejsze, aby określić typ danych każdego parametru i wartości zwracanej, jeśli istnieje. Zwiększa to również czytelność kodu.

## <a name="behavior"></a>Zachowanie

- **Zakres.** Odwołanie zewnętrzne znajduje się w zakresie całej jego klasy, struktury lub modułu.

- **Okres istnienia.** Odwołanie zewnętrzne ma taki sam okres istnienia jak klasa, struktura lub moduł, w którym jest zadeklarowany.

- **Wywołanie procedury zewnętrznej.** Wywołanie procedury zewnętrznej w taki `Function` `Sub` sam sposób, w jaki wywoływane lub procedury — używając go w wyrażeniu, jeśli zwraca wartość lub określając go w [instrukcji połączenia,](../../../visual-basic/language-reference/statements/call-statement.md) jeśli nie zwraca wartość.

  Argumenty do procedury zewnętrznej są dokładnie `parameterlist` takie, jak określono w `Declare` instrukcji. Nie należy brać pod uwagę, jak parametry zostały pierwotnie zadeklarowane w pliku zewnętrznym. Podobnie, jeśli istnieje wartość zwracana, należy użyć `returntype` go `Declare` dokładnie tak, jak określono w instrukcji.

- **Zestawy znaków.** Można określić, w `charsetmodifier` jaki sposób Visual Basic powinien marshal ciągi podczas wywoływania procedury zewnętrznej. Modyfikator `Ansi` kieruje visual basic do organizowania wszystkich ciągów `Unicode` do wartości ANSI, a modyfikator kieruje go do organizowania wszystkich ciągów do wartości Unicode. Modyfikator `Auto` kieruje visual basic do ciągów marshal zgodnie z regułami programu .NET Framework na podstawie odwołania `name`zewnętrznego lub `aliasname` jeśli określono. Wartością domyślną jest `Ansi`.

  `charsetmodifier`określa również, w jaki sposób program Visual Basic powinien wyszukać procedurę zewnętrzną w swoim pliku zewnętrznym. `Ansi`i `Unicode` zarówno bezpośrednie Visual Basic, aby wyszukać go bez modyfikowania jego nazwy podczas wyszukiwania. `Auto`nakazuje visual basic, aby określić podstawowy zestaw znaków platformy wykonywki i ewentualnie zmodyfikować nazwę procedury zewnętrznej, w następujący sposób:

  - Na platformie ANSI, takiej jak Windows 95, Windows 98 lub Windows Millennium Edition, najpierw wyszukuj procedurę zewnętrzną bez modyfikacji nazwy. Jeśli to się nie powiedzie, dołącz "A" na końcu nazwy procedury zewnętrznej i wyszukuj ją ponownie.

  - Na platformie Unicode, takiej jak Windows NT, Windows 2000 lub Windows XP, najpierw wyszukuj procedurę zewnętrzną bez modyfikacji nazwy. Jeśli to się nie powiedzie, dołącz "W" na końcu nazwy procedury zewnętrznej i wyszukuj ją ponownie.

- **Mechanizm.** Visual Basic używa platformy .NET Framework *invoke* (PInvoke) mechanizm do rozpoznawania i dostępu do procedur zewnętrznych. Instrukcja `Declare` i <xref:System.Runtime.InteropServices.DllImportAttribute> klasy zarówno używać tego mechanizmu automatycznie i nie trzeba żadnej wiedzy pinvoke. Aby uzyskać więcej informacji, zobacz [Przewodnik: Wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Jeśli procedura zewnętrzna jest uruchamiana poza wspólnym czasem wykonywania języka (CLR), jest to *kod niezarządzany.* Podczas wywoływania takiej procedury, na przykład funkcji interfejsu API systemu Windows lub metody COM, może narazić aplikację na zagrożenia bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [Wskazówki dotyczące bezpiecznego kodowania dla kodu niezarządzanego](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Przykład

Poniższy przykład deklaruje odwołanie zewnętrzne `Function` do procedury, która zwraca bieżącą nazwę użytkownika. Następnie wywołuje procedurę `GetUserNameA` zewnętrzną w `getUser` ramach procedury.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Przykład

Zapewnia <xref:System.Runtime.InteropServices.DllImportAttribute> alternatywny sposób korzystania z funkcji w kodzie niezarządzanym. Poniższy przykład deklaruje zaimportowane `Declare` funkcji bez użycia instrukcji.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrukcja funkcji](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call, instrukcja](../../../visual-basic/language-reference/statements/call-statement.md)
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
