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
ms.openlocfilehash: 75d41883aefbaa54eb836d89bbfc034d99b7bba0
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
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
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących elementów:<br /><br /> -   [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Friend chronionych](../../language-reference/modifiers/protected-friend.md)<br />- [Prywatne chronione](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Opcjonalna. Określa zestaw znaków i plik wyszukiwania informacji. Może to być jeden z następujących elementów:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (ustawienie domyślne)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Opcjonalne, ale albo `Sub` lub `Function` musi występować. Wskazuje, że procedura zewnętrzna nie zwraca wartości.|  
|`Function`|Opcjonalne, ale albo `Sub` lub `Function` musi występować. Wskazuje, że procedura zewnętrzna zwraca wartość.|  
|`name`|Wymagana. Nazwa tego odwołania zewnętrznego. Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).|  
|`Lib`|Wymagana. Wprowadza `Lib` klauzuli, która identyfikuje zewnętrzny plik (DLL lub zasób kodu) zawierający zewnętrzną procedurę.|  
|`libname`|Wymagana. Nazwa pliku, który zawiera procedury zadeklarowane.|  
|`Alias`|Opcjonalna. Wskazuje procedury został zadeklarowany nie można zidentyfikować w swoim pliku według nazwy określone w `name`. Określ jego identyfikację w `aliasname`.|  
|`aliasname`|Wymagane w przypadku użycia `Alias` — słowo kluczowe. Ciąg, który identyfikuje procedury w jeden z dwóch sposobów:<br /><br /> Nazwa punktu wejścia procedury w jego pliku w cudzysłowy (`""`)<br /><br /> —lub—<br /><br /> Znak liczby (`#`) następuje liczba całkowita określająca liczbę porządkową punktu wejścia procedury w jego pliku|  
|`parameterlist`|Wymagane, jeśli parametry przyjmowane przez procedurę. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Jeśli wymagane `Function` określono i `Option Strict` jest `On`. Typ danych wartości zwracanej przez procedurę.|  
  
## <a name="remarks"></a>Uwagi  
 Czasami trzeba wywołać procedurę zdefiniowane w pliku (np. DLL lub zasób kodu) poza projektem. Po wykonaniu tej czynności kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie, z którym znajduje się procedura, jak określono jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, który używa. `Declare` Instrukcji tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 Można użyć `Declare` tylko na poziomie modułu. Oznacza to, że *kontekście deklaracji* odwołanie zewnętrzne musi być klasą, strukturą lub modułu i nie może być plik źródłowy, przestrzeni nazw, interfejsu, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Domyślnie odwołuje się do zewnętrznego [publicznego](../../../visual-basic/language-reference/modifiers/public.md) dostępu. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.  
  
## <a name="rules"></a>Reguły  
  
-   **Atrybuty.** Atrybuty można zastosować do odwołania zewnętrznego. Wszelkie atrybuty, które stosujesz ma wpływ tylko w projekcie, a nie w pliku zewnętrznym.  
  
