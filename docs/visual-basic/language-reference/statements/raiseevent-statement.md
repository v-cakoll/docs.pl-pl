---
title: RaiseEvent — Instrukcja
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
ms.openlocfilehash: 19949fbdb1c1c54556876323d839b16fc01608f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="raiseevent-statement"></a>RaiseEvent — Instrukcja
Wyzwala zdarzenie zadeklarowane na poziomie modułu w obrębie klasy, formularza lub dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Części  
 `eventname`  
 Wymagana. Nazwa zdarzenia do wyzwalania.  
  
 `argumentlist`  
 Opcjonalna. Rozdzielana przecinkami lista zmiennych, tablic lub wyrażenia. `argumentlist` Argument musi być ujęta w nawiasy. Jeśli nie ma żadnych argumentów, należy pominąć nawiasów.  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `eventname` zadeklarowano nazwę zdarzenia w module. Wynika z konwencji nazewnictwa zmiennej języka Visual Basic.  
  
 Jeśli zdarzenie nie został zadeklarowany w module, w którym jest uruchamiany, wystąpi błąd. Poniższy fragment kodu przedstawia deklaracji zdarzenia i procedury, w którym zdarzenia.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Nie można użyć `RaiseEvent` wywołania zdarzeń, które nie są jawnie zadeklarowany w module. Na przykład wszystkich formularzy dziedziczą <xref:System.Windows.Forms.Control.Click> zdarzenia z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nie można zwiększyć za pomocą `RaiseEvent` w postaci pochodnych. W przypadku `Click` zdarzenia w module formularza go zasłania własnych formularza <xref:System.Windows.Forms.Control.Click> zdarzeń. Nadal można wywołać formularza <xref:System.Windows.Forms.Control.Click> zdarzenia przez wywołanie metody <xref:System.Windows.Forms.Control.OnClick%2A> metody.  
  
 Domyślnie zdarzenia zdefiniowany w języku Visual Basic zgłasza jego programy obsługi zdarzeń w kolejności ustanowienie połączenia. Ponieważ zdarzenia może mieć `ByRef` parametrów procesu, który łączy z opóźnieniem może pojawić się parametry, które zostały zmienione przez wcześniejszą obsługę zdarzeń. Po wykonywania programów obsługi zdarzeń, zwróceniem sterowania do procedury, która wywołała zdarzenie.  
  
> [!NOTE]
>  Nieudostępnieni zdarzenia nie powinien być wywoływany w konstruktorze klasy, w którym jest zadeklarowany. Chociaż takie zdarzenia nie powodują błędy środowiska wykonawczego, może nie powieść pod skojarzonej obsługi zdarzeń. Użyj `Shared` modyfikator, aby utworzyć udostępniony zdarzenie, chcąc wywołaj zdarzenie z konstruktora.  
  
> [!NOTE]
>  Domyślne zachowanie zdarzenia można zmienić, definiując zdarzenie niestandardowe. W przypadku niestandardowych zdarzeń `RaiseEvent` instrukcja wywołuje zdarzenie `RaiseEvent` metody dostępu. Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zdarzeń, aby liczba sekund od 10 do 0 w dół. Kod przedstawia niektóre zdarzenia związane z metod, właściwości oraz instrukcje, w tym `RaiseEvent` instrukcji.  
  
 Źródło zdarzenia jest klasa, która wywołuje zdarzenie i metod, które przetwarzają zdarzenia obsługi zdarzeń. Źródło zdarzenia może mieć wielu obsług do zdarzeń, które generuje. Po klasie zgłasza zdarzenie, że zdarzenie jest wywoływane dla każdej klasy, który został wybrany do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie użyto również formularza (`Form1`) z przyciskiem (`Button1`) i pola tekstowego (`TextBox1`). Po kliknięciu przycisku pierwsze pole tekstowe wyświetla odliczania od 10 do 0 sekund. Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".  
  
 Kod `Form1` określa stany początkowych i końcowych formularza. Zawiera również kod wykonywany w momencie pojawienia się zdarzenia.  
  
 Aby użyć tego przykładu, otwórz nowy projekt aplikacji systemu Windows, Dodawanie przycisku o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1`. Następnie kliknij prawym przyciskiem myszy formularz i kliknij przycisk **kod widoku** można otworzyć edytora kodu.  
  
 Dodaj `WithEvents` zmienną do sekcji deklaracji `Form1` klasy.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 Dodaj następujący kod do kodu `Form1`. Zamień wszystkie zduplikowane procedur, które mogą istnieć, takich jak `Form_Load`, lub `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedni przykład i kliknij przycisk oznaczony **Start**. Pierwsze pole tekstowe rozpoczyna odliczanie sekund. Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".  
  
> [!NOTE]
>  `My.Application.DoEvents` — Metoda nie przetwarza zdarzenia w taki sam sposób jak w formularzu. Aby zezwolić na formularzu, aby obsługiwać zdarzenia bezpośrednio, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz [wątki](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Uchwyty](../../../visual-basic/language-reference/statements/handles-clause.md)
