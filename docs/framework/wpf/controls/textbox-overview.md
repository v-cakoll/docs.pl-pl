---
title: TextBox — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: bb03d09b1730f4a8d607773f9024eee4f125e2c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557774"
---
# <a name="textbox-overview"></a>TextBox — Przegląd
<xref:System.Windows.Controls.TextBox> Klasa umożliwia wyświetlanie lub edycji niesformatowanego tekstu. Typowym zastosowaniem <xref:System.Windows.Controls.TextBox> jest edycji niesformatowanego tekstu w formularzu. Na przykład formularz monitowania o nazwę użytkownika, numer telefonu etc użyje <xref:System.Windows.Controls.TextBox> kontrolki wprowadzania tekstu. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasy i przykłady dotyczące używania go w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> umożliwiają użytkownikom wprowadzanie tekstu, ale dwóch formantów są używane w różnych scenariuszach. A <xref:System.Windows.Controls.TextBox> wymaga mniej zasobów systemowych, a następnie <xref:System.Windows.Controls.RichTextBox> tak jest idealne rozwiązanie w razie konieczności można edytować tylko zwykły tekst (np. użycie w postaci). A <xref:System.Windows.Controls.RichTextBox> jest lepszym rozwiązaniem jest niezbędna dla użytkownika edytować tekst sformatowany, obrazy, tabel lub inne obsługiwane zawartości. Na przykład edytowanie dokumentu, artykuł lub blog, która wymaga formatowania, obrazy, itp. najlepiej odbywa się przy użyciu <xref:System.Windows.Controls.RichTextBox>. W poniższej tabeli przedstawiono podstawowe funkcje <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBox>.  
  
|Formant|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Formatowanie poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (ewidencyjne + B)|<xref:System.Windows.Documents.FlowDocument> zawartość, takich jak obrazy, akapitów, tabelach itp.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Tak|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak (zobacz [omówienie RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|Tak (zobacz [omówienie RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Controls.TextBox> ma obsługuje formatowanie edycji pokrewne polecenia takie jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> ewidencyjne + B, wiele podstawowych poleceń są obsługiwane przez oba formanty, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkcje obsługiwane przez <xref:System.Windows.Controls.TextBox> są przedstawione w poniższych sekcjach. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.RichTextBox>, zobacz [omówienie RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć w czasie rzeczywistym sprawdzanie pisowni w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>. Gdy sprawdzanie pisowni jest włączone, czerwoną linią pojawi się poniżej żadnych pisowni (patrz rysunek poniżej).  
  
 ![Pole tekstowe z pisowni&#45;sprawdzanie](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [włączyć sprawdzanie pisowni w formancie edycji tekstu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) Aby dowiedzieć się, jak włączyć sprawdzanie pisowni.  
  
### <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie oba <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> ma menu kontekstowego, który jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz formantu. Menu kontekstowe zezwala użytkownikowi na wycinanie, kopiowanie lub wklejanie (patrz rysunek poniżej).  
  
 ![Pole tekstowe z menu kontekstowego](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne menu kontekstowe niestandardowych zastąpienie zachowania domyślnego. Zobacz [Menu kontekstowe niestandardowych za pomocą pola tekstowego](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md) Aby uzyskać więcej informacji.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Tworzenie pól tekstowych  
 A <xref:System.Windows.Controls.TextBox> można pojedynczej linii w wysokości lub obejmuje wiele wierszy. Pojedynczy wiersz <xref:System.Windows.Controls.TextBox> jest najlepsze dla wprowadzanie za małej ilości zwykły tekst (tj.) "Name", "Numer telefonu" itp. w postaci). Poniższy przykład przedstawia sposób tworzenia pojedynczej linii <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Można również utworzyć <xref:System.Windows.Controls.TextBox> umożliwiająca użytkownikowi wprowadzenie wiele wierszy tekstu. Na przykład, jeśli formularza wyświetlony monit o podanie osobowe szkicu użytkownika, czy chcesz użyć <xref:System.Windows.Controls.TextBox> obsługujący wiele wierszy tekstu. Poniższy przykład przedstawia użycie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie zwiększa się odpowiednio wiele wierszy tekstu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu `Wrap` powoduje, że tekst, który ma być zawijany do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> osiągnięciu kontroli automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> formantu, aby w razie potrzeby Dołącz miejsca, aby utworzyć nowy wiersz.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu `true` powoduje, że nowy wiersz do wstawienia, gdy zostanie naciśnięty klawisz RETURN ponownie automatycznie rozszerzanie <xref:System.Windows.Controls.TextBox> uwzględnienie miejsce dla nowego wiersza, jeśli to konieczne.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybutu dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane Jeśli <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiaru ramki lub okna ograniczający go.  
  
 Aby uzyskać więcej informacji na temat różnych zadań związanych z użyciem <xref:System.Windows.Controls.TextBox>, zobacz [— tematy porad](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Wykryj, kiedy zmienia zawartości  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia mają być używane do wykrywania po każdej zmianie tekstu w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> zmiany, a następnie <xref:System.Windows.UIElement.KeyDown> zgodnie z oczekiwaniami może. Zobacz [wykryć gdy tekst w pole tekstowe został zmieniony](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
