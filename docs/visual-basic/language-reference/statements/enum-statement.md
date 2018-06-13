---
title: Enum — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234019"
---
# <a name="enum-statement-visual-basic"></a>Enum — Instrukcja (Visual Basic)
Deklaruje wyliczenie i definiuje wartości jego elementów członkowskich.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalna. Lista atrybutów, które są stosowane do tego wyliczenia. Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
     <xref:System.FlagsAttribute> Atrybut wskazuje, że wartości wyliczenia wystąpienia może zawierać wiele elementy członkowskie wyliczenia i że każdy element członkowski reprezentuje pole bitowe wartości wyliczenia.  
  
-   `accessmodifier`  
  
     Opcjonalna. Określa, jaki kod mogą uzyskiwać dostęp do tego wyliczenia. Może to być jeden z następujących elementów:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Friend chronionych](../../language-reference/modifiers/protected-friend.md)
    
    - [Prywatne chronione](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     Opcjonalna. Określa, że to wyliczenie programistyczny ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej. Można określić [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) tylko na wyliczenie samego, nie na żadnym z jego elementów członkowskich.  
  
-   `enumerationname`  
  
     Wymagana. Nazwa wyliczenia. Uzyskać informacji o prawidłowych nazw, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Opcjonalna. Typ danych wyliczenia i wszyscy jej członkowie.  
  
-   `memberlist`  
  
     Wymagana. Lista stałe element członkowski został zadeklarowany w tej instrukcji. Wiele elementów członkowskich są wyświetlane na poszczególnych źródła wierszy kodu.  
  
     Każdy `member` ma następujące składni i części: `[<attribute list>] member name [ = initializer ]`  
  
    |Część|Opis|  
    |---|---|  
    |`membername`|Wymagana. Nazwa tego elementu członkowskiego.|  
    |`initializer`|Opcjonalna. Wyrażenie, które jest obliczane w czasie kompilacji i przypisane do tego elementu członkowskiego.|  
  
-   `End``Enum`  
  
     Kończy blok `Enum`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli masz zestaw wartości niezmiennych, logicznie powiązanych ze sobą, należy je zdefiniować w razem w wyliczeniu. Zapewnia to znaczące nazwy dla wyliczenia i jej elementów członkowskich, które są łatwiejsze do zapamiętania niż ich wartości. Elementy członkowskie wyliczenia można następnie użyć w wielu miejscach w kodzie.  
  
 Korzyści wynikające ze stosowania wyliczenia są następujące:  
  
-   Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.  
  
-   Można łatwo zmienić wartości w przyszłości.  
  
-   Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy zostaną wprowadzone.  
  
-   Zapewnia zgodność z nowszymi wersjami. Jeśli używasz wyliczenia, kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.  
  
 Wyliczenie ma nazwę, podstawowym typem danych i zestaw elementów członkowskich. Każdy element członkowski reprezentuje stałą.  
  
 To wyliczenie zadeklarowane na klasy, struktury, modułu lub poziom interfejsu poza dowolnej procedury *elementu członkowskiego wyliczenia*. Jest elementem członkowskim klasy, struktury, modułu lub interfejsu, który deklaruje go.  
  
 Element członkowski wyliczenia można uzyskać z dowolnego miejsca w obrębie klasy, struktury, modułu lub interfejs. Kod poza klasą, strukturą lub modułu muszą nazwy wyliczenia elementu członkowskiego z nazwą tej klasy, struktury lub modułu. Aby uniknąć konieczności używania w pełni kwalifikowane nazwy przez dodanie [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji do pliku źródłowego.  
  
 Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasy, struktury, modułu lub interfejsu, jest członkiem przestrzeni nazw, w których występuje.  
  
 *Kontekście deklaracji* wyliczenia musi być pliku źródłowego, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedury. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Można zastosować atrybutów do wyliczenia jako całość, ale nie do jego elementów członkowskich pojedynczo. Atrybut wspiera informacje dotyczące metadanych zestawu.  
  
## <a name="data-type"></a>Typ danych  
 `Enum` Instrukcji można zadeklarować typ danych wyliczenia. Każdy element członkowski ma typ danych wyliczenia. Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort`.  
  
 Jeśli nie określisz `datatype` wyliczenia, każdy element członkowski ma typ danych jego `initializer`. Jeśli możesz określić ich obu `datatype` i `initializer`, typ danych miary `initializer` musi być możliwe do przekonwertowania na `datatype`. Jeśli żadna `datatype` ani `initializer` ma typ danych wartości domyślnych do `Integer`.  
  
## <a name="initializing-members"></a>Podczas inicjowania elementów członkowskich  
 `Enum` Instrukcji można zainicjować zawartość wybranych członków w `memberlist`. Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia w można przypisać do elementu członkowskiego.  
  
 Jeśli nie określisz `initializer` dla elementu członkowskiego języka Visual Basic inicjowane albo zero (jeśli jest pierwszy `member` w `memberlist`), lub wartość większą o jeden niż bezpośrednio przed `member`.  
  
 Wyrażenie podane w każdym `initializer` może być dowolną kombinacją literały, inne stałe, które zostały już zdefiniowane i elementy członkowskie wyliczenia, które zostały już zdefiniowane, włączając poprzedni element członkowski tego wyliczenia. Operatory arytmetyczne i logiczne umożliwia łączenie takich elementów.  
  
 Nie można używać zmiennych lub funkcje w `initializer`. Jednak takie jak można użyć słowa kluczowe konwersji `CByte` i `CShort`. Można również użyć `AscW` połączeń ze stałą `String` lub `Char` argumentu, ponieważ może zostać oceniony w czasie kompilacji.  
  
 Wyliczenia nie może mieć wartości zmiennoprzecinkowych. Jeśli element członkowski jest przypisywana wartość zmiennoprzecinkowa i `Option Strict` ma wartość on, wystąpi błąd kompilatora. Jeśli `Option Strict` jest wyłączony, wartość jest automatycznie konwertowany do `Enum` typu.  
  
 Jeśli wartość elementu członkowskiego przekracza dopuszczalny zakres dla odpowiedniego typu danych lub zainicjować członków do maksymalna wartość dozwolona przez podstawowy typ danych, kompilator zgłasza błąd.  
  
## <a name="modifiers"></a>Modyfikatory  
 Klasy, struktury, moduł i domyślnie wyliczenia elementu członkowskiego interfejsu dostępu publicznego. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Namespace elementu członkowskiego wyliczenia domyślną wartość przyjaznego dostępu. Można dostosować ich poziomy dostępu publicznego, ale nie prywatne lub chronione. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Wszystkie elementy członkowskie wyliczenia mają dostęp publiczny i nie można użyć dowolnego modyfikatorów dostępu na nich. Jednak jeśli wyliczenia sam bardziej ograniczony poziom dostępu, wyliczenie określony poziom dostępu ma priorytet.  
  
 Domyślnie wszystkie wyliczenia są typy i ich pola są stałe. W związku z tym `Shared`, `Static`, i `ReadOnly` nie można użyć słowa kluczowe przy deklarowaniu wyliczenie lub jego elementów członkowskich.  
  
## <a name="assigning-multiple-values"></a>Przypisywanie wielu wartości  
 Wyliczenia zazwyczaj reprezentują wartości wykluczają się wzajemnie. W tym <xref:System.FlagsAttribute> atrybutu w `Enum` deklaracji, zamiast tego do można przypisać wielu wartości wystąpienia wyliczenia. <xref:System.FlagsAttribute> Atrybut określa, że wyliczenia być traktowane jako pole bitowe, czyli zestaw flag. Są one nazywane *bitowe* wyliczenia.  
  
 Gdy zadeklarować wyliczenia za pomocą <xref:System.FlagsAttribute> atrybutu, firma Microsoft zaleca użycie potęgami liczby 2, który jest, 1, 2, 4, 8, 16 i tak dalej dla wartości. Ponadto zaleca się "None" nazwę elementu członkowskiego, którego wartość jest równa 0. Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Enum` instrukcji. Należy pamiętać, że element członkowski jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metody jest poza `Egg` klasy. W związku z tym `EggSizeEnum` jest w pełni kwalifikowany jako `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Enum` instrukcję, aby zdefiniować powiązany zestaw o nazwie wartości stałych. W tym przypadku wartości są kolorów, które można wybrać do projektowania formularzy zapis danych dla bazy danych.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono wartości, które obejmują zarówno dodatnią, a liczby ujemne.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `As` klauzuli służy do określania `datatype` wyliczenia.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób korzystania z bitowego wyliczenia. Wiele wartości można przypisać do wystąpienia z bitowego wyliczenia. `Enum` Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że wyliczenia może być traktowana jako zestaw flag.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład iterację wyliczenia. Używa <xref:System.Enum.GetNames%2A> metoda pobierania tablicę nazw elementów członkowskich z wyliczenia, i <xref:System.Enum.GetValues%2A> do pobrania tablicy wartości elementu członkowskiego.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
