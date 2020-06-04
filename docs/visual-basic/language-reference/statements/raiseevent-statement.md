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
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404294"
---
# <a name="raiseevent-statement"></a>RaiseEvent — Instrukcja
Wyzwala zdarzenie zadeklarowane na poziomie modułu w klasie, formularzu lub dokumencie.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Części  
 `eventname`  
 Wymagany. Nazwa zdarzenia do wyzwolenia.  
  
 `argumentlist`  
 Opcjonalny. Rozdzielana przecinkami lista zmiennych, tablic lub wyrażeń. `argumentlist`Argument musi być ujęty w nawiasy. Jeśli nie ma żadnych argumentów, nawiasy muszą być pominięte.  
  
## <a name="remarks"></a>Uwagi  
 Wymagana `eventname` jest nazwą zdarzenia zadeklarowanego w module. Następuje Visual Basic konwencji nazewnictwa zmiennych.  
  
 Jeśli zdarzenie nie zostało zadeklarowane w module, w którym jest wywoływany, wystąpi błąd. Poniższy fragment kodu ilustruje deklarację zdarzenia i procedurę, w której zdarzenie jest zgłaszane.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Nie można użyć `RaiseEvent` do wywołania zdarzeń, które nie są jawnie zadeklarowane w module. Na przykład wszystkie formularze dziedziczą <xref:System.Windows.Forms.Control.Click> zdarzenie z <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , ale nie mogą być zgłaszane przy użyciu `RaiseEvent` w formularzu pochodnym. Jeśli zadeklarujesz `Click` zdarzenie w module formularza, zasłania ono własne <xref:System.Windows.Forms.Control.Click> wydarzenie formularza. Nadal można wywołać <xref:System.Windows.Forms.Control.Click> zdarzenie formularza, wywołując <xref:System.Windows.Forms.Control.OnClick%2A> metodę.  
  
 Domyślnie zdarzenie zdefiniowane w Visual Basic wywołuje obsługę zdarzeń w kolejności, w jakiej są nawiązywane połączenia. Ponieważ zdarzenia mogą mieć `ByRef` Parametry, proces, który nawiązuje połączenie, może odbierać parametry, które zostały zmienione przez wcześniejszą procedurę obsługi zdarzeń. Po wykonaniu obsługi zdarzeń sterowanie jest zwracane do procedury podrzędnej, która wywołała zdarzenie.  
  
> [!NOTE]
> Nie można podwyższyć poziomu zdarzeń nieudostępnionych w konstruktorze klasy, w której są zadeklarowane. Chociaż takie zdarzenia nie powodują błędów w czasie wykonywania, mogą one nie zostać przechwycone przez skojarzone programy obsługi zdarzeń. Użyj `Shared` modyfikatora, aby utworzyć zdarzenie udostępnione, jeśli trzeba zgłosić zdarzenie z konstruktora.  
  
> [!NOTE]
> Domyślne zachowanie zdarzeń można zmienić przez zdefiniowanie niestandardowego zdarzenia. W przypadku zdarzeń niestandardowych `RaiseEvent` instrukcja wywołuje `RaiseEvent` metodę dostępu zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](event-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zdarzeń do zliczenia w dół sekund od 10 do 0. Kod ilustruje kilka metod, właściwości i instrukcji związanych ze zdarzeniami, w tym `RaiseEvent` instrukcji.  
  
 Klasa, która wywołuje zdarzenie, jest źródłem zdarzenia, a metody, które przetwarzają zdarzenie, są procedurami obsługi zdarzeń. Źródło zdarzenia może mieć wiele programów obsługi dla generowanych zdarzeń. Gdy Klasa zgłasza zdarzenie, to zdarzenie jest zgłaszane dla każdej klasy, która została wybrana do obsługi zdarzeń dla tego wystąpienia obiektu.  
  
 W przykładzie używa się również formularza ( `Form1` ) z przyciskiem ( `Button1` ) i polem tekstowym ( `TextBox1` ). Po kliknięciu przycisku, pierwsze pole tekstowe Wyświetla odliczanie od 10 do 0 sekund. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
 Kod `Form1` określający początkowe i końcowe Stany formularza. Zawiera również kod wykonywany, gdy zdarzenia są zgłaszane.  
  
 Aby użyć tego przykładu, Otwórz nowy projekt aplikacji systemu Windows, Dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1` . Następnie kliknij prawym przyciskiem myszy formularz i kliknij polecenie **Wyświetl kod** , aby otworzyć Edytor kodu.  
  
 Dodaj `WithEvents` zmienną do sekcji deklaracji `Form1` klasy.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Dodaj następujący kod do kodu dla `Form1` . Zastąp wszystkie zduplikowane procedury, takie jak `Form_Load` lub `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Naciśnij klawisz F5, aby uruchomić poprzedni przykład, a następnie kliknij przycisk zatytułowany **Uruchom**. Pierwsze pole tekstowe zaczyna przeliczać sekundy w dół. Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".  
  
> [!NOTE]
> `My.Application.DoEvents`Metoda nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza. Aby umożliwić bezpośrednie obsługiwanie zdarzeń przez formularz, można użyć wielowątkowości. Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../programming-guide/language-features/events/index.md)
- [Event — Instrukcja](event-statement.md)
- [AddHandler — Instrukcja](addhandler-statement.md)
- [RemoveHandler — Instrukcja](removehandler-statement.md)
- [Handles](handles-clause.md)
