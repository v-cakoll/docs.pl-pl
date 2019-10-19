---
title: Event — Instrukcja (Visual Basic)
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
ms.openlocfilehash: ab4ff31cbc7b16e1d0ad8defed18e523c237e10d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583368"
---
# <a name="event-statement"></a>Event — Instrukcja
Deklaruje zdarzenie zdefiniowane przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
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
  
|Części|Opis|  
|---|---|  
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego zdarzenia. Wiele atrybutów jest oddzielonych przecinkami. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre ("`<`" i "`>`").|  
|`accessmodifier`|Opcjonalny. Określa kod, który może uzyskać dostęp do zdarzenia. Może być jedną z następujących czynności:<br /><br /> -   [publiczny](../../../visual-basic/language-reference/modifiers/public.md)— każdy kod, który może uzyskać dostęp do elementu, który deklaruje go, może uzyskać do niego dostęp.<br />-   [chroniony](../../../visual-basic/language-reference/modifiers/protected.md)— tylko kod wewnątrz swojej klasy lub klasy pochodnej mogą uzyskać do niej dostęp.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— tylko kod w tym samym zestawie może uzyskać do niego dostęp.<br />-   [prywatny](../../../visual-basic/language-reference/modifiers/private.md)— tylko kod w elemencie, który deklaruje, może uzyskać do niego dostęp.<br /> -   [chronionego tylko zaprzyjaźnionego](../../language-reference/modifiers/protected-friend.md)kodu w klasie zdarzenia, klasie pochodnej lub tego samego zestawu mogą uzyskać do niego dostęp. <br />- [prywatny](../../language-reference/modifiers/private-protected.md)kod tylko do odczytu w klasie zdarzenia lub Klasa pochodna w tym samym zestawie może uzyskać do niej dostęp.|  
|`Shared`|Opcjonalny. Określa, że to zdarzenie nie jest skojarzone z określonym wystąpieniem klasy lub struktury.|  
|`Shadows`|Opcjonalny. Wskazuje, że to zdarzenie ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.<br /><br /> Element w tle jest niedostępny z klasy pochodnej, która go zasłania, z wyjątkiem tego, że element shadowing jest niedostępny. Na przykład, jeśli element `Private` zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do elementu `Private`, zamiast tego uzyskuje dostęp do elementu klasy bazowej.|  
|`eventname`|Wymagany. Nazwa zdarzenia; obowiązują standardowe konwencje nazewnictwa zmiennych.|  
|`parameterlist`|Opcjonalny. Lista zmiennych lokalnych, które reprezentują parametry tego zdarzenia. Należy ująć [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`Implements`|Opcjonalny. Wskazuje, że to zdarzenie implementuje zdarzenie interfejsu.|  
|`implementslist`|Wymagane, jeśli podano `Implements`. Lista implementowanych procedur `Sub`. Wiele procedur jest oddzielonych przecinkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Każda `implementedprocedure` ma następującą składnię i części:<br /><br /> `interface`. `definedname`<br /><br /> -    `interface` — wymagane. Nazwa interfejsu, który jest implementowany przez tę procedurę zawierającą klasę lub strukturę.<br />-    `Definedname` — wymagane. Nazwa, przez którą procedura jest definiowana w `interface`. Nie musi to być taka sama jak `name`, nazwa używana przez tę procedurę w celu zaimplementowania zdefiniowanej procedury.|  
|`Custom`|Wymagany. Zdarzenia zadeklarowane jako `Custom` muszą definiować niestandardowe metody dostępu `AddHandler`, `RemoveHandler` i `RaiseEvent`.|  
|`delegatename`|Opcjonalny. Nazwa delegata, który określa sygnaturę procedury obsługi zdarzeń.|  
|`AddHandler`|Wymagany. Deklaruje metodę dostępu `AddHandler`, która określa instrukcje do wykonania po dodaniu programu obsługi zdarzeń, jawnie za pomocą instrukcji `AddHandler` lub niejawnie za pomocą klauzuli `Handles`.|  
|`End AddHandler`|Wymagany. Kończy blok `AddHandler`.|  
|`value`|Wymagany. Nazwa parametru.|  
|`RemoveHandler`|Wymagany. Deklaruje metodę dostępu `RemoveHandler`, która określa instrukcje do wykonania po usunięciu programu obsługi zdarzeń przy użyciu instrukcji `RemoveHandler`.|  
|`End RemoveHandler`|Wymagany. Kończy blok `RemoveHandler`.|  
|`RaiseEvent`|Wymagany. Deklaruje metodę dostępu `RaiseEvent`, która określa instrukcje do wykonania, gdy zdarzenie jest zgłaszane przy użyciu instrukcji `RaiseEvent`. Zwykle powoduje to wywołanie listy delegatów obsługiwanych przez `AddHandler` i `RemoveHandler` metod dostępu.|  
|`End RaiseEvent`|Wymagany. Kończy blok `RaiseEvent`.|  
|`delegatesignature`|Wymagany. Lista parametrów, które pasują do parametrów wymaganych przez delegata `delegatename`. Należy ująć [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`statements`|Opcjonalny. Instrukcje zawierające treści metod `AddHandler`, `RemoveHandler` i `RaiseEvent`.|  
|`End Event`|Wymagany. Kończy blok `Event`.|  
  
## <a name="remarks"></a>Uwagi  
 Po zadeklarowaniu zdarzenia Użyj instrukcji `RaiseEvent`, aby zgłosić zdarzenie. Typowe zdarzenie może zostać zadeklarowane i zgłoszone, jak pokazano w następujących fragmentach:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: zdarzenia nie mogą mieć nazwanych argumentów, argumentów `ParamArray` lub argumentów `Optional`. Zdarzenia nie mają zwracanych wartości.  
  
 Aby obsłużyć zdarzenie, należy je skojarzyć z podprocedurą obsługi zdarzeń przy użyciu instrukcji `Handles` lub `AddHandler`. Sygnatury podprocedury i zdarzenia muszą być zgodne. Aby obsłużyć zdarzenie udostępnione, należy użyć instrukcji `AddHandler`.  
  
 @No__t_0 można używać tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* dla zdarzenia musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 W większości przypadków można użyć pierwszej składni w sekcji Składnia tego tematu do deklarowania zdarzeń. Jednak niektóre scenariusze wymagają większej kontroli nad szczegółowym zachowaniem zdarzenia. Ostatnia składnia w sekcji składnia w tym temacie, która używa słowa kluczowego `Custom`, zapewnia tę kontrolkę, umożliwiając zdefiniowanie zdarzeń niestandardowych. W niestandardowym zdarzeniu należy określić dokładnie to, co się dzieje, gdy kod dodaje lub usuwa procedurę obsługi zdarzeń do lub ze zdarzenia lub gdy kod wywołuje zdarzenie. Aby zapoznać się z przykładami, zobacz [How to: DECLARE Custom Events by zaoszczędzić pamięć](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) i [instrukcje: deklarowanie zdarzeń niestandardowych w celu uniknięcia blokowania](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zdarzeń do zliczenia w dół sekund od 10 do 0. Kod ilustruje kilka metod, właściwości i instrukcji związanych z zdarzeniami. Obejmuje to instrukcję `RaiseEvent`.  
  
 Klasa, która wywołuje zdarzenie, jest źródłem zdarzenia, a metody, które przetwarzają zdarzenie, są procedurami obsługi zdarzeń. Źródło zdarzenia może mieć wiele programów obsługi dla generowanych zdarzeń. Gdy Klasa zgłasza zdarzenie, to zdarzenie jest zgłaszane dla każdej klasy, która została wybrana do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie zastosowano również formularz (`Form1`) z przyciskiem (`Button1`) i polem tekstowym (`TextBox1`). Po kliknięciu przycisku, pierwsze pole tekstowe Wyświetla odliczanie od 10 do 0 sekund. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
 Kod dla `Form1` określa początkowe i końcowe Stany formularza. Zawiera również kod wykonywany, gdy zdarzenia są zgłaszane.  
  
 Aby użyć tego przykładu, Otwórz nowy projekt Windows Forms. Następnie Dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1`. Następnie kliknij prawym przyciskiem myszy formularz i kliknij polecenie **Wyświetl kod** , aby otworzyć Edytor kodu.  
  
 Dodaj zmienną `WithEvents` do sekcji deklaracji klasy `Form1`:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Dodaj następujący kod do kodu dla `Form1`. Zastąp wszystkie zduplikowane procedury, takie jak `Form_Load` lub `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedni przykład, a następnie kliknij przycisk zatytułowany **Uruchom**. Pierwsze pole tekstowe zaczyna przeliczać sekundy w dół. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
> [!NOTE]
> Metoda `My.Application.DoEvents` nie przetwarza zdarzeń w taki sam sposób, jak w przypadku formularza. Aby włączyć obsługę zdarzeń bezpośrednio w formularzu, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Realizuj](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
