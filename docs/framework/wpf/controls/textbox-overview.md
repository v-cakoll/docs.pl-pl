---
title: TextBox — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 577a12a0c04e5e3bfbfecb2c45263b684f0ffc17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791004"
---
# <a name="textbox-overview"></a>TextBox — Przegląd
<xref:System.Windows.Controls.TextBox> Klasy pozwala do wyświetlania lub edycji niesformatowanego tekstu. Typowym zastosowaniem <xref:System.Windows.Controls.TextBox> jest edycji niesformatowanego tekstu w formularzu. Na przykład formularz z prośbą o nazwę użytkownika, numer telefonu etc użyje <xref:System.Windows.Controls.TextBox> kontrolki wprowadzania tekstu. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasy i przykłady dotyczące używania go w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> Zezwalaj użytkownikom na wprowadzanie tekstu, ale dwie kontrolki są używane w różnych scenariuszach. A <xref:System.Windows.Controls.TextBox> wymaga mniej zasobów systemowych, a następnie <xref:System.Windows.Controls.RichTextBox> , dzięki czemu jest idealnym rozwiązaniem, gdy należy edytować tylko zwykły tekst (tzn. użycie w postaci). Element <xref:System.Windows.Controls.RichTextBox> jest lepszym rozwiązaniem, gdy jest to niezbędne do użytkownika o taką edycję tekstu sformatowanego, obrazy, tabele lub inne obsługiwane zawartości. Na przykład, edytowanie dokumentów, artykuł lub blogów, która wymaga formatowania, obrazy, itp. najlepiej odbywa się przy użyciu <xref:System.Windows.Controls.RichTextBox>. W poniższej tabeli podsumowano podstawowe funkcje <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBox>.  
  
|formant|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Formatowanie poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (kont. + B)|<xref:System.Windows.Documents.FlowDocument> zawartość, taką jak obrazy, akapitów, tabelach itp.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Yes|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak (zobacz [RichTextBox — Przegląd](richtextbox-overview.md))|Tak (zobacz [RichTextBox — Przegląd](richtextbox-overview.md))|  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Controls.TextBox> ma obsługują formatowanie pokrewne edytowania poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> kont. + B, wiele podstawowych poleceń są obsługiwane przez oba formanty, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkcje obsługiwane przez <xref:System.Windows.Controls.TextBox> znajdują się w poniższych sekcjach. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.RichTextBox>, zobacz [RichTextBox — Przegląd](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć w czasie rzeczywistym sprawdzanie pisowni w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>. Po jej włączeniu sprawdzanie pisowni czerwoną linią pojawia się pod dowolnego błędnie napisanych wyrazów (patrz rysunek poniżej).  
  
 ![Pole tekstowe z pisowni&#45;sprawdzanie](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [włączyć sprawdzanie pisowni w formancie edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md) dowiesz się, jak włączyć sprawdzanie pisowni.  
  
### <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie oba <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> ma menu kontekstowego, który jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz formantu. Menu kontekstowe zezwala użytkownikowi na wycinanie, kopiowanie lub wklejanie (patrz rysunek poniżej).  
  
 ![Pole tekstowe z menu kontekstowego](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne menu kontekstowego, aby zastąpić domyślne zachowanie. Zobacz [niestandardowego Menu kontekstowego za pomocą TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md) Aby uzyskać więcej informacji.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Tworzenie pól tekstowych  
 Element <xref:System.Windows.Controls.TextBox> można pojedynczej linii w wysokości lub obejmują wiele wierszy. Pojedynczy wiersz <xref:System.Windows.Controls.TextBox> sprawdza się najlepiej w wprowadzanie za małej ilości zwykły tekst (tj.) "Name", "Numer telefonu" itp. w formie). Poniższy przykład pokazuje, jak utworzyć pojedynczy wiersz <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Można również utworzyć <xref:System.Windows.Controls.TextBox> umożliwiająca użytkownikowi wprowadzenie wiele wierszy tekstu. Na przykład w razie formularz prośby o osobowe szkic użytkownika, czy chcesz użyć <xref:System.Windows.Controls.TextBox> , która obsługuje wiele wierszy tekstu. Poniższy przykład pokazuje, jak używać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.TextBox> formant, który automatycznie rozszerza się, aby uwzględnić wiele wierszy tekstu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu `Wrap` powoduje, że tekst do opakowania do nowego wiersza w przypadku krawędzi <xref:System.Windows.Controls.TextBox> sterowania zostanie osiągnięty, automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> formantu, aby uwzględnić miejsce dla nowego wiersza, jeśli to konieczne.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu `true` powoduje, że nowy wiersz do wstawienia po naciśnięciu klawisza RETURN, ponownie automatyczne rozszerzanie <xref:System.Windows.Controls.TextBox> obejmujący miejsca na znak nowego wiersza, jeśli to konieczne.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Atrybut dodaje pasek przewijania, aby <xref:System.Windows.Controls.TextBox>, tak aby zawartość <xref:System.Windows.Controls.TextBox> mogą być przewijane za pośrednictwem if <xref:System.Windows.Controls.TextBox> rozwija rozmiar ramki lub okna, która ją obejmuje.  
  
 Aby uzyskać więcej informacji na temat różnych zadań związanych z korzystaniem z <xref:System.Windows.Controls.TextBox>, zobacz [tematy porad](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Wykryj, kiedy zmiany zawartości  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzeń powinny być używane do wykrywania w każdym przypadku, gdy tekst w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> zmieni się, a następnie <xref:System.Windows.UIElement.KeyDown> zgodnie z oczekiwaniami. Zobacz [wykrycia podczas tekst w polu tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) przykład.  
  
## <a name="see-also"></a>Zobacz także

- [Tematy z instrukcjami](textbox-how-to-topics.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
