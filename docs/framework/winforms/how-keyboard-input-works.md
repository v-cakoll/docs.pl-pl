---
title: "Działanie wprowadzania z klawiatury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f45d01da6f9a851a0e51f9d614e84a3fba91e4d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-keyboard-input-works"></a>Działanie wprowadzania z klawiatury
Formularze systemu Windows przetwarza wprowadzanie z klawiatury przez wywoływanie zdarzeń klawiatury w odpowiedzi na komunikaty systemu Windows. Większość aplikacji Windows Forms przetworzyć klawiatury wyłącznie przez obsługi zdarzenia klawiatury. Jednak należy zrozumieć, jak komunikaty klawiatury działają, można wdrożyć bardziej zaawansowanych scenariuszy wejście klawiatury, takie jak przechwytywaniu kluczy przed dotarciem formantu. W tym temacie opisano typy danych klucza, że program Windows Forms rozpoznaje i omówiono sposób kierowania komunikaty klawiatury. Aby uzyskać informacje o zdarzeniach klawiatury, zobacz [zdarzenia klawiatury przy użyciu](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy kluczy  
 Formularze systemu Windows identyfikuje klawiatury jako klucz wirtualny kody, które są reprezentowane przez operatora testu koniunkcji <xref:System.Windows.Forms.Keys> wyliczenia. Z <xref:System.Windows.Forms.Keys> wyliczenia, można połączyć serii naciśniętego kluczy w pojedynczej wartości. Te wartości odpowiada wartości dołączone do wiadomości WM_KEYDOWN i WM_SYSKEYDOWN systemu Windows. Obsługa, można wykrywać większości fizycznych naciśnięć klawiszy <xref:System.Windows.Forms.Control.KeyDown> lub <xref:System.Windows.Forms.Control.KeyUp> zdarzenia. Klawisze są podzbiorem <xref:System.Windows.Forms.Keys> wyliczenie i odpowiadają wartościom dołączone do wiadomości WM_CHAR i WM_SYSCHAR systemu Windows. Kombinacja klawiszy naciśniętego powoduje znak, można wykryć znak Obsługa <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Alternatywnie można użyć <xref:Microsoft.VisualBasic.Devices.Keyboard>, uwidocznione przez interfejs programowania Visual Basic, do odnajdywania, zostały naciśnięte klawisze i wysyłania kluczy. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do klawiatury](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Kolejność zdarzeń klawiatury  
 Jak wymienionymi wcześniej, istnieją 3 klawiatury zdarzenia powiązane, które mogą wystąpić w formancie. Poniższa sekwencja zawiera kolejność zdarzeń:  
  
1.  Użytkownik wypchnięcia "" klucza, klucz jest wstępnie przetworzony, wysyłane, a <xref:System.Windows.Forms.Control.KeyDown> zdarzenie.  
  
2.  Użytkownik ma klucz "", klucz jest wstępnie przetworzony, wysyłane, a <xref:System.Windows.Forms.Control.KeyPress> zdarzenie.  
  
     To zdarzenie występuje wiele razy, użytkownik posiada klucza.  
  
3.  Wersje użytkownika "" klucz jest wstępnie przetworzony, wysyłane i <xref:System.Windows.Forms.Control.KeyUp> zdarzenie.  
  
## <a name="preprocessing-keys"></a>Przetwarzanie wstępne kluczy  
 Podobnie jak inne komunikaty, komunikaty klawiatury są przetwarzane w <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub kontrolki. Jednak przed klawiatury wiadomości są przetwarzane, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda wywołuje jedną lub kilka metod, które może zostać zastąpiona w celu obsługi znaków specjalnych klucze i klucze fizycznych. Można zastąpić te metody wykrywania i filtrowania określonych kluczy przed komunikaty są przetwarzane przez formant. W poniższej tabeli przedstawiono akcję, która jest wykonywana i powiązanej metody, która występuje, w kolejności, że metoda występuje.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Przetwarzanie wstępne zdarzenia KeyDown  
  
|Akcja|Pokrewne — metoda|Uwagi|  
|------------|--------------------|-----------|  
|Sprawdź, czy klucz polecenia, takich jak akceleratora lub menu skrótów.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Ta metoda przetwarza klucz polecenia, który ma pierwszeństwo przed regularne kluczy. Jeśli ta metoda zwraca `true`, nie jest wysyłany komunikat klucza i klucza zdarzenie nie występuje. Jeśli zmienna zwraca `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> nosi nazwę`.`|  
|Sprawdź, czy specjalny klucz, który wymaga przetwarzania wstępnego lub należy wywołać klucz normalne znaki <xref:System.Windows.Forms.Control.KeyDown> zdarzeń i być wysyłane do formantu.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Jeśli metoda zwraca `true`, oznacza to zwykły znak jest formantu i <xref:System.Windows.Forms.Control.KeyDown> zdarzenia. Jeśli `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana. **Uwaga:** w celu zapewnienia formantu pobiera klucz lub kombinację klawiszy, może obsługiwać <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i zestaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` dla klucza lub kluczy ma.|  
|Sprawdź, czy klucz nawigacji (ESC, karta, Return lub klawiszy strzałek).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Ta metoda przetwarza fizycznych klucz, który wykorzystuje funkcje specjalne w formancie, takie jak przełączanie fokus między formantem a jego elementu nadrzędnego. Jeśli bezpośredniej kontroli nie obsługuje klucza, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana w kontrolce nadrzędnej i tak dalej do formantu najwyższego poziomu w hierarchii. Jeśli ta metoda zwraca `true`, przetwarzania wstępnego została zakończona i nie jest generowane zdarzenie klucza. Jeśli zmienna zwraca `false`, <xref:System.Windows.Forms.Control.KeyDown> zdarzenie.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Przetwarzanie wstępne zdarzenia KeyPress  
  
|Akcja|Pokrewne — metoda|Uwagi|  
|------------|--------------------|-----------|  
|Sprawdź, czy klucz jest normalne znaki, który ma zostać przetworzony przez formant|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Jeśli znak jest normalne znaki, ta metoda zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> zdarzenia i dalsze przetwarzanie wstępne występuje. W przeciwnym razie <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zostanie wywołana.|  
|Sprawdź, czy znak jest wartość (takich jak & OK na przycisku)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Ta metoda jest podobna do <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, zostanie wywołana w górę hierarchii formantu. Jeśli formant jest kontenerem, sprawdza klawiszy skrótu wywołując <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> na siebie i jej kontrolkach podrzędnych. Jeśli <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie nie występuje.|  
  
## <a name="processing-keyboard-messages"></a>Przetwarzanie komunikatów klawiatury  
 Po reach komunikaty klawiatury <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub kontrolki, są przetwarzane przez zestaw metod, które mogą zostać zastąpione. Każda z tych metod zwraca <xref:System.Boolean> wartość określającą, czy komunikat klawiatury zostały przetworzone i używane przez formant. Jeśli zwraca jedną z metod `true`, następnie wiadomość jest uznawany za obsługiwany, i nie zostanie przekazany do podstawowej formantu lub jego element nadrzędny dla dalszego przetwarzania. W przeciwnym razie wiadomość pozostaje w kolejce wiadomości i mogą być przetwarzane w innej metody w podstawowej lub nadrzędnej formantu. W poniższej tabeli przedstawiono metody, które przetwarzają komunikaty klawiatury.  
  
|Metoda|Uwagi|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Ta metoda przetwarza wszystkie komunikaty klawiatury, które są odbierane przez <xref:System.Windows.Forms.Control.WndProc%2A> metody formantu.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Ta metoda wysyła wiadomość klawiatury do kontrolki nadrzędnej. Jeśli <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> zwraca `true`, nie klucza zostanie wygenerowane zdarzenie, w przeciwnym razie <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> jest wywoływana.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Ta metoda zgłasza <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia, zależnie od potrzeb.|  
  
## <a name="overriding-keyboard-methods"></a>Zastępowanie metody klawiatury  
 Istnieje wiele metod zastępowanie, gdy wiadomość klawiatury jest wstępnie przetworzony i przetwarzania; Jednak niektóre metody są znacznie lepszą opcji od innych. Poniższa tabela zawiera zadania, które można wykonywać i najlepszy sposób, aby zastąpić metody klawiatury. Aby uzyskać więcej informacji na zastępowanie metod, zobacz [zastępowanie właściwości i metod w klasach pochodnych](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Zadanie|Metoda|  
|----------|------------|  
|Przechwytywać klucza nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyDown> zdarzeń. Na przykład chcesz kartę i wrócić do obsługi w polu tekstowym.|Zastąpienie <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Uwaga:** Alternatywnie można obsługiwać <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i zestaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` dla klucza lub kluczy ma.|  
|Wykonaj specjalne obsługi danych wejściowych lub nawigacji w formancie. Na przykład chcesz użycie klawiszy strzałek w formancie z listy, aby zmienić wybrany element.|Zastąpienie<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Przechwytywać klucza nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Na przykład w formancie pole pokrętła ma się, że wiele Strzałka musi nacisnąć, aby przyspieszyć przez kolejne elementy.|Zastąpienie <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Specjalne obsługi danych wejściowych lub nawigacji podczas wykonywania <xref:System.Windows.Forms.Control.KeyPress> zdarzeń. Na przykład na liście kontroli, przytrzymując klawisz "r" pomija między elementami, które zaczynają się od litery r.|Zastąpienie<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Wykonaj niestandardowy skrót klawiszowy Obsługa; na przykład chcesz obsługiwać symboli na przyciskach rysowanych przez właściciela zawarte w pasku narzędzi.|Zastąpienie <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [My.Computer.Keyboard — obiekt](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [Uzyskiwanie dostępu do klawiatury](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [Używanie zdarzeń klawiatury](../../../docs/framework/winforms/using-keyboard-events.md)
