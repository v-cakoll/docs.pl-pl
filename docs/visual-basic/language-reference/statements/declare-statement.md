---
title: DECLARE — instrukcja (Visual Basic)
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
ms.openlocfilehash: fbb7b4e118598157e2005469f89831df50de6576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638230"
---
# <a name="declare-statement"></a>Declare — Instrukcja
Deklaruje odwołanie do procedury zaimplementowanej w zewnętrznym pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`attributelist`|Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących elementów:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Private protected](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Opcjonalna. Określa zestaw znaków i plik wyszukiwania informacji. Może to być jeden z następujących elementów:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (ustawienie domyślne)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Opcjonalne, ale albo `Sub` lub `Function` musi znajdować się. Wskazuje, że procedura zewnętrzna nie zwraca wartości.|  
|`Function`|Opcjonalne, ale albo `Sub` lub `Function` musi znajdować się. Wskazuje, że procedura zewnętrzna, zwraca wartość.|  
|`name`|Wymagana. Nazwa tego odwołania zewnętrznego. Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).|  
|`Lib`|Wymagana. Wprowadza `Lib` klauzula, która identyfikuje zewnętrzny plik (DLL lub zasób kodu) zawierający zewnętrzną procedurę.|  
|`libname`|Wymagana. Nazwa pliku, który zawiera zadeklarowanej procedury.|  
|`Alias`|Opcjonalna. Wskazuje, że procedura deklarowanej nie identyfikowany w jego pliku według nazwy określonej w `name`. Należy określić jego identyfikacji w `aliasname`.|  
|`aliasname`|Wymagane w przypadku użycia `Alias` — słowo kluczowe. Ciąg, który identyfikuje procedurę opisaną w jeden z dwóch sposobów:<br /><br /> Nazwa punktu wejścia procedury w jego pliku w cudzysłowie (`""`)<br /><br /> —lub—<br /><br /> Znak numeru (`#`) następuje całkowitą określającą liczbę porządkową punktu wejścia procedury w ramach jego pliku|  
|`parameterlist`|Wymagane, jeśli parametry przyjmowane przez procedurę. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Jeśli wymagane `Function` jest określona i `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę procedurę.|  
  
## <a name="remarks"></a>Uwagi  
 Czasami zachodzi potrzeba wywoływanie procedury zdefiniowane w pliku (np. biblioteki DLL lub zasób kodu) poza projektem. Gdy to zrobisz, kompilator Visual Basic nie ma dostęp do informacji wymaganych do wywołania tej procedury poprawnie, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, który używa. `Declare` Instrukcja tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.  
  
 Możesz użyć `Declare` tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* odwołanie zewnętrzne musi być klasy, struktury lub modułu i nie może być plik źródłowy, przestrzeń nazw, interfejsu, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Domyślnie odwołuje się do zewnętrznego [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostępu. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.  
  
## <a name="rules"></a>reguły  
  
- **Atrybuty.** Atrybuty można zastosować do odwołania zewnętrznego. Każdego atrybutu, który należy zastosować obowiązuje tylko w projekcie, a nie w pliku zewnętrznym.  
  
- **Modyfikatory.** Procedury zewnętrzne są niejawnie [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć `Shared` — słowo kluczowe podczas deklarowania odwołanie zewnętrzne, a nie można zmienić jego stan udostępnionych.  
  
     Zewnętrzna procedura nie może uczestniczyć w zastępowanie, implementowanie elementów interfejsu lub obsługi zdarzeń. W związku z tym nie można użyć `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, lub `Handles` — słowo kluczowe w `Declare` instrukcji.  
  
- **Nazwę procedury zewnętrznej.** Nie trzeba nadać tym odwołania zewnętrznego taką samą nazwę (w `name`) jako nazwa punktu wejścia procedury w ramach jego plik zewnętrzny (`aliasname`). Możesz użyć `Alias` klauzulę, aby określić nazwę punktu wejścia. Może to być przydatne, jeśli procedura zewnętrzna ma taką samą nazwę jak zastrzeżone Modyfikatory języka Visual Basic lub zmienną, procedura lub innego elementu programowania, w tym samym zakresie.  
  
    > [!NOTE]
    >  Nazwy punktu wejścia w większości biblioteki DLL jest rozróżniana wielkość liter.  
  
- **Liczba zewnętrzną procedurę.** Alternatywnie, można użyć `Alias` klauzulę, aby określić liczbę porządkową punktu wejścia w tabeli eksportu pliku zewnętrznego. Aby to zrobić, możesz rozpocząć `aliasname` znakiem numeru (`#`). Może to być przydatne, jeśli dowolny znak nazwę procedury zewnętrznej jest niedozwolone w języku Visual Basic lub zewnętrznego pliku Eksportuje procedury bez nazwy.  
  
## <a name="data-type-rules"></a>Zasady dla typu danych  
  
- **Typ danych parametru.** Jeśli `Option Strict` jest `On`, należy określić typ danych każdego parametru w `parameterlist`. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. W ramach `parameterlist`, możesz użyć `As` klauzuli, aby określić typ danych argumentu, które mają być przekazane do każdego parametru.  
  
    > [!NOTE]
    >  Jeśli procedura zewnętrzna nie został napisany dla programu .NET Framework, możesz należy zadbać o odpowiadające typy danych. Na przykład, jeśli deklaruje odwołanie zewnętrzne do procedury języka Visual Basic 6.0 z `Integer` parametru (16 bitów w języku Visual Basic 6.0), należy zidentyfikować odpowiedni argument jako `Short` w `Declare` instrukcji, ponieważ jest to 16 - bit integer — typ w języku Visual Basic. Podobnie `Long` ma różną szerokość danych w Visual Basic 6.0 i `Date` implementowane w inny sposób.  
  
