---
title: Działanie wprowadzania z klawiatury
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 4335798395a3b73dbcb2546a6fadac3d8efedb64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204747"
---
# <a name="how-keyboard-input-works"></a>Działanie wprowadzania z klawiatury
Formularze Windows przetwarza dane wejściowe z klawiatury, wywoływanie zdarzeń klawiatury w odpowiedzi na wiadomości Windows. Większość aplikacji Windows Forms przetwarzać dane wejściowe z klawiatury wyłącznie przez obsługi zdarzenia klawiatury. Jednak musisz zrozumieć, jak komunikaty klawiatury współdziałać, dzięki czemu można zaimplementować bardziej zaawansowane scenariusze wejście klawiatury, przechwytuje kluczy, zanim dotrą formantu. W tym temacie opisano typy danych klucza, formularze Windows rozpoznaje i omówiono sposób kierowania komunikaty klawiatury. Aby uzyskać informacji na temat zdarzeń klawiatury, zobacz [zdarzenia klawiatury przy użyciu](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy kluczy  
 Windows Forms identyfikuje dane wejściowe z klawiatury jako klawisza wirtualnego kody, które są reprezentowane przez operatora testu koniunkcji <xref:System.Windows.Forms.Keys> wyliczenia. Za pomocą <xref:System.Windows.Forms.Keys> wyliczania, można połączyć szereg po naciśnięciu klawiszy do wyniku w postaci pojedynczej wartości. Te wartości odpowiadają wartościom, dołączone do wiadomości przetłumaczyła i WM_SYSKEYDOWN Windows. Większości fizycznych naciśnięcia klawiszy może wykryć, obsługując <xref:System.Windows.Forms.Control.KeyDown> lub <xref:System.Windows.Forms.Control.KeyUp> zdarzenia. Klawisze stanowią podzestaw <xref:System.Windows.Forms.Keys> wyliczenie i odpowiadają wartościom, dołączone do wiadomości WM_CHAR i WM_SYSCHAR Windows. Jeśli kombinację po naciśnięciu klawiszy w wyniku znak, można wykryć znak obsługi <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Alternatywnie, można użyć <xref:Microsoft.VisualBasic.Devices.Keyboard>, uwidocznione przez interfejs programowania Visual Basic, odnajdywanie, których klucze zostały naciśnięte i Wyślij klucze. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do klawiatury](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Kolejność zdarzeń klawiatury  
 Zgodnie z wymienionymi wcześniej, istnieją 3 za pomocą klawiatury w powiązanych zdarzeń, które mogą wystąpić w kontrolce. Poniższa sekwencja zawiera kolejność zdarzeń:  
  
1.  Użytkownik umieszcza klucz "", klucz jest wstępnie przetworzony, wysyłane oraz <xref:System.Windows.Forms.Control.KeyDown> wystąpi zdarzenie.  
  
2.  Użytkownik utrzyma "" klucza, klucz jest wstępnie przetworzony, wysyłane oraz <xref:System.Windows.Forms.Control.KeyPress> wystąpi zdarzenie.  
  
     To zdarzenie występuje wiele razy, użytkownik posiada klucza.  
  
3.  Wersje użytkownika "" klucz jest wstępnie przetworzony, wysyłane i <xref:System.Windows.Forms.Control.KeyUp> wystąpi zdarzenie.  
  
## <a name="preprocessing-keys"></a>Klucze przetwarzania wstępnego  
 Podobnie jak inne komunikaty, komunikaty klawiatury są przetwarzane w <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub formantu. Jednak przed klawiatury komunikaty są przetwarzane, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda wywołuje co najmniej jednej metody, które może zostać zastąpiona w celu obsługi znaków specjalnych kluczy i kluczy fizycznych. Możesz przesłonić te metody, aby wykrywać i filtrowania określonych kluczy przed komunikaty są przetwarzane przez kontrolkę. W poniższej tabeli przedstawiono akcję, która jest wykonywana i powiązanej metody, która występuje, w kolejności, że metoda występuje.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Wstępne przetwarzanie zdarzenia KeyDown  
  
|Akcja|Powiązana metoda|Uwagi|  
|------------|--------------------|-----------|  
|Sprawdź, czy klucz polecenia, takie jak skrótu lub skrótu w menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Ta metoda przetwarza klucz polecenia, który ma pierwszeństwo przed regularne kluczy. Jeśli ta metoda zwraca `true`komunikat klucza nie są wysyłane i kluczy zdarzenie nie występuje. Jeśli zostanie zwrócona `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> nosi nazwę`.`|  
|Sprawdź specjalny klucz, który wymaga przetwarzania wstępnego lub klucz normalne znaki, które powinny wywoływać <xref:System.Windows.Forms.Control.KeyDown> zdarzeń i być wysyłane do formantu.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Jeśli metoda zwraca `true`, oznacza, że kontrolka jest zwykły znak i <xref:System.Windows.Forms.Control.KeyDown> zdarzenie jest wywoływane. Jeśli `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana. **Uwaga:**  W celu zapewnienia kontroli pobiera klawisz lub kombinację klawiszy, które ułatwią Ci obsługę <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i ustaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` klucza lub ma kluczy.|  
|Sprawdź, czy klucz nawigacji (klawisze ESC, TAB, Return lub Strzałka).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Ta metoda przetwarza fizycznych klucz, który wykorzystuje specjalne funkcje znajdujących się pod kontrolą, takich jak przełączanie fokus między formantem i jego obiektu nadrzędnego. Jeśli bezpośredniej kontroli nie obsługuje klucza, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana w kontrolce nadrzędnej i tak dalej, aby kontrolka najwyższego poziomu w hierarchii. Jeśli ta metoda zwraca `true`wstępne przetwarzanie zostało ukończone i nie jest generowane zdarzenie klucza. Jeśli zostanie zwrócona `false`, <xref:System.Windows.Forms.Control.KeyDown> wystąpi zdarzenie.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Wstępne przetwarzanie zdarzenia KeyPress  
  
|Akcja|Powiązana metoda|Uwagi|  
|------------|--------------------|-----------|  
|Sprawdź, że klucz jest normalne znaki, które mają być przetwarzane przez kontrolkę|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Jeśli znak jest normalne znaki, ta metoda zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> jest wywoływane zdarzenie i żadne dodatkowe przetwarzanie wstępne występuje. W przeciwnym razie <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zostanie wywołana.|  
|Zaznacz, aby sprawdzić, czy znak jest skrót klawiszowy (takich jak & OK na przycisku)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Ta metoda jest podobna do <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, zostanie wywołana w hierarchii kontroli. Jeśli jest to kontrolka kontenera, sprawdza mnemonik przez wywołanie metody <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> na siebie i swoich formantów podrzędnych. Jeśli <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie nie występuje.|  
  
## <a name="processing-keyboard-messages"></a>Przetwarzanie komunikatów klawiatury  
 Po klawiatury komunikaty zasięg <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub formantu, są przetwarzane przez zestaw metod, które mogą zostać zastąpione. Każda z tych metod zwraca <xref:System.Boolean> wartość określającą, czy został przetworzony i używane przez formant komunikatu z klawiatury. Jeśli jednej z metod zwraca `true`, następnie wiadomości jest uznawany za obsługiwany i nie jest przekazywany do podstawowej lub nadrzędnego formantu do dalszego przetwarzania. W przeciwnym razie komunikat pozostaje w kolejce komunikatów i mogą być przetwarzane w innej metody w podstawowej formantu lub jego element nadrzędny. W poniższej tabeli przedstawiono metody, które przetwarzają komunikaty klawiatury.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Ta metoda przetwarza komunikaty klawiatury, które są odbierane przez <xref:System.Windows.Forms.Control.WndProc%2A> metoda formantu.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Ta metoda wysyła komunikatu z klawiatury do kontrolki nadrzędnej. Jeśli <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> zwraca `true`, nie klucza jest generowane zdarzenie, w przeciwnym razie <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> jest wywoływana.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Ta metoda wywołuje <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia, zgodnie z potrzebami.|  
  
## <a name="overriding-keyboard-methods"></a>Zastępowanie metody klawiatury  
 Istnieje wiele metod zastępowanie gdy komunikatu z klawiatury zostanie wstępnie przetworzony i przetwarzania; Jednak niektóre metody są znacznie lepsze możliwości niż inne. Poniższej tabeli przedstawiono zadania, które można wykonać i najlepszy sposób Przesłaniaj metody klawiatury. Aby uzyskać więcej informacji na temat nadpisywania metod, zobacz [zastępowanie właściwości i metod w klasach pochodnych](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Zadanie|Metoda|  
|----------|------------|  
|Przechwytywać klucz nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyDown> zdarzeń. Na przykład chcesz kartę i wróć do obsłużenia w polu tekstowym.|Zastąp <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Uwaga:**  Alternatywnie, można obsługiwać <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i ustaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` klucza lub kluczy ma.|  
|W kontrolce, należy wykonać specjalne obsługi danych wejściowych lub nawigacji. Na przykład chcesz użycie klawiszy strzałek w kontrolce listy można zmienić wybranego elementu.|Zastąpienie <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Przechwytywać klucz nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Na przykład w kontrolce pola pokrętła potrzebujesz wielu Strzałka musi nacisnąć, aby przyspieszyć przez kolejne elementy.|Zastąp <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Wykonywać specjalne obsługi danych wejściowych lub nawigacji podczas <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Na przykład na liście kontroli, przytrzymując naciśnięty klawisz "r" pomija między elementami, które zaczynają się od litery r.|Zastąpienie <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Wykonaj niestandardowy skrót klawiszowy obsługi; na przykład chcesz obsługiwać symboli na przyciskach rysowanych przez właściciela, znajdujących się na pasku narzędzi.|Zastąp <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard — Obiekt](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Uzyskiwanie dostępu do klawiatury](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Używanie zdarzeń klawiatury](using-keyboard-events.md)
