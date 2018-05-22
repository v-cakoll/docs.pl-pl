---
title: Const — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: a5842e284eaa858e7a66160060123edc21858a3a
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
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
 Opcjonalna. Lista atrybutów, które są stosowane do wszystkich stałych zadeklarowany w tej instrukcji. Zobacz [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
 `accessmodifier`  
 Opcjonalna. Umożliwia określenie, jakie kodu mogą uzyskiwać dostęp do tych stałych. Może być [publicznego](../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [prywatnej](../../../visual-basic/language-reference/modifiers/private.md), lub [Prywatne chronione](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 Opcjonalna. Umożliwia to ponownie zadeklarować i ukrywanie elementu programistycznego w klasie podstawowej. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Wymagana. Lista stałe został zadeklarowany w tej instrukcji.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Każdy `constant` ma następujące składni i części:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Część|Opis|  
|----------|-----------------|  
|`constantname`|Wymagana. Nazwa stałej. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Jeśli wymagane `Option Strict` jest `On`. Typ danych stałej.|  
|`initializer`|Wymagana. Wyrażenie, które jest obliczane w czasie kompilacji i przypisane do stałej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość nie ulega zmianie w aplikacji, można zdefiniować nazwanej stałej i zastępującą wartość literału. Nazwa jest łatwiejsze do zapamiętania niż określona wartość. Można zdefiniować stała tylko raz i używany w wielu miejscach w kodzie. Jeśli w nowszej wersji. musisz ponownie zdefiniować wartości, `Const` instrukcja jest tylko miejscu, należy wprowadzić zmiany.  
  
 Można użyć `Const` tylko na poziomie modułu lub procedury. Oznacza to, że *kontekście deklaracji* dla zmiennej musi być klasy, struktury, modułu, procedurę lub blok i nie może być plik źródłowy, przestrzeni nazw lub interfejs. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Domyślnie lokalne — stałe (wewnątrz procedury) dostępu publicznego, a nie można użyć dowolnego modyfikatory dostępu na nich. Klasy i moduł domyślny — stałe (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie stałe elementu członkowskiego struktury dostępu publicznego. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Stała zadeklarowane na poziomie modułu, poza każda procedura jest *członek stałej*; jest elementem członkowskim klasy, struktury lub moduł które deklaruje go.  
  
     Stałe zadeklarowane na poziomie procedury są *stałą lokalną*; jest lokalny dla procedury lub bloku, który deklaruje go.  
  
-   **Atrybuty.** Atrybuty można stosować tylko do elementu członkowskiego stałe, a nie do lokalnego stałe. Atrybut przyczynia się informacji metadanych zestawu, który nie jest zrozumiały dla tymczasowego magazynu, takich jak lokalny stałe.  
  
-   **Modyfikatory.** Domyślnie wszystkie stałe są `Shared`, `Static`, i `ReadOnly`. Nie można użyć dowolnego z następujących słów kluczowych przy deklarowaniu stałą.  
  
     Na poziomie procedury nie można użyć `Shadows` lub dowolnego dostępu Modyfikatory Aby zadeklarować lokalnego stałe.  
  
-   **Wiele stałych.** Można zadeklarować kilka stałych w tej samej instrukcji deklaracji, określając `constantname` część dla każdej z nich. Wiele stałych są oddzielone przecinkami.  
  
## <a name="data-type-rules"></a>Zasady dla typu danych  
  
-   **Typy danych.** `Const` Instrukcji można zadeklarować zmiennej typu danych. Można określić dowolny typ danych lub nazwa wyliczenia.  
  
-   **Domyślny typ.** Jeśli nie określisz `datatype`, stałej ma typ danych `initializer`. Jeśli możesz określić ich obu `datatype` i `initializer`, typ danych miary `initializer` musi być możliwe do przekonwertowania na `datatype`. Jeśli żadna `datatype` ani `initializer` ma typ danych wartości domyślnych do `Object`.  
  
-   **Różne typy.** Można określić różne typy danych dla różnych stałe za pomocą oddzielnego `As` klauzula dla każdej zmiennej można zadeklarować. Jednak nie można zadeklarować kilka stałych do tego samego typu przy użyciu wspólnego `As` klauzuli.  
  
-   **Inicjowanie.** Należy zainicjować wartość stałą, co w `constantlist`. Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia do przypisania do stałej. Wyrażenie może być dowolną kombinacją literały, inne stałe, które zostały już zdefiniowane i elementy członkowskie wyliczenia, które zostały już zdefiniowane. Operatory arytmetyczne i logiczne umożliwia łączenie takich elementów.  
  
     Nie można używać zmiennych lub funkcje w `initializer`. Jednak takie jak można użyć słowa kluczowe konwersji `CByte` i `CShort`. Można również użyć `AscW` połączeń ze stałą `String` lub `Char` argumentu, ponieważ może zostać oceniony w czasie kompilacji.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zakres.** Stałe lokalnego jest dostępny tylko w obrębie ich procedurę lub blok. Element członkowski stałe są dostępne z dowolnego miejsca w ich klasy, struktury lub modułu.  
  
-   **Kwalifikacji.** Kod poza klasą, strukturą lub modułu muszą nazwy stałą elementu członkowskiego z nazwą tej klasy, struktury lub modułu. Kod poza procedurę lub blok nie może odwoływać się do żadnych lokalnych stałych w ramach tej procedury lub bloku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Const` instrukcji, aby zadeklarować stałych do użycia zamiast wartości literałów.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W przypadku definiowania stałą z typem danych `Object`, kompilator Visual Basic zapewnia jej typ `initializer`, zamiast `Object`. W poniższym przykładzie, stała `naturalLogBase` ma typu run-time `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 W poprzednim przykładzie użyto <xref:System.Type.ToString%2A> metoda <xref:System.Type> obiektu zwróconego przez [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), ponieważ <xref:System.Type> nie można przekonwertować na `String` przy użyciu `CStr`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Stałe i wyliczenia](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
