---
title: Działanie wprowadzania z klawiatury
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 369c434f5443334ccb8b136ce50ff2d5db8ece01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963446"
---
# <a name="how-keyboard-input-works"></a>Działanie wprowadzania z klawiatury
Windows Forms przetwarza dane wejściowe z klawiatury przez wywoływanie zdarzeń klawiatury w odpowiedzi na komunikaty systemu Windows. Większość aplikacji Windows Forms przetwarza wprowadzanie klawiatury wyłącznie przez obsługę zdarzeń klawiatury. Należy jednak zrozumieć, jak działają komunikaty klawiatury, aby można było zaimplementować bardziej zaawansowane scenariusze wprowadzania klawiatury, takie jak przechwycenie kluczy przed osiągnięciem kontroli. W tym temacie opisano typy kluczowych danych, które Windows Forms rozpoznawane i zawiera omówienie sposobu, w jaki są kierowane komunikaty klawiatury. Aby uzyskać informacje na temat zdarzeń klawiatury, zobacz [Używanie zdarzeń klawiatury](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy kluczy  
 Windows Forms identyfikuje dane wejściowe z klawiatury jako kody kluczy wirtualnych, które są reprezentowane przez <xref:System.Windows.Forms.Keys> Wyliczenie bitowe. <xref:System.Windows.Forms.Keys> Z wyliczeniem można połączyć serię naciśniętych klawiszy, aby spowodować powstanie pojedynczej wartości. Te wartości odpowiadają wartościom, które towarzyszą PRZETŁUMACZYŁA i WM_SYSKEYDOWN komunikatów systemu Windows. Większość klawiszy fizycznych można wykryć, obsługując <xref:System.Windows.Forms.Control.KeyDown> zdarzenia lub. <xref:System.Windows.Forms.Control.KeyUp> Klucze znaków są podzbiorem <xref:System.Windows.Forms.Keys> wyliczenia i odpowiadają wartościom dołączonym do komunikatów systemu Windows WM_CHAR i WM_SYSCHAR. Jeśli kombinacja naciśniętych klawiszy spowoduje wykrycie znaku, można wykryć znak poprzez obsługę <xref:System.Windows.Forms.Control.KeyPress> zdarzenia. Alternatywnie można użyć <xref:Microsoft.VisualBasic.Devices.Keyboard>, uwidoczniony przez interfejs programowania Visual Basic, aby wykryć, które klucze zostały naciśnięte i wysyłać klucze. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do klawiatury](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Kolejność zdarzeń klawiatury  
 Jak wspomniano wcześniej, istnieją trzy zdarzenia związane z klawiaturą, które mogą wystąpić na formancie. Poniższa sekwencja przedstawia ogólną kolejność zdarzeń:  
  
1. Użytkownik wypycha klucz "a", klucz jest wstępnie przetworzony, wysłany i <xref:System.Windows.Forms.Control.KeyDown> występuje zdarzenie.  
  
2. Użytkownik przechowuje klucz "a", klucz jest wstępnie przetworzony, wysłany i <xref:System.Windows.Forms.Control.KeyPress> występuje zdarzenie.  
  
     To zdarzenie występuje wiele razy, gdy użytkownik przechowuje klucz.  
  
3. Użytkownik zwalnia klucz "a", jest wstępnie przetworzony, wysłany i <xref:System.Windows.Forms.Control.KeyUp> występuje zdarzenie.  
  
## <a name="preprocessing-keys"></a>Przetwarzanie wstępne kluczy  
 Podobnie jak w przypadku innych komunikatów, komunikaty klawiatury są <xref:System.Windows.Forms.Control.WndProc%2A> przetwarzane w metodzie formularza lub kontrolki. Jednak przed przetworzeniem <xref:System.Windows.Forms.Control.PreProcessMessage%2A> komunikatów klawiatury metoda wywołuje jedną lub więcej metod, które mogą zostać zastąpione w celu obsługi specjalnych kluczy znaków i kluczy fizycznych. Można zastąpić te metody, aby wykryć i odfiltrować niektóre klucze przed przetworzeniem komunikatów przez formant. W poniższej tabeli przedstawiono akcję, która jest wykonywana, oraz powiązaną metodę, która występuje w kolejności, w jakiej występuje metoda.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Przetwarzanie wstępne dla zdarzenia KeyDown  
  
|Akcja|Pokrewna Metoda|Uwagi|  
|------------|--------------------|-----------|  
|Sprawdź, czy nie ma klucza polecenia, takiego jak akcelerator lub skrót do menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Ta metoda przetwarza klucz polecenia, który ma pierwszeństwo przed kluczami regularnymi. Jeśli ta metoda zwróci `true`wartość, komunikat klucza nie jest wysyłany, a zdarzenie klucza nie wystąpi. Jeśli zwróci `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> jest wywoływana`.`|  
|Wyszukaj specjalny klucz wymagający przetwarzania wstępnego lub normalny klucz znaku, który powinien zgłosić <xref:System.Windows.Forms.Control.KeyDown> zdarzenie i zostać wysłany do kontrolki.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Jeśli metoda zwraca `true`, oznacza to, że kontrolka jest znakiem regularnym <xref:System.Windows.Forms.Control.KeyDown> , a zdarzenie jest zgłaszane. Jeśli `false` ,<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana. **Uwaga:**  Aby upewnić się, że kontrolka Pobiera klucz lub kombinację kluczy, można <xref:System.Windows.Forms.Control.PreviewKeyDown> obsłużyć <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> zdarzenie i <xref:System.Windows.Forms.PreviewKeyDownEventArgs> zestaw `true` do dla żądanych kluczy lub kluczy.|  
|Sprawdź klawisz nawigacyjny (ESC, TAB, Return lub strzałka).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Ta metoda przetwarza klucz fizyczny, który wykorzystuje specjalne funkcje w kontrolce, takie jak przełączanie fokusu między kontrolką a jego elementem nadrzędnym. Jeśli bezpośrednia kontrolka nie obsługuje klucza, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> obiekt jest wywoływany w kontrolce nadrzędnej i tak dalej, jak najwyższego poziomu w hierarchii. Jeśli ta metoda zwróci `true`metodę, przetwarzanie wstępne jest zakończone i nie jest generowane zdarzenie klucza. Jeśli zwróci `false` <xref:System.Windows.Forms.Control.KeyDown> , wystąpi zdarzenie.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Przetwarzanie wstępne dla zdarzenia KeyPress  
  
|Akcja|Pokrewna Metoda|Uwagi|  
|------------|--------------------|-----------|  
|Zaznacz, aby zobaczyć, że klucz jest normalnym znakiem, który powinien być przetworzony przez formant|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Jeśli znak jest zwykłym znakiem, ta metoda zwraca `true` <xref:System.Windows.Forms.Control.KeyPress> , zdarzenie jest zgłaszane i nie występuje dalsze przetwarzanie wstępne. W <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> przeciwnym razie zostanie wywołana.|  
|Sprawdź, czy znak jest metaznakiem (na przykład & OK na przycisku)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Ta metoda, podobna do <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, zostanie wywołana hierarchią formantów. Jeśli formant jest kontrolką kontenera, sprawdza obecność symboli przez wywołanie <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> samego siebie i jego formantów podrzędnych. Jeśli <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zwraca `true` ,<xref:System.Windows.Forms.Control.KeyPress> zdarzenie nie występuje.|  
  
## <a name="processing-keyboard-messages"></a>Przetwarzanie komunikatów klawiatury  
 Po osiągnięciu <xref:System.Windows.Forms.Control.WndProc%2A> przez komunikaty klawiatury metody formularza lub kontrolki są one przetwarzane przez zestaw metod, które mogą zostać zastąpione. Każda z tych metod zwraca <xref:System.Boolean> wartość określającą, czy komunikat klawiatury został przetworzony i zużyty przez formant. Jeśli jedna z metod zwraca `true`, komunikat jest uznawany za obsłużony i nie jest przenoszona do podstawowej lub nadrzędnej kontrolki do dalszej obróbki. W przeciwnym razie komunikat pozostaje w kolejce komunikatów i może być przetwarzany w innej metodzie w podstawowej lub nadrzędnej kontrolce. W poniższej tabeli przedstawiono metody przetwarzania komunikatów z klawiatury.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Ta metoda przetwarza wszystkie komunikaty klawiatury odbierane przez <xref:System.Windows.Forms.Control.WndProc%2A> metodę formantu.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Ta metoda wysyła komunikat z klawiatury do elementu nadrzędnego formantu. Jeśli <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> zwraca `true`wartość, żadne zdarzenie klucza nie jest generowane <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> , w przeciwnym razie jest wywoływana.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Ta metoda podnosi <xref:System.Windows.Forms.Control.KeyDown>odpowiednio zdarzenia <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp> .|  
  
## <a name="overriding-keyboard-methods"></a>Zastępowanie metod klawiatury  
 Istnieje wiele metod przesłaniania, gdy komunikat klawiatury jest wstępnie przetworzony i przetwarzany; Jednak niektóre metody są znacznie lepszym rozwiązaniem niż inne. W poniższej tabeli przedstawiono zadania, które można wykonać, i najlepszym sposobem przesłonięcia metod klawiatury. Aby uzyskać więcej informacji na temat zastępowania metod, zobacz [przesłanianie właściwości i metod w klasach pochodnych](../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Zadanie|Metoda|  
|----------|------------|  
|Przechwytuje klucz nawigacji i zgłasza <xref:System.Windows.Forms.Control.KeyDown> zdarzenie. Na przykład karta i Return mają być obsługiwane w polu tekstowym.|Zastąpienie <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Uwaga:**  Alternatywnie można obsłużyć <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzenie i <xref:System.Windows.Forms.PreviewKeyDownEventArgs> zestaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> do `true` dla żądanych kluczy lub kluczy.|  
|Wykonywanie specjalnych operacji wejścia lub nawigacji na formancie. Na przykład aby zmienić wybrany element, należy użyć klawiszy strzałek w kontrolce listy.|Mapowań<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Przechwytuje klucz nawigacji i zgłasza <xref:System.Windows.Forms.Control.KeyPress> zdarzenie. Na przykład w kontrolce pole pokrętła chcesz nacisnąć wiele klawiszy strzałek, aby przyspieszyć postęp przez elementy.|Zastąpienie <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Wykonywanie specjalnych operacji wejścia lub nawigacji podczas <xref:System.Windows.Forms.Control.KeyPress> zdarzenia. Na przykład w kontrolce listy trzymającej wciśnięty klawisz "r" pomija między elementami, które zaczynają się literą r.|Mapowań<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Wykonywanie obsługi niestandardowych symboli; na przykład, chcesz obsłużyć symboli na przyciskach rysowanych przez właściciela znajdujących się na pasku narzędzi.|Zastąpienie <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard, obiekt](../../visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Uzyskiwanie dostępu do klawiatury](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Używanie zdarzeń klawiatury](using-keyboard-events.md)
