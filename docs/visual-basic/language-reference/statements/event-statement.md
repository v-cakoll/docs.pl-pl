---
title: Event — instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Event
- vb.Custom
helpviewer_keywords:
- Event statement [Visual Basic]
- declaring events [Visual Basic], syntax
- Public keyword [Visual Basic], Event statements
- Custom keyword [Visual Basic]
- declarations [Visual Basic], events
- event keyword [Visual Basic]
- WithEvents keyword [Visual Basic], Event statements
- events [Visual Basic], declaring
- ByVal keyword [Visual Basic], Event statements
- events [Visual Basic], custom
- ByRef keyword [Visual Basic], Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
ms.openlocfilehash: 2f600f3ed37f38ddd7d86300231e0c447f458aa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638106"
---
# <a name="event-statement"></a>Event — Instrukcja
Deklaruje zdarzenie zdefiniowane przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Części  
  
|Część|Opis|  
|---|---|  
|`attrlist`|Opcjonalna. Lista atrybutów, które są stosowane do tego zdarzenia. Wiele atrybutów rozdziela się przecinkami. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").|  
|`accessmodifier`|Opcjonalna. Określa, jaki kod może uzyskać dostęp do zdarzenia. Może to być jeden z następujących elementów:<br /><br /> -   [Publiczne](../../../visual-basic/language-reference/modifiers/public.md)— wszelki kod, który mogą uzyskiwać dostęp do elementu, który deklaruje ją do niego dostęp.<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)— tylko do kodu w swojej klasie lub klasie pochodnej do niego dostęp.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— tylko do kodu z tego samego zestawu do niego dostęp.<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)— tylko do kodu w elemencie który deklaruje ją do niego dostęp.<br /> -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)— tylko do kodu w klasie zdarzeń, klasę pochodną lub tego samego zestawu do niego dostęp. <br />- [Prywatny chroniony](../../language-reference/modifiers/private-protected.md)— tylko do kodu w klasie zdarzenia lub klasę pochodną z tego samego zestawu do niego dostęp.|  
|`Shared`|Opcjonalna. Określa, czy to zdarzenie nie jest skojarzony z określonego wystąpienia klasy lub struktury.|  
|`Shadows`|Opcjonalna. Wskazuje, że to zdarzenie programistyczny ponownie deklaruje i ukrywa o identycznej nazwie elementu programistycznego lub zestaw przeciążonych elementów w klasie bazowej. Można w tle dowolnego typu element zadeklarowany za pomocą dowolnego typu.<br /><br /> Zasłonięte element jest niedostępny z w klasie pochodnej, która zasłania, z wyjątkiem sytuacji, z którym przesłaniania elementu jest niedostępny. Na przykład jeśli `Private` element zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.|  
|`eventname`|Wymagana. Nazwa zdarzenia; następuje standardową konwencją nazw zmiennych.|  
|`parameterlist`|Opcjonalna. Lista zmiennych lokalnych, które reprezentują parametry tego zdarzenia. Należy ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`Implements`|Opcjonalna. Wskazuje, że to zdarzenie implementuje zdarzenia interfejsu.|  
|`implementslist`|Jeśli wymagane `Implements` podano. Lista `Sub` procedury są wdrożone. Wiele procedur są oddzielone przecinkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Każdy `implementedprocedure` ma następujące składni i części:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` — Wymagane. Implementuje Nazwa interfejsu, że tej procedury zawierający klasy lub struktury.<br />-   `Definedname` — Wymagane. Nazwa, za pomocą którego procedura jest zdefiniowany w `interface`. To nie musi być taka sama jak `name`, nazwa która używa tej procedury do zaimplementowania zdefiniowanej procedury.|  
|`Custom`|Wymagana. Zdarzenia są zadeklarowane jako `Custom` musi definiować niestandardowe `AddHandler`, `RemoveHandler`, i `RaiseEvent` metod dostępu.|  
|`delegatename`|Opcjonalna. Nazwa delegat, który określa podpis, program obsługi zdarzeń.|  
|`AddHandler`|Wymagana. Deklaruje `AddHandler` dostępu, który określa instrukcji do wykonania po dodaniu programu obsługi zdarzeń, jawnie za pomocą `AddHandler` instrukcji lub niejawnie, przy użyciu `Handles` klauzuli.|  
|`End AddHandler`|Wymagana. Kończy blok `AddHandler`.|  
|`value`|Wymagana. Nazwa parametru.|  
|`RemoveHandler`|Wymagana. Deklaruje `RemoveHandler` dostępu, który określa instrukcje wykonywania, gdy program obsługi zdarzeń jest usuwana za pomocą `RemoveHandler` instrukcji.|  
|`End RemoveHandler`|Wymagana. Kończy blok `RemoveHandler`.|  
|`RaiseEvent`|Wymagana. Deklaruje `RaiseEvent` dostępu, który określa instrukcji do wykonania, gdy zdarzenie jest wywoływane przy użyciu `RaiseEvent` instrukcji. Zazwyczaj wywołuje to lista delegatów utrzymywane przez `AddHandler` i `RemoveHandler` metod dostępu.|  
|`End RaiseEvent`|Wymagana. Kończy blok `RaiseEvent`.|  
|`delegatesignature`|Wymagana. Lista parametrów, który odpowiada parametrów wymaganych przez `delegatename` delegować. Należy ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`statements`|Opcjonalna. Instrukcje zawierające organów `AddHandler`, `RemoveHandler`, i `RaiseEvent` metody.|  
|`End Event`|Wymagana. Kończy blok `Event`.|  
  
## <a name="remarks"></a>Uwagi  
 Po zdarzeniu został zadeklarowany, użyj `RaiseEvent` instrukcję, aby zgłosić zdarzenie. Typowe zdarzenia może być zadeklarowana i wywoływane, jak pokazano w poniższym fragmenty:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
>  Można zadeklarować argumenty zdarzenia, tak jak argumenty procedur z następującymi wyjątkami: zdarzenia nie mają nazwane argumenty `ParamArray` argumentów, lub `Optional` argumentów. Nie są zwracane wartości zdarzeń.  
  
 Aby obsłużyć zdarzenie, musisz skojarzyć go z procedury obsługi zdarzeń za pomocą `Handles` lub `AddHandler` instrukcji. Podpisy procedurę i zdarzenia muszą być zgodne. Aby obsłużyć zdarzenie udostępnionego, należy użyć `AddHandler` instrukcji.  
  
 Możesz użyć `Event` tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* zdarzenie musi być klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeń nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 W większości przypadków można użyć pierwszej składni w składni części tego tematu do deklarowania zdarzenia. Jednak niektóre scenariusze wymagają, że masz większą kontrolę nad zachowaniem szczegółowe zdarzenia. Ostatnie składni w sekcji składni w tym temacie, który używa `Custom` — słowo kluczowe, zawiera tę kontrolkę, umożliwiając definiowanie zdarzeń niestandardowych. W przypadku niestandardowych określasz dokładnie co występuje, gdy kod dodaje lub usuwa program obsługi zdarzeń do lub ze zdarzenia lub gdy kod wywołuje zdarzenie. Aby uzyskać przykłady, zobacz [jak: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) i [jak: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zdarzeń odliczanie sekund od 10 do 0. Kod ilustruje kilka powiązanych zdarzeń do metod, właściwości i instrukcji. Obejmuje to `RaiseEvent` instrukcji.  
  
 Klasa, która wywołuje zdarzenie, jest źródłem zdarzeń i metody, które przetwarzają zdarzenia są procedury obsługi zdarzeń. Źródło zdarzenia może mieć wielu obsług do zdarzeń, które generuje. Jeśli klasa wywołuje zdarzenie, że zdarzenie jest zgłaszane w każdej klasy, który został wybrany do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie użyto również formularza (`Form1`) za pomocą przycisku (`Button1`) i pole tekstowe (`TextBox1`). Po kliknięciu przycisku, pierwszego pola tekstowego wyświetla odliczania od 10 do 0 sekund. Po upływie pełnoetatowi (10 sekund), pierwszego pola tekstowego wyświetla "Gotowe".  
  
 Kod `Form1` określa stany początkowych i końcowych formularza. Zawiera on również kod wykonywany, gdy zdarzenia są wywoływane.  
  
 Aby wykorzystać ten przykład, otwórz nowy projekt Windows Forms. Następnie dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` w formularzu głównym o nazwie `Form1`. Następnie kliknij prawym przyciskiem myszy formularz i kliknij przycisk **Wyświetl kod** można otworzyć edytora kodu.  
  
 Dodaj `WithEvents` zmiennej do sekcji deklaracji `Form1` klasy:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Dodaj następujący kod do kodu `Form1`. Zamień zduplikowane procedur, które mogą występować, takich jak `Form_Load` lub `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Naciśnij klawisz F5, aby uruchomić w poprzednim przykładzie, a następnie kliknij przycisk **Start**. Pierwsze pole tekstowe rozpoczyna odliczanie sekund. Po upływie pełnoetatowi (10 sekund), pierwszego pola tekstowego wyświetla "Gotowe".  
  
> [!NOTE]
>  `My.Application.DoEvents` Metoda nie może przetwarzać zdarzenia w taki sam sposób, w formularzu jest. Aby włączyć formularz do obsługi zdarzeń bezpośrednio, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