-   **Modyfikatory.** Procedury zewnętrzne są niejawnie [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć `Shared` — słowo kluczowe podczas deklarowania odwołanie zewnętrzne i nie można zmienić stanu udostępnionego.  
  
     Zewnętrzna procedura nie może uczestniczyć w zastępowanie, implementować członków interfejsu lub obsługi zdarzeń. W związku z tym nie można użyć `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, lub `Handles` — słowo kluczowe w `Declare` instrukcji.  
  
-   **Nazwę procedury zewnętrznej.** Nie trzeba podać to odwołanie zewnętrzne tej samej nazwie (w `name`) jako nazwę punktu wejścia procedury w ramach jego zewnętrzny plik (`aliasname`). Można użyć `Alias` klauzuli do określenia nazwy punktu wejścia. Może to być przydatne, jeśli procedura zewnętrzna ma taką samą nazwę jak modyfikujący zastrzeżone Visual Basic lub zmienną, procedurę lub innych elementów programowania, w tym samym zakresie.  
  
    > [!NOTE]
    >  Nazwy punktu wejścia w większości biblioteki DLL jest rozróżniana wielkość liter.  
  
-   **Numer procedury zewnętrznego.** Alternatywnie można użyć `Alias` klauzuli, aby określić liczbę porządkową punkt wejścia w tabeli eksportu zewnętrznego pliku. Aby to zrobić, należy rozpocząć `aliasname` ze znakiem numeru (`#`). Może to być przydatne, jeśli dowolny znak nazwę procedury zewnętrznej jest niedozwolone w języku Visual Basic lub zewnętrzny plik eksportuje procedury bez nazwy.  
  
## <a name="data-type-rules"></a>Zasady dla typu danych  
  
-   **Typ danych parametru.** Jeśli `Option Strict` jest `On`, należy określić typ każdego parametru w danych `parameterlist`. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. W ramach `parameterlist`, możesz użyć `As` klauzuli, aby określić typ danych argumentu, które mają być przekazane do każdego parametru.  
  
    > [!NOTE]
    >  Jeśli procedura zewnętrzna nie został zapisany dla programu .NET Framework, użytkownik musi zajmie się odpowiadające typów danych. Na przykład, jeśli Zadeklaruj odwołanie zewnętrzne Visual Basic 6.0 procedury z `Integer` parametr (16 bitów w Visual Basic 6.0), należy zidentyfikować odpowiedni argument jako `Short` w `Declare` instrukcji, ponieważ jest to 16 - bit typu Liczba całkowita w języku Visual Basic. Podobnie `Long` ma szerokość różnych danych w Visual Basic 6.0 i `Date` jest zaimplementowana w inny sposób.  
  
-   **Zwraca typ danych.** Jeśli procedura zewnętrzna jest `Function` i `Option Strict` jest `On`, należy określić typ danych wartości zwracanej do wywołującego kodu. Może to być dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
    > [!NOTE]
    >  Kompilator Visual Basic nie sprawdza, czy typów danych są zgodne z tymi procedury zewnętrznego. Jeśli występuje niezgodność, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Runtime.InteropServices.MarshalDirectiveException> wyjątek w czasie wykonywania.  
  
-   **Domyślne typy danych.** Jeśli `Option Strict` jest `Off` i nie należy określać typ danych parametru w `parameterlist`, kompilator Visual Basic konwertuje odpowiedni argument [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobnie jeśli nie określisz `returntype`, kompilator ma typ zwracanych danych `Object`.  
  
    > [!NOTE]
    >  Ponieważ dotyczących procedury zewnętrznego, który może być zapisany na innej platformie, jest niebezpieczne przyjmuje żadnych założeń dotyczących typów danych lub zezwolić im na domyślne. Jest znacznie bezpieczniejsze określić typ danych każdego parametru i wartości zwracanej, jeśli istnieje. Poprawia to również czytelność kodu.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zakres.** Odwołanie zewnętrzne jest w zakresie w całym jej klasy, struktury lub modułu.  
  
-   **Okres istnienia.** Odwołanie zewnętrzne ma lifetime klasy, struktury lub moduł, w którym jest zadeklarowany.  
  
-   **Wywołanie procedury zewnętrznego.** Wywołanie procedury zewnętrznego taki sam sposób, należy wywołać `Function` lub `Sub` procedury — za pomocą w wyrażeniu, jeśli wartość jest zwracana lub określając je w [instrukcji Call](../../../visual-basic/language-reference/statements/call-statement.md) Jeśli nie zwraca wartości.  
  
     Przekazywanie argumentów do procedury zewnętrznego dokładnie określoną przez `parameterlist` w `Declare` instrukcji. Nie uwzględniać jak parametry zostały pierwotnie zadeklarowany w pliku zewnętrznym. Podobnie w przypadku wartości zwracanej, użyj go dokładnie określoną przez `returntype` w `Declare` instrukcji.  
  
-   **Zestawy znaków.** Można określić w `charsetmodifier` jak Visual Basic powinien kierować ciągi wywołuje procedury zewnętrznego. `Ansi` Modyfikator kieruje Visual Basic, aby kierować wszystkie ciągi jako wartości ANSI i `Unicode` modyfikator kieruje je do kierować wszystkie ciągi jako wartości Unicode. `Auto` Modyfikator Określa, że program Visual Basic kierowanie ciągów zgodnie z .NET Framework zasady oparte na odwołanie zewnętrzne `name`, lub `aliasname` Jeśli zostanie określony. Wartość domyślna to `Ansi`.  
  
     `charsetmodifier` Określa również sposób Visual Basic powinien wyglądać zewnętrznej procedury w ramach jego zewnętrznego pliku. `Ansi` i `Unicode` zarówno bezpośrednie Visual Basic w celu wyszukania bez modyfikowania jej nazwy podczas wyszukiwania. `Auto` Określa, że Visual Basic, aby ustalić podstawowy zestaw znaków platformy środowiska wykonawczego i możliwie zmodyfikować nazwę procedury zewnętrznej w następujący sposób:  
  
    -   Na platformie ANSI, takie jak Windows 95, Windows 98 lub Windows Millennium Edition Pierwsze spojrzenie procedury zewnętrznego bez żadnych modyfikacji nazwy. W przypadku niepowodzenia dołączyć "A" na końcu nazwę procedury zewnętrznej, i wyszukiwać go ponownie.  
  
    -   Na platformie Unicode, takie jak Windows NT, Windows 2000 lub Windows XP Pierwsze spojrzenie procedury zewnętrznego bez żadnych modyfikacji nazwy. W przypadku niepowodzenia Dołącz "W" na końcu procedury zewnętrznego nazwy i wyszukiwać go ponownie.  
  
-   **Mechanizm.** Korzysta z programu Visual Basic .NET Framework *wywołanie platformy* mechanizmu (PInvoke) do rozwiązania i dostępu do zewnętrznych procedur. `Declare` Instrukcji i <xref:System.Runtime.InteropServices.DllImportAttribute> klasy zarówno automatycznie używać ten mechanizm i nie są wszystkie informacje dotyczące funkcji PInvoke. Aby uzyskać więcej informacji, zobacz [wskazówki: wywoływanie Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Jeśli procedura zewnętrzna działa poza środowisko uruchomieniowe języka wspólnego (CLR), jest *niezarządzany kod*. Podczas wywoływania takich procedury, na przykład funkcji Win32 API lub metodę COM może narazić aplikacji na zagrożenia bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [Secure kodowania wytycznymi dla kodu niezarządzanego](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje odwołanie zewnętrzne do `Function` procedury, która zwraca nazwę bieżącego użytkownika. Następnie wywołuje procedury zewnętrznego `GetUserNameA` jako część `getUser` procedury.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Zapewnia alternatywny sposób użycia funkcji za pomocą kodu niezarządzanego. Poniższy przykład deklaruje funkcję zaimportowane bez użycia `Declare` instrukcji.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Call, instrukcja](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
