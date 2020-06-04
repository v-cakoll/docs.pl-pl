---
title: Event — Instrukcja
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
ms.openlocfilehash: a136a517c7ce865b4e1d349270696e2704d61592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404670"
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
  
|Część|Opis|  
|---|---|  
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego zdarzenia. Wiele atrybutów jest oddzielonych przecinkami. Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").|  
|`accessmodifier`|Opcjonalny. Określa kod, który może uzyskać dostęp do zdarzenia. Może być jedną z następujących czynności:<br /><br /> -   [Publiczny](../modifiers/public.md)— każdy kod, który może uzyskać dostęp do elementu, który deklaruje go, może uzyskać do niego dostęp.<br />-   [Chroniony](../modifiers/protected.md)— dostęp do niego mają tylko kod wewnątrz klasy lub klasy pochodnej.<br />-   [Zaprzyjaźniony](../modifiers/friend.md)— tylko kod w tym samym zestawie może uzyskać do niego dostęp.<br />-   [Prywatny](../modifiers/private.md)— tylko kod w elemencie, który deklaruje, może uzyskać do niego dostęp.<br /> -   [Chroniony znajomo](../modifiers/protected-friend.md)kod w klasie zdarzenia, klasie pochodnej lub tym samym zestawie mogą uzyskać do niego dostęp. <br />- Tylko [prywatny chroniony](../modifiers/private-protected.md)kod w klasie zdarzenia lub klasy pochodnej w tym samym zestawie mogą uzyskać do niej dostęp.|  
|`Shared`|Opcjonalny. Określa, że to zdarzenie nie jest skojarzone z określonym wystąpieniem klasy lub struktury.|  
|`Shadows`|Opcjonalny. Wskazuje, że to zdarzenie ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.<br /><br /> Element w tle jest niedostępny z klasy pochodnej, która go zasłania, z wyjątkiem tego, że element shadowing jest niedostępny. Na przykład jeśli `Private` element zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do `Private` elementu, zamiast niego uzyskuje dostęp do elementu klasy bazowej.|  
|`eventname`|Wymagany. Nazwa zdarzenia; obowiązują standardowe konwencje nazewnictwa zmiennych.|  
|`parameterlist`|Opcjonalny. Lista zmiennych lokalnych, które reprezentują parametry tego zdarzenia. Należy ująć [listę parametrów](parameter-list.md) w nawiasach.|  
|`Implements`|Opcjonalny. Wskazuje, że to zdarzenie implementuje zdarzenie interfejsu.|  
|`implementslist`|Wymagane, jeśli `Implements` jest podany. Lista `Sub` implementowanych procedur. Wiele procedur jest oddzielonych przecinkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Każda `implementedprocedure` z nich ma następującą składnię i części:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`Potrzeb. Nazwa interfejsu, który jest implementowany przez tę procedurę zawierającą klasę lub strukturę.<br />-   `Definedname`Potrzeb. Nazwa, przez którą procedura jest zdefiniowana `interface` . Nie musi to być taka sama `name` , jak nazwa używana przez tę procedurę w celu zaimplementowania zdefiniowanej procedury.|  
|`Custom`|Wymagany. Zdarzenia zadeklarowane jako `Custom` muszą definiować metody `AddHandler` dostępu Custom, `RemoveHandler` i `RaiseEvent` .|  
|`delegatename`|Opcjonalny. Nazwa delegata, który określa sygnaturę procedury obsługi zdarzeń.|  
|`AddHandler`|Wymagany. Deklaruje `AddHandler` metodę dostępu, która określa instrukcje do wykonania po dodaniu programu obsługi zdarzeń, albo jawnie za pomocą `AddHandler` instrukcji lub niejawnie za pomocą `Handles` klauzuli.|  
|`End AddHandler`|Wymagany. Kończy `AddHandler` blok.|  
|`value`|Wymagany. Nazwa parametru.|  
|`RemoveHandler`|Wymagany. Deklaruje `RemoveHandler` metodę dostępu, która określa instrukcje do wykonania po usunięciu procedury obsługi zdarzeń przy użyciu `RemoveHandler` instrukcji.|  
|`End RemoveHandler`|Wymagany. Kończy `RemoveHandler` blok.|  
|`RaiseEvent`|Wymagany. Deklaruje `RaiseEvent` metodę dostępu, która określa instrukcje do wykonania, gdy zdarzenie jest zgłaszane przy użyciu `RaiseEvent` instrukcji. Zwykle powoduje to wywołanie listy delegatów obsługiwanych przez i metody `AddHandler` `RemoveHandler` dostępu.|  
|`End RaiseEvent`|Wymagany. Kończy `RaiseEvent` blok.|  
|`delegatesignature`|Wymagany. Lista parametrów, które pasują do parametrów wymaganych przez `delegatename` delegata. Należy ująć [listę parametrów](parameter-list.md) w nawiasach.|  
|`statements`|Opcjonalny. Instrukcje zawierające treści `AddHandler` `RemoveHandler` metod,, i `RaiseEvent` .|  
|`End Event`|Wymagany. Kończy `Event` blok.|  
  
## <a name="remarks"></a>Uwagi  
 Po zadeklarowaniu zdarzenia Użyj `RaiseEvent` instrukcji, aby zgłosić zdarzenie. Typowe zdarzenie może zostać zadeklarowane i zgłoszone, jak pokazano w następujących fragmentach:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: zdarzenia nie mogą mieć nazwanych argumentów, `ParamArray` argumentów lub `Optional` argumentów. Zdarzenia nie mają zwracanych wartości.  
  
 Aby obsłużyć zdarzenie, należy je skojarzyć z podprocedurą obsługi zdarzeń przy użyciu `Handles` instrukcji or `AddHandler` . Sygnatury podprocedury i zdarzenia muszą być zgodne. Aby obsłużyć zdarzenie udostępnione, należy użyć `AddHandler` instrukcji.  
  
 Można używać `Event` tylko na poziomie modułu. Oznacza to, że *kontekst deklaracji* dla zdarzenia musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 W większości przypadków można użyć pierwszej składni w sekcji Składnia tego tematu do deklarowania zdarzeń. Jednak niektóre scenariusze wymagają większej kontroli nad szczegółowym zachowaniem zdarzenia. Ostatnia składnia w sekcji Składnia tego tematu, która używa `Custom` słowa kluczowego, zapewnia tę kontrolkę, umożliwiając zdefiniowanie zdarzeń niestandardowych. W niestandardowym zdarzeniu należy określić dokładnie to, co się dzieje, gdy kod dodaje lub usuwa procedurę obsługi zdarzeń do lub ze zdarzenia lub gdy kod wywołuje zdarzenie. Aby zapoznać się z przykładami, zobacz [How to: DECLARE Custom Events by zaoszczędzić pamięć](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) i [instrukcje: deklarowanie zdarzeń niestandardowych w celu uniknięcia blokowania](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zdarzeń do zliczenia w dół sekund od 10 do 0. Kod ilustruje kilka metod, właściwości i instrukcji związanych z zdarzeniami. Obejmuje to `RaiseEvent` instrukcję.  
  
 Klasa, która wywołuje zdarzenie, jest źródłem zdarzenia, a metody, które przetwarzają zdarzenie, są procedurami obsługi zdarzeń. Źródło zdarzenia może mieć wiele programów obsługi dla generowanych zdarzeń. Gdy Klasa zgłasza zdarzenie, to zdarzenie jest zgłaszane dla każdej klasy, która została wybrana do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie używa się również formularza ( `Form1` ) z przyciskiem ( `Button1` ) i polem tekstowym ( `TextBox1` ). Po kliknięciu przycisku, pierwsze pole tekstowe Wyświetla odliczanie od 10 do 0 sekund. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
 Kod `Form1` określający początkowe i końcowe Stany formularza. Zawiera również kod wykonywany, gdy zdarzenia są zgłaszane.  
  
 Aby użyć tego przykładu, Otwórz nowy projekt Windows Forms. Następnie Dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1` . Następnie kliknij prawym przyciskiem myszy formularz i kliknij polecenie **Wyświetl kod** , aby otworzyć Edytor kodu.  
  
 Dodaj `WithEvents` zmienną do sekcji deklaracji `Form1` klasy:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Dodaj następujący kod do kodu dla `Form1` . Zastąp wszystkie zduplikowane procedury, takie jak `Form_Load` lub `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedni przykład, a następnie kliknij przycisk zatytułowany **Uruchom**. Pierwsze pole tekstowe zaczyna przeliczać sekundy w dół. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
> [!NOTE]
> `My.Application.DoEvents`Metoda nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza. Aby włączyć obsługę zdarzeń bezpośrednio w formularzu, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [RaiseEvent — Instrukcja](raiseevent-statement.md)
- [Implements — Instrukcja](implements-statement.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
- [AddHandler — Instrukcja](addhandler-statement.md)
- [RemoveHandler — Instrukcja](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Delegate — Instrukcja](delegate-statement.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../modifiers/shared.md)
- [Shadows](../modifiers/shadows.md)
