---
title: TextBox — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 86b2cf8cb0c72186fd92bdad0af6bf5bd3fa9f3f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174435"
---
# <a name="textbox-overview"></a>TextBox — Przegląd
<xref:System.Windows.Controls.TextBox>Klasa umożliwia wyświetlanie lub edytowanie niesformatowanego tekstu. Typowym zastosowaniem <xref:System.Windows.Controls.TextBox> jest edytowanie niesformatowanego tekstu w formularzu. Na przykład formularz z prośbą o nazwę użytkownika, numer telefonu itp. użyje <xref:System.Windows.Controls.TextBox> kontrolek do wprowadzania tekstu. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasę i przedstawiono przykłady używania jej w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.TextBox> , jak i <xref:System.Windows.Controls.RichTextBox> umożliwiają użytkownikom wprowadzanie tekstu, ale dwie kontrolki są używane w różnych scenariuszach. <xref:System.Windows.Controls.TextBox>Program wymaga mniej zasobów systemowych, <xref:System.Windows.Controls.RichTextBox> dlatego jest idealnym rozwiązaniem, gdy wystarczy edytować tylko zwykły tekst (tj. użycie w formularzu). A <xref:System.Windows.Controls.RichTextBox> jest lepszym wyborem, gdy jest to konieczne, aby użytkownik mógł edytować sformatowany tekst, obrazy, tabele lub inną obsługiwaną zawartość. Na przykład Edycja dokumentu, artykułu lub blogu wymagającego formatowania, obrazów itp. jest najlepiej realizowana przy użyciu <xref:System.Windows.Controls.RichTextBox> . W poniższej tabeli zestawiono podstawowe funkcje programu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> .  
  
|Kontrola|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Polecenia formatowania, takie jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Rob + B)|<xref:System.Windows.Documents.FlowDocument>zawartość, taka jak obrazy, akapity, tabele itd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Yes|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak (zobacz [RichTextBox — Omówienie](richtextbox-overview.md))|Tak (zobacz [RichTextBox — Omówienie](richtextbox-overview.md))|  
  
> [!NOTE]
> Mimo że <xref:System.Windows.Controls.TextBox> program nie obsługuje formatowania powiązanych poleceń edycji <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> , takich jak (Rob + B), wiele podstawowych poleceń jest obsługiwanych przez obie kontrolki, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> . Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkcje obsługiwane przez program <xref:System.Windows.Controls.TextBox> zostały omówione w poniższych sekcjach. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.RichTextBox> , zobacz [RichTextBox Overview](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć sprawdzanie pisowni w czasie rzeczywistym w programie <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> . Gdy sprawdzanie pisowni jest włączone, czerwona linia pojawia się pod wszelkimi błędnie napisanymi wyrazami (zobacz rysunek poniżej).  
  
 ![Pole tekstowe ze sprawdzaniem pisowni&#45;](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [Włączanie sprawdzania pisowni w kontrolce edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md) , aby dowiedzieć się, jak włączyć sprawdzanie pisowni.  
  
### <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie zarówno, <xref:System.Windows.Controls.TextBox> jak i <xref:System.Windows.Controls.RichTextBox> mają menu kontekstowe, które pojawia się, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz kontrolki. Menu kontekstowe umożliwia użytkownikowi wycinanie, kopiowanie i wklejanie (Zobacz zdjęcie poniżej).  
  
 ![Pole tekstowe z menu kontekstowym](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne niestandardowe menu kontekstowe, aby zastąpić zachowanie domyślne. Aby uzyskać więcej informacji [, zobacz Używanie niestandardowego menu kontekstowego z polem tekstowym](how-to-use-a-custom-context-menu-with-a-textbox.md) .  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Tworzenie pól tekstowych  
 <xref:System.Windows.Controls.TextBox>Może być pojedynczym wierszem w wysokości lub zawierać wiele wierszy. Pojedynczy wiersz <xref:System.Windows.Controls.TextBox> jest najlepszy do umieszczania niewielkich ilości zwykłego tekstu (tj. "name", "numer telefonu" itp.). Poniższy przykład pokazuje, jak utworzyć pojedynczy wiersz <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Można również utworzyć obiekt <xref:System.Windows.Controls.TextBox> , który umożliwia użytkownikowi wprowadzanie wielu wierszy tekstu. Na przykład, jeśli formularz zażądał biographicalego szkicu użytkownika, warto użyć <xref:System.Windows.Controls.TextBox> , który obsługuje wiele wierszy tekstu. Poniższy przykład pokazuje, jak użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do zdefiniowania <xref:System.Windows.Controls.TextBox> kontrolki, która automatycznie powiększa się, aby pomieścić wiele wierszy tekstu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atrybutu powoduje, że `Wrap` tekst będzie zawijany do nowego wiersza po <xref:System.Windows.Controls.TextBox> osiągnięciu krawędzi kontrolki, automatyczne powiększanie <xref:System.Windows.Controls.TextBox> kontrolki w celu dołączenia miejsca dla nowego wiersza, w razie potrzeby.  
  
 Ustawienie <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atrybutu `true` powoduje, że nowy wiersz zostanie wstawiony po naciśnięciu klawisza powrotu, po ponownym rozwinięciu automatycznie, <xref:System.Windows.Controls.TextBox> Aby uwzględnić miejsce dla nowego wiersza, w razie potrzeby.  
  
 Ten <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atrybut dodaje pasek przewijania do <xref:System.Windows.Controls.TextBox> , tak aby zawartość <xref:System.Windows.Controls.TextBox> można przewijać w przypadku, gdy <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiar ramki lub okna.  
  
 Aby uzyskać więcej informacji na temat różnych zadań skojarzonych z korzystaniem z programu <xref:System.Windows.Controls.TextBox> , zobacz [Tematy](textbox-how-to-topics.md)porad.  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Wykrywaj zmiany zawartości  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenie powinno być używane do wykrywania każdego tekstu <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> zmiany, a nie w <xref:System.Windows.UIElement.KeyDown> oczekiwany sposób. Zobacz [Wykryj, kiedy tekst w polu tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) na przykład.  
  
## <a name="see-also"></a>Zobacz też

- [— Tematy porad](textbox-how-to-topics.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
