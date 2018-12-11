---
title: RaiseEvent — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ba4c05b3ef69d180f43ac3b90aa8fd6dee9c80fb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143301"
---
# <a name="raiseevent-statement"></a>RaiseEvent — Instrukcja
Wyzwala zdarzenie zadeklarowane na poziomie modułu w obrębie klasy, formularza lub dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Części  
 `eventname`  
 Wymagana. Nazwa zdarzenia w celu wyzwolenia.  
  
 `argumentlist`  
 Opcjonalna. Rozdzielana przecinkami lista zmiennych, tablic lub wyrażenia. `argumentlist` Argument musi być ujęta w nawiasy. Jeśli nie ma żadnych argumentów, nawiasy musi zostać pominięty.  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `eventname` jest zadeklarowany Nazwa zdarzenia w module. Jest zgodna z zmiennej konwencje nazewnictwa języka Visual Basic.  
  
 Jeśli nie została zadeklarowana zdarzenia w module, w którym jest uruchamiany, wystąpi błąd. Poniższy fragment kodu ilustruje deklaracji zdarzenia i procedury, w którym zdarzenie jest wywoływane.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Nie można użyć `RaiseEvent` aby wywołać zdarzenia, które nie są jawnie zadeklarowane w module. Na przykład dziedziczą wszystkie formularze <xref:System.Windows.Forms.Control.Click> zdarzenie z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nie może zostać wywołane, za pomocą `RaiseEvent` w postaci pochodnych. Jeśli zadeklarujesz `Click` zdarzenia w module formularza zasłania jego własnej formularza <xref:System.Windows.Forms.Control.Click> zdarzeń. Nadal można wywołać formularza <xref:System.Windows.Forms.Control.Click> zdarzeń przez wywołanie metody <xref:System.Windows.Forms.Control.OnClick%2A> metody.  
  
 Domyślnie zdarzenia, zdefiniowany w języku Visual Basic zgłasza swoich programów obsługi zdarzeń w kolejności, że nawiązywane są połączenia. Ponieważ zdarzenia może mieć `ByRef` parametrów procesu, który łączy z opóźnieniem może pojawić się parametry, które zostały zmienione przez wcześniejsze procedury obsługi zdarzeń. Po wykonaniu procedury obsługi zdarzeń, formant zostaje zwrócony do podprocedury, który spowodował zdarzenie.  
  
> [!NOTE]
>  Udostępnione innym zdarzenia nie powinien być wywoływany w ramach konstruktora klasy, w którym są one zgłoszone. Mimo że takie zdarzenia nie powodują błędy czasu wykonywania, ich może nie być przechwycony przez program obsługi skojarzone ze zdarzeniem. Użyj `Shared` modyfikator, aby utworzyć udostępniony zdarzenie, jeśli musisz wywołać zdarzenie z konstruktora.  
  
> [!NOTE]
>  Możesz zmienić domyślne zachowanie zdarzenia, definiując zdarzenia niestandardowego. W przypadku zdarzeń niestandardowych instrukcja `RaiseEvent` wywołuje metodę dostępu zdarzenia `RaiseEvent`. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zdarzeń odliczanie sekund od 10 do 0. Kod ilustruje kilka powiązanych zdarzeń do metod, właściwości i instrukcji, w tym `RaiseEvent` instrukcji.  
  
 Klasa, która wywołuje zdarzenie, jest źródłem zdarzeń i metody, które przetwarzają zdarzenia są procedury obsługi zdarzeń. Źródło zdarzenia może mieć wielu obsług do zdarzeń, które generuje. Jeśli klasa wywołuje zdarzenie, że zdarzenie jest zgłaszane w każdej klasy, który został wybrany do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie użyto również formularza (`Form1`) za pomocą przycisku (`Button1`) i pole tekstowe (`TextBox1`). Po kliknięciu przycisku, pierwszego pola tekstowego wyświetla odliczania od 10 do 0 sekund. Po upływie pełnoetatowi (10 sekund), pierwszego pola tekstowego wyświetla "Gotowe".  
  
 Kod `Form1` określa stany początkowych i końcowych formularza. Zawiera on również kod wykonywany, gdy zdarzenia są wywoływane.  
  
 Aby użyć tego przykładu, otwórz nowy projekt aplikacji Windows, Dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` w formularzu głównym o nazwie `Form1`. Następnie kliknij prawym przyciskiem myszy formularz i kliknij przycisk **Wyświetl kod** można otworzyć edytora kodu.  
  
 Dodaj `WithEvents` zmiennej do sekcji deklaracji `Form1` klasy.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 Dodaj następujący kod do kodu `Form1`. Zamień zduplikowane procedur, które mogą występować, takich jak `Form_Load`, lub `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedniego przykładu, a następnie kliknij przycisk **Start**. Pierwsze pole tekstowe rozpoczyna odliczanie sekund. Po upływie pełnoetatowi (10 sekund), pierwszego pola tekstowego wyświetla "Gotowe".  
  
> [!NOTE]
>  `My.Application.DoEvents` Metody nie przetwarza zdarzeń w taki sam sposób jak formularz. Aby zezwolić na formularzu do obsługi zdarzeń bezpośrednio, możesz użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
