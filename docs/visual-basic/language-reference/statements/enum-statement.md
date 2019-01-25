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
ms.openlocfilehash: f1086fdc26f1909e751617b78e0cd31f2a8b1b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656664"
---
# <a name="enum-statement-visual-basic"></a>Enum — Instrukcja (Visual Basic)
Deklaruje wyliczenie i definiuje wartości jego członków.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalna. Lista atrybutów, które są stosowane do tego wyliczenia. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").  
  
     <xref:System.FlagsAttribute> Atrybut wskazuje, że wartość instancja wyliczenia może zawierać wiele elementów członkowskich wyliczenia i że każdy element członkowski reprezentuje pole bitowe wartości wyliczenia.  
  
-   `accessmodifier`  
  
     Opcjonalna. Określa, jaki kod może uzyskać dostęp do tego wyliczenia. Może to być jeden z następujących elementów:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     Opcjonalna. Określa, że to wyliczenie programistyczny ponownie deklaruje i ukrywa o identycznej nazwie elementu programistycznego lub zestaw przeciążonych elementów w klasie bazowej. Można określić [cieni](../../../visual-basic/language-reference/modifiers/shadows.md) tylko w przypadku samego wyliczenia, a nie na jedną z jej członków.  
  
-   `enumerationname`  
  
     Wymagana. Nazwa wyliczenia. Informacje na temat prawidłowych nazw można zobaczyć [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Opcjonalna. Typ danych wyliczenie i jej elementów członkowskich.  
  
-   `memberlist`  
  
     Wymagana. Lista stałe element członkowski został zadeklarowany w tej instrukcji. Wiele elementów członkowskich pojawiają się na poszczególnych źródła wierszy kodu.  
  
     Każdy `member` ma następujące składni i części: `[<attribute list>] member name [ = initializer ]`  
  
    |Część|Opis|  
    |---|---|  
    |`membername`|Wymagana. Nazwa tego elementu członkowskiego.|  
    |`initializer`|Opcjonalna. Wyrażenie jest obliczane w czasie kompilacji i przypisane do tego elementu członkowskiego.|  
  
-   `End``Enum`  
  
     Kończy blok `Enum`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli masz zestaw niezmiennych wartości, które są logicznie powiązane ze sobą, można zdefiniować je ze sobą w wyliczeniu. Dzięki temu nazw opisowych dla wyliczenia i jej elementów członkowskich, które są łatwiejsze do zapamiętania niż ich wartości. Elementy członkowskie wyliczenia można następnie użyć w wielu miejscach w kodzie.  
  
 Zalety używania wyliczenia obejmują następujące czynności:  
  
-   Zmniejsza błędy spowodowane Transponowanie lub błędne liczby.  
  
-   Można łatwo zmienić wartości w przyszłości.  
  
-   Sprawia, że kod łatwiejsza do odczytania, co oznacza, że jest mniej prawdopodobne, że błędy będą wprowadzone.  
  
-   Zapewnia zgodność z nowszymi wersjami. Jeśli używasz wyliczenia, kod jest mniej prawdopodobne zakończyć się niepowodzeniem, jeśli w przyszłości ktoś zmienia wartości odpowiadające nazwy elementów członkowskich.  
  
 Wyliczenie ma nazwę odpowiedniego typu danych i zestaw elementów członkowskich. Każdy element członkowski reprezentuje stałą.  
  
 To wyliczenie zadeklarowane na poziomie klasy, struktury, modułu lub interfejsu, poza dowolnej procedury *elementu członkowskiego wyliczenia*. Jest on członkiem klasy, struktury, modułu lub interfejs, który deklaruje ją.  
  
 Element członkowski wyliczenia jest możliwy z dowolnego miejsca w obrębie klasy, struktury, modułu lub interfejsu. Kod poza klasą, struktury lub modułu musi kwalifikować nazwy wyliczenia elementu członkowskiego z nazwą tej klasy, struktury lub modułu. Aby uniknąć konieczności używać w pełni kwalifikowanych nazw, dodając [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji do pliku źródłowego.  
  
 Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasy, struktury, modułu lub interfejsu, jest członkiem obszaru nazw, w której występuje.  
  
 *Kontekst deklaracji* dla wyliczenia musi być plikiem źródłowym, przestrzeń nazw, klasy, struktury, modułu lub interfejsu, a nie może być procedurą. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Atrybuty można zastosować do wyliczenia jako całości, ale nie do swoich elementów członkowskich indywidualnie. Atrybut przyczynia się informacji metadanych zestawu.  
  
## <a name="data-type"></a>Typ danych  
 `Enum` Instrukcji można zadeklarować wyliczenie typu danych. Każdy element członkowski ma typ danych wyliczeniowych. Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort`.  
  
 Jeśli nie określisz `datatype` wyliczenia, każdy element członkowski ma typ danych jego `initializer`. Jeśli określisz zarówno `datatype` i `initializer`, typ danych `initializer` musi być konwertowany na `datatype`. Jeśli żadna `datatype` ani `initializer` jest obecny, wartość domyślna to typ danych `Integer`.  
  
## <a name="initializing-members"></a>Inicjowanie elementów członkowskich  
 `Enum` Instrukcji można zainicjować zawartość wybranych członków w `memberlist`. Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia można przypisać do elementu członkowskiego.  
  
 Jeśli nie określisz `initializer` dla elementu członkowskiego, Visual Basic inicjuje go do zera (jeśli jest on pierwszy `member` w `memberlist`), lub wartość większą o jeden niż bezpośrednio poprzedzający `member`.  
  
 Wyrażenie podane w każdym `initializer` może być dowolną kombinacją literały, inne stałe, które są już zdefiniowane i elementów członkowskich wyliczenia, które są już zdefiniowane, łącznie z poprzednim elementem tego wyliczenia. Za pomocą operatorów arytmetycznych i logicznych połączyć takie elementy.  
  
 Nie można używać zmiennych lub funkcji w `initializer`. Jednak można użyć słowa kluczowe konwersji takich jak `CByte` i `CShort`. Można również użyć `AscW` Jeśli wywołasz ze stałą `String` lub `Char` argumentu, ponieważ mogą być obliczane w czasie kompilacji.  
  
 Wyliczenia nie może mieć różne wartości zmiennoprzecinkowe. Jeśli członek nie zostanie przypisana wartość zmiennoprzecinkowa i `Option Strict` jest włączona, występuje błąd kompilatora. Jeśli `Option Strict` jest wyłączone, wartość jest automatycznie konwertowany do `Enum` typu.  
  
 Jeśli wartość elementu członkowskiego przekracza dopuszczalny zakres dla odpowiedniego typu danych lub zainicjować dowolnego elementu członkowskiego na wartość maksymalną dozwoloną przez odpowiedniego typu danych, kompilator zgłosi błąd.  
  
## <a name="modifiers"></a>Modyfikatory  
 Klasy, struktury, moduł i domyślnie wyliczenia elementu członkowskiego interfejsu publicznego dostępu. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu. Namespace domyślnie wyliczenia Członkowskiego dostęp zaprzyjaźniony. Można dostosować ich poziomy dostępu do publicznego, ale nie do prywatnych lub chronionych. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Wszystkie elementy członkowskie wyliczenia mają dostęp publiczny i nie można użyć dowolnego modyfikatory dostępu na nich. Jednak jeśli samego wyliczenia ma bardziej ograniczony poziom dostępu, wyliczenie określony poziom dostępu ma pierwszeństwo.  
  
 Domyślnie wszystkie wyliczenia są typy i ich pól są stałymi. W związku z tym `Shared`, `Static`, i `ReadOnly` słów kluczowych nie można użyć podczas deklarowania wyliczania lub jego składowych.  
  
## <a name="assigning-multiple-values"></a>Przypisywanie wielu wartości  
 Wyliczenia zazwyczaj reprezentują wartości wzajemnie się wykluczają. Jeśli dołączysz <xref:System.FlagsAttribute> atrybutu w `Enum` deklaracji, można zamiast tego przypisać wielu wartości do wystąpienia wyliczenia. <xref:System.FlagsAttribute> Atrybut określa, że wyliczenie być traktowane jako pole bitowe, czyli zestaw flag. Są to tak zwane *bitowe* wyliczenia.  
  
 Podczas deklarowania wyliczania, przy użyciu <xref:System.FlagsAttribute> atrybutu, zalecamy użycie potęgi 2, który jest, 1, 2, 4, 8, 16 i tak dalej dla wartości. Zalecamy również, czy można "None" nazwy elementu członkowskiego, w których wartość jest równa 0. Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `Enum` instrukcji. Należy zauważyć, że składowa jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metody znajduje się poza `Egg` klasy. W związku z tym `EggSizeEnum` jest w pełni kwalifikowany jako `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Enum` instrukcji, aby zdefiniować zestaw powiązanych nazwanych stałych. W tym przypadku wartości są kolory, których można projektować formularzach wprowadzania danych dla bazy danych.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia wartości, które zawierają zarówno dodatnie i ujemne liczby.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `As` klauzuli służy do określania `datatype` wyliczenia.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia bitowego wyliczenia. Wiele wartości można przypisać do wystąpienia bitowe wyliczenia. `Enum` Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że wyliczenia mogą być traktowane jako zestaw flag.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje iterację za pomocą wyliczania. Używa ona <xref:System.Enum.GetNames%2A> metodę, aby pobrać tablicę nazwy elementów członkowskich z wyliczenia i <xref:System.Enum.GetValues%2A> do pobrania tablicy wartości elementów członkowskich.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
