---
title: RichTextBox — Przegląd
description: Dowiedz się, w jaki sposób formant RichTextBox Windows Presentation Foundation umożliwia użytkownikom wyświetlanie i Edytowanie zawartości, takiej jak tekst, obrazy i tabele. Zobacz przykłady XAML i C#.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166244"
---
# <a name="richtextbox-overview"></a>RichTextBox — Przegląd

<xref:System.Windows.Controls.RichTextBox>Kontrolka umożliwia wyświetlanie i Edytowanie zawartości przepływu, w tym akapitów, obrazów, tabel i innych. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasę i przedstawiono przykłady używania jej w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?

Jednocześnie <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.TextBox> Zezwalaj użytkownikom na edytowanie tekstu, jednak te dwa kontrolki są używane w różnych scenariuszach. A <xref:System.Windows.Controls.RichTextBox> to lepszy wybór, gdy jest to konieczne, aby użytkownik mógł edytować sformatowany tekst, obrazy, tabele lub inną rozbudowaną zawartość. Na przykład Edycja dokumentu, artykułu lub blogu wymagającego formatowania, obrazów itp. jest najlepiej realizowana przy użyciu <xref:System.Windows.Controls.RichTextBox> . <xref:System.Windows.Controls.TextBox>Program wymaga mniej zasobów systemowych <xref:System.Windows.Controls.RichTextBox> i jest idealnym rozwiązaniem, gdy wystarczy edytować tylko zwykły tekst (tj. użycie w formularzach). Aby uzyskać więcej informacji na temat, zobacz [TextBox — Omówienie](textbox-overview.md) <xref:System.Windows.Controls.TextBox> . Poniższa tabela zawiera podsumowanie głównych funkcji programu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> .

|Kontrola|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Polecenia formatowania, takie jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Rob + B)|<xref:System.Windows.Documents.FlowDocument>zawartość, taka jak obrazy, akapity, tabele itd.|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Tak|Yes|Nie|Nie.|
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak|Tak|

> [!NOTE]
> Chociaż nie <xref:System.Windows.Controls.TextBox> obsługuje formatowania poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Rob + B), wiele podstawowych poleceń jest obsługiwanych przez obie kontrolki, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> .

Funkcje z powyższej tabeli zostały omówione bardziej szczegółowo w dalszej części.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>Tworzenie RichTextBox

Poniższy kod pokazuje, jak utworzyć <xref:System.Windows.Controls.RichTextBox> , że użytkownik może edytować rozbudowaną zawartość.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

W przypadku zawartości edytowanej w programie <xref:System.Windows.Controls.RichTextBox> jest zawartość przepływu. Zawartość przepływu może zawierać wiele typów elementów, takich jak sformatowany tekst, obrazy, listy i tabele. Zobacz [Omówienie dokumentu przepływu](../advanced/flow-document-overview.md) dla szczegółowych informacji o dokumentach przepływu. Aby można było zawierać zawartość przepływu, <xref:System.Windows.Controls.RichTextBox> hosty, <xref:System.Windows.Documents.FlowDocument> który z kolei zawiera zawartość edytowalną. Aby zademonstrować zawartość przepływu w programie <xref:System.Windows.Controls.RichTextBox> , poniższy kod ilustruje sposób tworzenia <xref:System.Windows.Controls.RichTextBox> z akapitem i fragmentem tekstu pogrubionego.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.

