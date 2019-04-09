---
title: RichTextBox — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162714"
---
# <a name="richtextbox-overview"></a>RichTextBox — Przegląd
<xref:System.Windows.Controls.RichTextBox> Control umożliwia wyświetlanie lub edytowanie zawartości przepływu, w tym akapitów, obrazy, tabele i. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasy i przykłady dotyczące używania go w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.TextBox> umożliwia użytkownikom edytowanie tekstu, jednak dwa formanty są używane w różnych scenariuszach. Element <xref:System.Windows.Controls.RichTextBox> jest lepszym rozwiązaniem, gdy jest to niezbędne do użytkownika o taką edycję tekstu sformatowanego, obrazy, tabele lub inne sformatowanej zawartości. Na przykład, edytowanie dokumentów, artykuł lub blogów, która wymaga formatowania, obrazy, itp. najlepiej odbywa się przy użyciu <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> wymaga mniej zasobów systemowych, a następnie <xref:System.Windows.Controls.RichTextBox> i jest idealnym rozwiązaniem, gdy tylko zwykły tekst musi być edytowany (tzn. użycie w formularzach). Zobacz [TextBox — Przegląd](textbox-overview.md) więcej informacji na temat <xref:System.Windows.Controls.TextBox>. Poniższa tabela zawiera podsumowanie najważniejszych funkcji <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox>.  
  
|formant|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Formatowanie poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (kont. + B)|<xref:System.Windows.Documents.FlowDocument> zawartość, taką jak obrazy, akapitów, tabelach itp.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Yes|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Yes|Yes|Yes|Tak|  
  
 **Uwaga:** Mimo że <xref:System.Windows.Controls.TextBox> nie obsługuje powiązanych poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> kont. + B, wiele podstawowych poleceń są obsługiwane przez oba formanty, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Funkcje z powyższej tabeli są bardziej szczegółowo omówione później.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Tworzenie kontrolki RichTextBox  
 Poniższy kod przedstawia sposób tworzenia <xref:System.Windows.Controls.RichTextBox> czy użytkownik może edytować bogatą zawartość w.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 W szczególności edytować zawartość w <xref:System.Windows.Controls.RichTextBox> zawartości przepływu. Przepływ zawartości może zawierać wiele typów elementów, w tym sformatowany tekst, obrazy, listy i tabele. Zobacz [Przegląd dokumentu przepływu](../advanced/flow-document-overview.md) Aby uzyskać szczegółowe informacje na temat dokumenty przepływu. Aby mogła zawierać zawartość przepływu <xref:System.Windows.Controls.RichTextBox> hosty <xref:System.Windows.Documents.FlowDocument> obiektu, który z kolei zawiera edytowalnej zawartości. Aby zademonstrować dowolnej zawartości w <xref:System.Windows.Controls.RichTextBox>, poniższy kod przedstawia sposób tworzenia <xref:System.Windows.Controls.RichTextBox> akapitu i jakiś tekst pogrubiony.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Poniższa ilustracja przedstawia, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![RichTextBox — z zawartością](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Elementów, takich jak <xref:System.Windows.Documents.Paragraph> i <xref:System.Windows.Documents.Bold> określić sposób, w jaki zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> pojawia się. Jako użytkownik edytuje <xref:System.Windows.Controls.RichTextBox> zawartość, zmiany zawartości tego przepływu. Aby dowiedzieć się więcej na temat funkcji przepływ zawartości i jak pracować z nim, zobacz [Przegląd dokumentu przepływu](../advanced/flow-document-overview.md).  
  
 **Uwaga:** Przepływ zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> nie zachowuje się tak samo jak dowolnej zawartości znajdujących się w innych kontrolek. Na przykład istnieją Brak kolumn w <xref:System.Windows.Controls.RichTextBox> i dlatego nie automatyczne zmienianie rozmiaru zachowanie. Ponadto wbudowane funkcje, takie jak wyszukiwanie, trybu wyświetlania, nawigowania po stronach i powiększenia nie są dostępne w ramach <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć w czasie rzeczywistym sprawdzanie pisowni w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>. Po jej włączeniu sprawdzanie pisowni czerwoną linią pojawia się pod dowolnego błędnie napisanych wyrazów (patrz rysunek poniżej).  
  
 ![Pole tekstowe z pisowni&#45;sprawdzanie](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [włączyć sprawdzanie pisowni w formancie edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md) dowiesz się, jak włączyć sprawdzanie pisowni.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie oba <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> ma menu kontekstowego, który jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz formantu. Menu kontekstowe zezwala użytkownikowi na wycinanie, kopiowanie lub wklejanie (zobacz rysunek poniżej).  
  
 ![Pole tekstowe z menu kontekstowego](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne menu kontekstowego, aby zastąpić domyślny. Zobacz [pozycji niestandardowego Menu kontekstowego w RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) Aby uzyskać więcej informacji.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Polecenia edycji  
 Edytowanie polecenia umożliwianie użytkownikom, aby sformatować edytowalną zawartość wewnątrz <xref:System.Windows.Controls.RichTextBox>. Oprócz podstawowe polecenia, edycji <xref:System.Windows.Controls.RichTextBox> zawiera polecenia formatowania, które <xref:System.Windows.Controls.TextBox> nie obsługuje. Na przykład podczas edycji w <xref:System.Windows.Controls.RichTextBox>, użytkownik może nacisnąć kont. + B, aby przełączyć formatowania tekstu pogrubienie. Zobacz <xref:System.Windows.Documents.EditingCommands> pełną listę dostępnych poleceń. Oprócz używania skróty klawiaturowe, można dołączyć poleceń maksymalnie inne formanty, takie jak przyciski. Poniższy przykład przedstawia sposób tworzenia prostego narzędzia paska zawierający przyciski, które użytkownik może użyć do zmiany formatowania tekstu.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Poniższa ilustracja przedstawia, jak w tym przykładzie wyświetlono.  
  
 ![RichTextBox za pomocą narzędzi](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Wykryj, kiedy zmiany zawartości  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzeń powinny być używane do wykrywania w każdym przypadku, gdy tekst w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> zmiany, a następnie <xref:System.Windows.UIElement.KeyDown> zgodnie z oczekiwaniami. Zobacz [wykrycia podczas tekst w polu tekstowym został zmieniony](how-to-detect-when-text-in-a-textbox-has-changed.md) przykład.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Zapisz, ładuj i drukuj zawartość RichTextBox  
 Poniższy przykład pokazuje, jak można zapisać zawartości <xref:System.Windows.Controls.RichTextBox> do pliku, należy załadować tej zawartości wstecz do <xref:System.Windows.Controls.RichTextBox>i Drukuj zawartość. Oto znaczniki dla przykładu.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Poniżej znajduje się kod w przykładzie.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [— Tematy porad](richtextbox-how-to-topics.md)
- [TextBox — Przegląd](textbox-overview.md)
