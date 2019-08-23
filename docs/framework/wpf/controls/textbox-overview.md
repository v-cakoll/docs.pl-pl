---
title: TextBox — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951487"
---
# <a name="textbox-overview"></a>TextBox — Przegląd
<xref:System.Windows.Controls.TextBox> Klasa umożliwia wyświetlanie lub edytowanie niesformatowanego tekstu. Typowym zastosowaniem <xref:System.Windows.Controls.TextBox> jest edytowanie niesformatowanego tekstu w formularzu. Na przykład formularz z prośbą o nazwę użytkownika, numer telefonu itp. użyje <xref:System.Windows.Controls.TextBox> kontrolek do wprowadzania tekstu. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasę i przedstawiono przykłady używania jej w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> jak i umożliwiają użytkownikom wprowadzanie tekstu, ale dwie kontrolki są używane w różnych scenariuszach. Program wymaga mniej zasobów systemowych, <xref:System.Windows.Controls.RichTextBox> dlatego jest idealnym rozwiązaniem, gdy wystarczy edytować tylko zwykły tekst (tj. użycie w formularzu). <xref:System.Windows.Controls.TextBox> A <xref:System.Windows.Controls.RichTextBox> jest lepszym wyborem, gdy jest to konieczne, aby użytkownik mógł edytować sformatowany tekst, obrazy, tabele lub inną obsługiwaną zawartość. Na przykład Edycja dokumentu, artykułu lub blogu wymagającego formatowania, obrazów itp <xref:System.Windows.Controls.RichTextBox>. jest najlepiej realizowana przy użyciu. W poniższej tabeli zestawiono podstawowe funkcje programu <xref:System.Windows.Controls.TextBox> i. <xref:System.Windows.Controls.TextBox>  
  
|formant|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Polecenia formatowania, <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> takie jak (Rob + B)|<xref:System.Windows.Documents.FlowDocument>zawartość, taka jak obrazy, akapity, tabele itd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Yes|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak (zobacz [RichTextBox — Omówienie](richtextbox-overview.md))|Tak (zobacz [RichTextBox — Omówienie](richtextbox-overview.md))|  
  
> [!NOTE]
> Mimo <xref:System.Windows.Controls.TextBox> że program nie obsługuje formatowania powiązanych <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> poleceń edycji, takich jak (Rob + B), wiele podstawowych poleceń jest obsługiwanych przez obie <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>kontrolki, takie jak. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkcje obsługiwane przez <xref:System.Windows.Controls.TextBox> program zostały omówione w poniższych sekcjach. Aby uzyskać więcej informacji <xref:System.Windows.Controls.RichTextBox>na temat, zobacz [RichTextBox Overview](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć sprawdzanie pisowni w czasie rzeczywistym w programie <xref:System.Windows.Controls.TextBox> lub. <xref:System.Windows.Controls.RichTextBox> Gdy sprawdzanie pisowni jest włączone, czerwona linia pojawia się pod wszelkimi błędnie napisanymi wyrazami (zobacz rysunek poniżej).  
  
 ![Pole tekstowe ze&#45;sprawdzaniem pisowni](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [Włączanie sprawdzania pisowni w kontrolce edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md) , aby dowiedzieć się, jak włączyć sprawdzanie pisowni.  
  
### <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie zarówno <xref:System.Windows.Controls.TextBox> , jak i <xref:System.Windows.Controls.RichTextBox> mają menu kontekstowe, które pojawia się, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz kontrolki. Menu kontekstowe umożliwia użytkownikowi wycinanie, kopiowanie i wklejanie (Zobacz zdjęcie poniżej).  
  
 ![Pole tekstowe z menu kontekstowym](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne niestandardowe menu kontekstowe, aby zastąpić zachowanie domyślne. Aby uzyskać więcej informacji [, zobacz Używanie niestandardowego menu kontekstowego z polem tekstowym](how-to-use-a-custom-context-menu-with-a-textbox.md) .  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Tworzenie pól tekstowych  
 <xref:System.Windows.Controls.TextBox> Może być pojedynczym wierszem w wysokości lub zawierać wiele wierszy. Pojedynczy wiersz <xref:System.Windows.Controls.TextBox> jest najlepszy do umieszczania niewielkich ilości zwykłego tekstu (tj. "Name", "numer telefonu" itp. w formularzu). Poniższy przykład pokazuje, jak utworzyć pojedynczy wiersz <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Można również utworzyć obiekt <xref:System.Windows.Controls.TextBox> , który umożliwia użytkownikowi wprowadzanie wielu wierszy tekstu. Na przykład, jeśli formularz zażądał biographicalego szkicu użytkownika, warto użyć <xref:System.Windows.Controls.TextBox> , który obsługuje wiele wierszy tekstu. Poniższy przykład pokazuje, jak użyć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do <xref:System.Windows.Controls.TextBox> zdefiniowania kontrolki, która automatycznie powiększa się, aby pomieścić wiele wierszy tekstu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ustawienie <xref:System.Windows.Controls.TextBox.TextWrapping%2A> <xref:System.Windows.Controls.TextBox> atrybutu powoduje, że tekst będzie zawijany do nowego wiersza po osiągnięciu krawędzi kontrolki, automatyczne powiększanie <xref:System.Windows.Controls.TextBox> kontrolki w celu dołączenia miejsca dla nowego wiersza, w razie potrzeby. `Wrap`  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> Ustawienie <xref:System.Windows.Controls.TextBox> atrybutu powoduje, że nowy wiersz zostanie wstawiony po naciśnięciu klawisza powrotu, po ponownym rozwinięciu automatycznie, aby uwzględnić miejsce dla nowego wiersza, w razie potrzeby. `true`  
  
 Ten <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atrybut dodaje pasek przewijania <xref:System.Windows.Controls.TextBox>do, tak aby zawartość <xref:System.Windows.Controls.TextBox> można przewijać w przypadku, gdy <xref:System.Windows.Controls.TextBox> rozszerza się poza rozmiar ramki lub okna.  
  
 Aby uzyskać więcej informacji na temat różnych zadań skojarzonych z <xref:System.Windows.Controls.TextBox>korzystaniem z programu, zobacz [Tematy](textbox-how-to-topics.md)porad.  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Wykrywaj zmiany zawartości  
 Zazwyczaj zdarzenie powinno być używane do wykrywania każdego <xref:System.Windows.Controls.TextBox> tekstu <xref:System.Windows.UIElement.KeyDown> lub <xref:System.Windows.Controls.RichTextBox> zmiany, a nie w oczekiwany sposób. <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> Zobacz [Wykryj, kiedy tekst w polu tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) na przykład.  
  
## <a name="see-also"></a>Zobacz także

- [Tematy z instrukcjami](textbox-how-to-topics.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
