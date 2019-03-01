---
title: Const — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: eb99213287cda5ce7f9c3afe2998efb02ec68a03
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979076"
---
# <a name="const-statement-visual-basic"></a>Const — Instrukcja (Visual Basic)
Deklaruje i definiuje co najmniej jedną stałą.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalna. Lista atrybutów, które są stosowane do wszystkich stałych zadeklarowanych w tej instrukcji. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
 `accessmodifier`  
 Opcjonalna. Umożliwia określenie, jaki kod mogą uzyskiwać dostęp do tych stałych. Może być [publicznych](../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [prywatnej](../../../visual-basic/language-reference/modifiers/private.md), lub [Prywatny chroniony](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 Opcjonalna. Umożliwia to ponownie zadeklarować i ukrywanie elementu programistycznego w klasie bazowej. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Wymagana. Lista stałe został zadeklarowany w tej instrukcji.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Każdy `constant` ma następujące składni i części:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Część|Opis|  
|----------|-----------------|  
|`constantname`|Wymagana. Nazwa tej stałej. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Jeśli wymagane `Option Strict` jest `On`. Typ danych stałej.|  
|`initializer`|Wymagana. Wyrażenie jest obliczane w czasie kompilacji i przypisanym do stałej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli masz wartość, która nigdy się nie zmienia w aplikacji, można zdefiniować stałej nazwanej i zastępującą wartości literału. Nazwa jest łatwiejsze do zapamiętania niż określona wartość. Można zdefiniować stałą tylko raz i użyć go w wielu miejscach w kodzie. Jeśli w nowszej wersji. musisz ponownie definiować wartości, `Const` instrukcja jest jedynym miejscem, musisz wprowadzić zmiany.  
  
 Możesz użyć `Const` tylko na poziomie modułu lub procedury. Oznacza to, że *kontekst deklaracji* zmiennej musi być klasy, struktury, moduł, procedurę lub blok i nie może być plikiem źródłowym, przestrzeń nazw lub interfejsu. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Domyślnie lokalnym stałymi (wewnątrz procedury) publicznego dostępu, a nie można użyć dowolnego modyfikatory dostępu na nich. Klasy i moduł domyślny — stałe (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie stałe elementu członkowskiego struktury dostępu publicznego. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Stałą zadeklarowane na poziomie modułu, poza każda procedura jest *członek stałej*; jest członkiem klasy, struktury lub modułu, deklaruje ją.  
  
     Stałe zadeklarowane na poziomie procedury są *stała lokalna*; jest ono kontem lokalnym procedurę lub blok, który deklaruje ją.  
  
-   **Atrybuty.** Atrybuty można zastosować tylko do elementu członkowskiego stałych, a nie do lokalnego stałe. Atrybut przyczynia się informacji metadanych zestawu, które nie są istotne dla magazynów tymczasowych, takich jak lokalne stałe.  
  
-   **Modyfikatory.** Domyślnie są stałymi `Shared`, `Static`, i `ReadOnly`. Nie można użyć dowolnego z tych słów kluczowych, podczas deklarowania stałą.  
  
     Na poziomie procedury nie można użyć `Shadows` lub dowolne dostępu Modyfikatory do deklarowania lokalnym stałymi.  
  
-   **Kilka stałych.** Możesz zadeklarować kilka stałych w tej samej instrukcji deklaracji, określając `constantname` wchodzi w skład dla każdej z nich. Kilka stałych są oddzielone przecinkami.  
  
## <a name="data-type-rules"></a>Zasady dla typu danych  
  
-   **Typy danych.** `Const` Instrukcji może zadeklarować zmienną typu danych. Można określić dowolny typ danych lub nazwę wyliczenia.  
  
-   **Domyślny typ.** Jeśli nie określisz `datatype`, stałej ma typ danych `initializer`. Jeśli określisz zarówno `datatype` i `initializer`, typ danych `initializer` musi być konwertowany na `datatype`. Jeśli żadna `datatype` ani `initializer` jest obecny, wartość domyślna to typ danych `Object`.  
  
-   **Różne typy.** Można określić różne typy danych dla różnych stałych przy użyciu oddzielnego `As` klauzula dla każdej zmiennej można zadeklarować. Jednak nie można zadeklarować kilka stałych do tego samego typu przy użyciu wspólnego `As` klauzuli.  
  
-   **Inicjowanie.** Należy zainicjować wartość każdego stała `constantlist`. Możesz użyć `initializer` dostarczyć wyrażenie ma być przypisany do stałej. Wyrażenie może być dowolną kombinacją literały, inne stałe, które są już zdefiniowane i elementów członkowskich wyliczenia, które są już zdefiniowane. Za pomocą operatorów arytmetycznych i logicznych połączyć takie elementy.  
  
     Nie można używać zmiennych lub funkcji w `initializer`. Jednak można użyć słowa kluczowe konwersji takich jak `CByte` i `CShort`. Można również użyć `AscW` Jeśli wywołasz ze stałą `String` lub `Char` argumentu, ponieważ mogą być obliczane w czasie kompilacji.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zakres.** Lokalnym stałymi jest dostępny tylko w obrębie ich procedurą lub blokiem. Element członkowski stałe będą dostępne w dowolnym miejscu ich klasy, struktury lub modułu.  
  
-   **Kwalifikacja.** Kod poza klasą, struktury lub modułu musi kwalifikować nazwy stałą element członkowski o nazwie tej klasy, struktury lub modułu. Kod poza terenem procedurą lub blokiem nie może odwoływać się do dowolnego lokalnego stałych w ramach tej procedury lub bloku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Const` instrukcję, aby zadeklarować stałych do użycia zamiast wartości literału.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Przykład  
 Po zdefiniowaniu stałej z typem danych `Object`, kompilator Visual Basic nadaje jej typ `initializer`, zamiast `Object`. W poniższym przykładzie stała `naturalLogBase` ma typu run-time `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 W poprzednim przykładzie użyto <xref:System.Type.ToString%2A> metody <xref:System.Type> obiektu zwróconego przez [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), ponieważ <xref:System.Type> nie można przekonwertować na `String` przy użyciu `CStr`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Stałe i wyliczenia](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