![RichTextBox z zawartością](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Elementy takie jak <xref:System.Windows.Documents.Paragraph> i <xref:System.Windows.Documents.Bold> określają sposób, w jaki <xref:System.Windows.Controls.RichTextBox> znajduje się zawartość wewnątrz. Użytkownik edytuje <xref:System.Windows.Controls.RichTextBox> zawartość, zmieniając zawartość tego przepływu. Aby dowiedzieć się więcej o funkcjach zawartości przepływu i sposobach ich pracy, zobacz [dokument przepływu — Omówienie](../advanced/flow-document-overview.md).

> [!NOTE]
> Zawartość przepływu wewnątrz elementu <xref:System.Windows.Controls.RichTextBox> nie zachowuje się dokładnie tak, jak zawartość przepływu zawarta w innych kontrolkach. Na przykład nie ma żadnych kolumn w <xref:System.Windows.Controls.RichTextBox> i nie ma żadnego automatycznego zmieniania rozmiarów. Ponadto wbudowane funkcje, takie jak wyszukiwanie, tryb wyświetlania, Nawigacja po stronie i powiększenie, nie są dostępne w programie <xref:System.Windows.Controls.RichTextBox> .

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Sprawdzanie pisowni w czasie rzeczywistym

Można włączyć sprawdzanie pisowni w czasie rzeczywistym w programie <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> . Gdy sprawdzanie pisowni jest włączone, czerwona linia pojawia się pod wszelkimi błędnie napisanymi wyrazami (zobacz rysunek poniżej).

![Pole tekstowe ze sprawdzaniem pisowni&#45;](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Zobacz [Włączanie sprawdzania pisowni w kontrolce edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md) , aby dowiedzieć się, jak włączyć sprawdzanie pisowni.

<a name="context_menu"></a>

## <a name="context-menu"></a>Menu kontekstowe

Domyślnie zarówno, <xref:System.Windows.Controls.TextBox> jak i <xref:System.Windows.Controls.RichTextBox> mają menu kontekstowe, które pojawia się, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz kontrolki. Menu kontekstowe umożliwia użytkownikowi wycinanie, kopiowanie i wklejanie (Zobacz ilustrację poniżej).

![Pole tekstowe z menu kontekstowym](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Możesz utworzyć własne niestandardowe menu kontekstowe, aby przesłonić wartość domyślną. Aby uzyskać więcej informacji [, zobacz pozycjonowanie niestandardowego menu kontekstowego w RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) .

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Edytowanie poleceń

Edycja poleceń umożliwia użytkownikom formatowanie edytowalnej zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> . Oprócz podstawowych poleceń edycji program <xref:System.Windows.Controls.RichTextBox> zawiera polecenia formatowania, które <xref:System.Windows.Controls.TextBox> nie są obsługiwane. Na przykład podczas edytowania w programie <xref:System.Windows.Controls.RichTextBox> użytkownik może nacisnąć pozycję Rob + B w celu przełączenia formatowania pogrubionego tekstu. Zobacz <xref:System.Windows.Documents.EditingCommands> , aby uzyskać pełną listę dostępnych poleceń. Oprócz używania skrótów klawiaturowych można podłączyć polecenia do innych kontrolek, takich jak przyciski. Poniższy przykład pokazuje, jak utworzyć prosty pasek narzędzi zawierający przyciski, których użytkownik może użyć do zmiany formatowania tekstu.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

Na poniższej ilustracji przedstawiono sposób wyświetlania tego przykładu.

![RichTextBox z paskiem narzędzi](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Wykrywaj zmiany zawartości

Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenie powinno być używane do wykrywania za każdym razem, gdy tekst jest lub zmienia się w zależności od tego, czy jest to <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.UIElement.KeyDown> oczekiwane. Zobacz [Wykryj, kiedy tekst w polu tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) na przykład.

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>Zapisz, ładuj i drukuj zawartość RichTextBox

Poniższy przykład pokazuje, jak zapisać zawartość <xref:System.Windows.Controls.RichTextBox> do pliku, załadować tę zawartość z powrotem do <xref:System.Windows.Controls.RichTextBox> i wydrukować zawartość. Poniżej znajduje się znacznik dla przykładu.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Poniżej znajduje się kod dla przykładu.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Zobacz także

- [— Tematy porad](richtextbox-how-to-topics.md)
- [TextBox — Przegląd](textbox-overview.md)
