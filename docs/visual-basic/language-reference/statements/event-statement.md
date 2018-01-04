---
title: "Event — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ba49d6582eb2ecac4846eaee570a4d92439a5d9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-statement"></a>Event — Instrukcja
Deklaruje zdarzeń zdefiniowanych przez użytkownika.  
  
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
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego zdarzenia. Wiele atrybutów są rozdzielane przecinkami. Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").|  
|`accessmodifier`|Opcjonalny. Określa, jaki kod można uzyskać dostępu do zdarzenia. Może to być jedna z następujących czynności:<br /><br /> -   [Publiczny](../../../visual-basic/language-reference/modifiers/public.md)— kodu, który można uzyskać dostępu do elementu, który deklaruje go do niego dostęp.<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)— tylko do kodu w klasie lub klasy pochodnej do niego dostęp.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— tylko do kodu w skład zestawu do niego dostęp.<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)— tylko kodu w elemencie, który deklaruje go do niego dostęp.<br /><br /> Można określić `Protected Friend` Aby włączyć dostęp z kodu w klasie zdarzenia, klasa pochodna lub tego samego zestawu.|  
|`Shared`|Opcjonalny. Określa, że to zdarzenie nie jest skojarzony z konkretnym wystąpieniem klasy lub struktury.|  
|`Shadows`|Opcjonalny. Wskazuje, że to zdarzenie programistyczny ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej. Można obserwować dowolny rodzaj elementu zadeklarowany z innego typu.<br /><br /> Element zasłonięty z są niedostępne w klasie pochodnej, któremu, z wyjątkiem z którym przesłaniania element jest niedostępny. Na przykład jeśli `Private` element zasłania element klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.|  
|`eventname`|Wymagany. Nazwa zdarzenia; następuje standardowej konwencji nazewnictwa zmiennej.|  
|`parameterlist`|Opcjonalny. Lista zmiennych lokalnych, które reprezentują parametry tego zdarzenia. Musisz ją ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`Implements`|Opcjonalny. Wskazuje, że to zdarzenie implementuje zdarzenia interfejsu.|  
|`implementslist`|Jeśli wymagane `Implements` podano. Lista `Sub` procedury implementowana. Wiele procedur są oddzielone przecinkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Każdy `implementedprocedure` ma następujące składni i części:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-Wymagane. Implementuje Nazwa interfejsu, że tej procedury zawierający klasy lub struktury.<br />-   `Definedname`-Wymagane. Za pomocą którego procedura została określona w nazwie `interface`. To nie musi być taka sama jak `name`, nazwa, która używa tej procedury do zaimplementowania zdefiniowanej procedury.|  
|`Custom`|Wymagany. Zdarzenia deklarowane jako `Custom` musi definiować niestandardowe `AddHandler`, `RemoveHandler`, i `RaiseEvent` metody dostępu.|  
|`delegatename`|Opcjonalny. Nazwa delegata, który określa podpis obsługi zdarzeń.|  
|`AddHandler`|Wymagany. Deklaruje `AddHandler` dostępu, który określa instrukcje do wykonania po dodaniu obsługi zdarzeń, albo jawnie za pomocą `AddHandler` instrukcji lub niejawnie, przy użyciu `Handles` klauzuli.|  
|`End AddHandler`|Wymagany. Kończy `AddHandler` bloku.|  
|`value`|Wymagany. Nazwa parametru.|  
|`RemoveHandler`|Wymagany. Deklaruje `RemoveHandler` dostępu, który określa instrukcje do wykonania, gdy program obsługi zdarzeń zostanie usunięty, za pomocą `RemoveHandler` instrukcji.|  
|`End RemoveHandler`|Wymagany. Kończy `RemoveHandler` bloku.|  
|`RaiseEvent`|Wymagany. Deklaruje `RaiseEvent` dostępu, który określa instrukcje do wykonania, gdy zdarzenie jest wywoływane przy użyciu `RaiseEvent` instrukcji. Zwykle to wywołuje lista delegatów obsługiwanego przez `AddHandler` i `RemoveHandler` metody dostępu.|  
|`End RaiseEvent`|Wymagany. Kończy `RaiseEvent` bloku.|  
|`delegatesignature`|Wymagany. Listy parametrów, który odpowiada parametrów wymaganych przez `delegatename` delegowanie. Musisz ją ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`statements`|Opcjonalny. Instrukcje zawierające organów `AddHandler`, `RemoveHandler`, i `RaiseEvent` metody.|  
|`End Event`|Wymagany. Kończy `Event` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Po zdarzeniu został zadeklarowany, użyj `RaiseEvent` instrukcji, aby wywołać zdarzenie. Typowych zdarzeń może być zadeklarowana i wywoływane, jak pokazano w poniższych fragmenty:  
  
 [!code-vb[VbVbalrEvents#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Argumenty zdarzenia można zadeklarować tak samo, jak argumenty procedur z następującymi wyjątkami: zdarzenia nie może posiadać nazwane argumenty, `ParamArray` argumentów lub `Optional` argumentów. Zdarzenia nie mają zwracanych wartości.  
  
 Obsługa zdarzenia, musisz skojarzyć go z procedury obsługi zdarzeń za pomocą `Handles` lub `AddHandler` instrukcji. Podpisy procedurę i zdarzenia muszą być zgodne. W celu obsługi zdarzenia udostępnionego, należy użyć `AddHandler` instrukcji.  
  
 Można użyć `Event` tylko na poziomie modułu. Oznacza to, że *kontekście deklaracji* zdarzenia musi być klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 W większości przypadków za pomocą składni pierwszy w składni sekcji tego tematu deklarowania zdarzenia. Jednak w niektórych scenariuszach wymagane, czy masz większą kontrolę nad zachowanie szczegółowe zdarzenia. Ostatni składni w części w tym temacie, który używa składni `Custom` — słowo kluczowe, zapewnia tego formantu, umożliwiając określenie niestandardowych zdarzeń. W przypadku niestandardowych określ dokładnie co występuje, gdy kod dodaje lub usuwa obsługi zdarzeń do lub z zdarzenia lub gdy kod wywołuje zdarzenie. Przykłady można znaleźć [porady: zadeklarować niestandardowych zdarzeń do oszczędzania pamięci](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) i [porady: zadeklarować niestandardowych zdarzeń do uniknięcia blokuje](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zdarzeń, aby liczba sekund od 10 do 0 w dół. Kod przedstawia niektóre zdarzenia związane z metod, właściwości oraz instrukcje. Dotyczy to również `RaiseEvent` instrukcji.  
  
 Źródło zdarzenia jest klasa, która wywołuje zdarzenie i metod, które przetwarzają zdarzenia obsługi zdarzeń. Źródło zdarzenia może mieć wielu obsług do zdarzeń, które generuje. Po klasie zgłasza zdarzenie, że zdarzenie jest wywoływane dla każdej klasy, który został wybrany do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie użyto również formularza (`Form1`) z przyciskiem (`Button1`) i pola tekstowego (`TextBox1`). Po kliknięciu przycisku pierwsze pole tekstowe wyświetla odliczania od 10 do 0 sekund. Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".  
  
 Kod `Form1` określa stany początkowych i końcowych formularza. Zawiera również kod wykonywany w momencie pojawienia się zdarzenia.  
  
 Aby użyć tego przykładu, otwórz nowy projekt formularzy systemu Windows. Następnie dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1`. Następnie kliknij prawym przyciskiem myszy formularz i kliknij przycisk **kod widoku** można otworzyć edytora kodu.  
  
 Dodaj `WithEvents` zmienną do sekcji deklaracji `Form1` klasy:  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Dodaj następujący kod do kodu `Form1`. Zamień wszystkie zduplikowane procedur, które mogą istnieć, takich jak `Form_Load` lub `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedni przykład, a następnie kliknij przycisk **Start**. Pierwsze pole tekstowe rozpoczyna odliczanie sekund. Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".  
  
> [!NOTE]
>  `My.Application.DoEvents` — Metoda nie przetwarza zdarzenia w taki sam sposób jest formularz. Aby włączyć formularza, aby obsługiwać zdarzenia bezpośrednio, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [wątki](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Uchwyty](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)  
 [Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
