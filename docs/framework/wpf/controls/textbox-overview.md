---
title: TextBox — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186640"
---
# <a name="textbox-overview"></a>TextBox — Przegląd
Klasa <xref:System.Windows.Controls.TextBox> umożliwia wyświetlanie lub edytowanie niesformatowanego tekstu. Typowym zastosowaniem <xref:System.Windows.Controls.TextBox> a jest edytowanie niesformatowanego tekstu w formularzu. Na przykład formularz z prośbą o nazwę użytkownika, numer <xref:System.Windows.Controls.TextBox> telefonu itp. W tym temacie <xref:System.Windows.Controls.TextBox> przedstawiono klasę i zawiera przykłady, jak go używać w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> i umożliwić użytkownikom wprowadzania tekstu, ale dwa formanty są używane dla różnych scenariuszy. A <xref:System.Windows.Controls.TextBox> wymaga mniej zasobów <xref:System.Windows.Controls.RichTextBox> systemowych, a następnie tak jest idealny, gdy tylko zwykły tekst musi być edytowany (tj. użycie w formularzu). A <xref:System.Windows.Controls.RichTextBox> jest lepszym wyborem, gdy użytkownik musi edytować sformatowany tekst, obrazy, tabele lub inną obsługiwaną zawartość. Na przykład edytowanie dokumentu, artykułu lub bloga, który wymaga formatowania, <xref:System.Windows.Controls.RichTextBox>obrazów itp., najlepiej jest wykonać za pomocą pliku . Poniższa tabela zawiera podsumowanie <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>podstawowych cech i .  
  
|Kontrola|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Polecenia formatowania, <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> takie jak (Ctr+B)|<xref:System.Windows.Documents.FlowDocument>treści, takich jak obrazy, akapity, tabele itp.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Tak|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak (zobacz [Przegląd RichTextBox)](richtextbox-overview.md)|Tak (zobacz [Przegląd RichTextBox)](richtextbox-overview.md)|  
  
> [!NOTE]
> Chociaż <xref:System.Windows.Controls.TextBox> nie obsługuje formatowania powiązanych <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> poleceń edycji, takich jak (Ctr + B), wiele podstawowych poleceń są obsługiwane przez oba formanty, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkcje obsługiwane <xref:System.Windows.Controls.TextBox> przez są omówione w poniższych sekcjach. Aby uzyskać <xref:System.Windows.Controls.RichTextBox>więcej informacji na temat , zobacz [Omówienie RichTextBox](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Sprawdzanie pisowni w czasie rzeczywistym można <xref:System.Windows.Controls.TextBox> włączyć <xref:System.Windows.Controls.RichTextBox>w pliku . Gdy sprawdzanie pisowni jest włączone, pod błędnie napisanymi słowami pojawia się czerwona linia (patrz rysunek poniżej).  
  
 ![Pole tekstowe z sprawdzaniem&#45;pisowni](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [Włączanie sprawdzania pisowni w formancie edycji tekstu,](how-to-enable-spell-checking-in-a-text-editing-control.md) aby dowiedzieć się, jak włączyć sprawdzanie pisowni.  
  
### <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie oba <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> i mają menu kontekstowe, które pojawia się, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz formantu. Menu kontekstowe umożliwia użytkownikowi wycinanie, kopiowanie lub wklejenie (patrz rysunek poniżej).  
  
 ![TextBox z menu kontekstowym](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Można utworzyć własne niestandardowe menu kontekstowe, aby zastąpić zachowanie domyślne. Aby uzyskać więcej [informacji, zobacz Używanie niestandardowego menu kontekstowego z polem tekstowym.](how-to-use-a-custom-context-menu-with-a-textbox.md)  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Tworzenie skrzynek tekstowych  
 A <xref:System.Windows.Controls.TextBox> może być pojedynczą linią wysokości lub obejmować wiele linii. Pojedynczy wiersz <xref:System.Windows.Controls.TextBox> najlepiej jest wprowadzić niewielkie ilości zwykłego tekstu (tj. "Nazwa", "Numer telefonu" itp. W poniższym przykładzie pokazano, <xref:System.Windows.Controls.TextBox>jak utworzyć pojedynczy wiersz .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Można również <xref:System.Windows.Controls.TextBox> utworzyć, który umożliwia użytkownikowi wprowadzenie wielu wierszy tekstu. Na przykład, jeśli formularz poprosił o szkic biograficzny użytkownika, należy <xref:System.Windows.Controls.TextBox> użyć, który obsługuje wiele wierszy tekstu. W poniższym przykładzie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pokazano, <xref:System.Windows.Controls.TextBox> jak użyć do zdefiniowania formantu, który automatycznie rozwija się w celu uwzględnienia wielu wierszy tekstu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu `Wrap` powoduje, że tekst jest zawijany <xref:System.Windows.Controls.TextBox> do nowego wiersza po <xref:System.Windows.Controls.TextBox> osiągnięciu krawędzi formantu, automatycznie rozszerzając formant, aby uwzględnić miejsce dla nowego wiersza, jeśli to konieczne.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu `true` powoduje, że nowy wiersz ma zostać wstawiony po naciśnięciu <xref:System.Windows.Controls.TextBox> klawisza RETURN, po raz kolejny automatycznie rozszerzając o miejsce na nowy wiersz, jeśli to konieczne.  
  
 Atrybut <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> dodaje pasek przewijania <xref:System.Windows.Controls.TextBox>do , tak, <xref:System.Windows.Controls.TextBox> aby zawartość można przewijać, jeśli <xref:System.Windows.Controls.TextBox> rozwija się poza rozmiar ramki lub okna, które go otacza.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.TextBox>różnych zadań skojarzonych z użyciem programu , zobacz [Tematy insyceny](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Wykrywanie, kiedy zawartość się zmienia  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenie powinno być używane do wykrywania, <xref:System.Windows.Controls.RichTextBox> gdy tekst <xref:System.Windows.UIElement.KeyDown> w <xref:System.Windows.Controls.TextBox> lub zmienia się, a następnie, jak można się spodziewać. Zobacz [Wykrywanie, gdy tekst w pole tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) na przykład.  
  
## <a name="see-also"></a>Zobacz też

- [Tematy in jakże](textbox-how-to-topics.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