- **Zwracany typ danych.** Jeśli procedura zewnętrzna jest `Function` i `Option Strict` jest `On`, należy określić typ danych wartości zwracanej do wywołującego kodu. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
    > [!NOTE]
    >  Kompilator Visual Basic nie sprawdza, czy Twoje typy danych są zgodne z tymi zewnętrzną procedurę. Jeśli występuje niezgodność, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Runtime.InteropServices.MarshalDirectiveException> wyjątek w czasie wykonywania.  
  
- **Domyślne typy danych.** Jeśli `Option Strict` jest `Off` i nie określisz typ danych parametru w `parameterlist`, kompilator Visual Basic konwertuje odpowiadający argument do [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobnie jeśli nie określisz `returntype`, kompilator przyjmuje zwracany typ danych jako `Object`.  
  
    > [!NOTE]
    >  Masz do czynienia z zewnętrzną procedurę, która może być napisana na innej platformie, dlatego jest niebezpieczne, należy czynić żadnych założeń dotyczących typów danych lub zezwolić im na domyślne. Jest znacznie bezpieczniejsze, określ typ danych, każdy parametr i wartość zwracana, jeśli istnieje. Zwiększa to czytelność kodu.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Zakres.** Odwołanie zewnętrzne znajduje się w zakresie w całej swojej klasy, struktury lub modułu.  
  
- **Okres istnienia.** Odwołanie zewnętrzne ma ten sam okres istnienia jako klasy, struktury lub modułu, w którym jest zdeklarowana.  
  
- **Wywoływanie zewnętrzną procedurę.** Wywoływanie procedury zewnętrznej taki sam sposób, należy wywołać `Function` lub `Sub` procedury — przy użyciu w wyrażeniu, jeśli zostanie zwrócona wartość lub określając ją w [instrukcji Call](../../../visual-basic/language-reference/statements/call-statement.md) Jeśli nie zwraca wartości.  
  
     Przekazywanie argumentów do procedury zewnętrznego dokładnie określany przez `parameterlist` w `Declare` instrukcji. Nie uwzględnia jak parametry zostały pierwotnie zadeklarowana w pliku zewnętrznego. Podobnie w przypadku wartości zwracanej, użyj go dokładnie określonych przez `returntype` w `Declare` instrukcji.  
  
- **Zestawy znaków.** Można określić w `charsetmodifier` jak Visual Basic powinien kierować ciągi wywoływanych przez nią zewnętrzną procedurę. `Ansi` Modyfikator kieruje Visual Basic, aby kierować wszystkie ciągi jako wartości ANSI i `Unicode` modyfikator kieruje go do kierować wszystkie ciągi jako wartości Unicode. `Auto` Modyfikator kieruje Visual Basic, aby przeprowadzanie marshalingu ciągów zgodnie z .NET Framework reguł na podstawie odwołania zewnętrzne `name`, lub `aliasname` Jeśli zostanie określony. Wartość domyślna to `Ansi`.  
  
     `charsetmodifier` Określa również, jak Visual Basic powinna wyszukiwać zewnętrzną procedurę w jego pliku zewnętrznego. `Ansi` i `Unicode` bezpośrednie zarówno Visual Basic, aby wyszukać bez modyfikowania jej nazwy podczas wyszukiwania. `Auto` Określa, że Visual Basic, aby ustalić podstawowy zestaw znaków platformy uruchomieniowej i możliwie zmodyfikować nazwę procedury zewnętrznej w następujący sposób:  
  
    - Na platformie ANSI, takich jak Windows 95, Windows 98 lub Windows Millennium Edition Pierwsze spojrzenie procedura zewnętrzna, bez żadnych modyfikacji nazwy. W przypadku niepowodzenia należy dołączyć "A" na końcu nazwę procedury zewnętrznej, i wyszukaj ją ponownie.  
  
    - Na platformie Unicode, takich jak Windows NT, Windows 2000 lub Windows XP Pierwsze spojrzenie procedura zewnętrzna, bez żadnych modyfikacji nazwy. W przypadku niepowodzenia dołączenia "W" na końcu zewnętrzną procedurę nazwę i wyszukaj ją ponownie.  
  
- **Mechanizm.** Visual Basic używa programu .NET Framework *wywołania platformy* (funkcja PInvoke) mechanizm rozwiązywania i dostęp do zewnętrznej procedury. `Declare` Instrukcji i <xref:System.Runtime.InteropServices.DllImportAttribute> klasy zarówno automatycznie używać tego mechanizmu, a nie potrzebujesz żadnej wiedzy PInvoke. Aby uzyskać więcej informacji, zobacz [instruktażu: Wywoływanie Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Jeśli procedura zewnętrzna działa poza środowisko uruchomieniowe języka wspólnego (CLR), to *kod niezarządzany*. Podczas wywoływania takiej procedury, na przykład funkcja interfejsu API Windows lub metodę modelu COM może narazić aplikację na zagrożenia bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [bezpiecznego kodowania wytyczne dla niezarządzanego kodu](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje odwołanie zewnętrzne do `Function` procedury, która zwraca bieżącą nazwę użytkownika. Następnie wywołuje zewnętrzną procedurę `GetUserNameA` jako część `getUser` procedury.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="example"></a>Przykład  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Zapewnia alternatywny sposób korzystania z funkcji w niezarządzanym kodzie. Poniższy przykład deklaruje funkcję importowanych bez użycia `Declare` instrukcji.  
  
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
