---
title: "RichTextBox — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e88afe5f9c35448b3234498af413500bee163abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="richtextbox-overview"></a>RichTextBox — Przegląd
<xref:System.Windows.Controls.RichTextBox> Kontroli umożliwia wyświetlanie lub edytowanie tym akapitów, obrazy, tabele i zawartości przepływu. W tym temacie przedstawiono <xref:System.Windows.Controls.TextBox> klasy i przykłady dotyczące używania go w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox lub RichTextBox?  
 Zarówno <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.TextBox> Zezwalaj użytkownikom na edytowanie tekstu, jednak dwóch formantów są używane w różnych scenariuszach. A <xref:System.Windows.Controls.RichTextBox> jest lepszym rozwiązaniem, gdy jest to niezbędne dla użytkownika edytować tekst sformatowany, obrazów, tabel lub innych bogatej zawartości. Na przykład edytowanie dokumentu, artykuł lub blog, która wymaga formatowania, obrazy, itp. najlepiej odbywa się przy użyciu <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> wymaga mniej zasobów systemowych, a następnie <xref:System.Windows.Controls.RichTextBox> i jest idealnym rozwiązaniem, gdy tylko zwykły tekst musi być edytowany (tj. użycie w formularzach). Zobacz [omówienie pole tekstowe](../../../../docs/framework/wpf/controls/textbox-overview.md) Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.TextBox>. Poniższa tabela zawiera podsumowanie najważniejszych funkcji usługi <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox>.  
  
|Formant|Sprawdzanie pisowni w czasie rzeczywistym|Menu kontekstowe|Formatowanie poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (ewidencyjne + B)|<xref:System.Windows.Documents.FlowDocument>zawartość, takich jak obrazy, akapitów, tabelach itp.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Tak|Tak|Nie|Nie.|  
|<xref:System.Windows.Controls.RichTextBox>|Tak|Tak|Tak|Tak|  
  
 **Uwaga:** chociaż <xref:System.Windows.Controls.TextBox> nie obsługuje pokrewnych poleceń, takich jak <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> ewidencyjne + B, wiele podstawowych poleceń są obsługiwane przez oba formanty, takie jak <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Funkcje dostępne w powyższej tabeli są opisane bardziej szczegółowo później.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Tworzenie w kontrolce RichTextBox  
 Poniższy kod przedstawia sposób tworzenia <xref:System.Windows.Controls.RichTextBox> czy użytkownik może edytować zawartość sformatowanego.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 W szczególności edytować zawartość w <xref:System.Windows.Controls.RichTextBox> zawartość śródwierszowa jest. Zawartość śródwierszowa może zawierać wiele typów elementów w tym sformatowany tekst, obrazy, listy i tabele. Zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md) uzyskać szczegółowe informacje na temat przepływu dokumentów. Aby zawartością przepływu <xref:System.Windows.Controls.RichTextBox> hostów <xref:System.Windows.Documents.FlowDocument> obiektu, który z kolei zawiera edytowalnej zawartości. Aby zademonstrować dowolnej zawartości w <xref:System.Windows.Controls.RichTextBox>, poniższy kod przedstawia sposób tworzenia <xref:System.Windows.Controls.RichTextBox> akapitu i pogrubiony tekst.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Na poniższej ilustracji przedstawiono, jak ten przykład renderuje.  
  
 ![RichTextBox z zawartością](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Elementów, takich jak <xref:System.Windows.Documents.Paragraph> i <xref:System.Windows.Documents.Bold> ustalić sposób zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> pojawi się. Jako użytkownik edytuje <xref:System.Windows.Controls.RichTextBox> zawartości, ich zmienianie tej zawartości przepływu. Aby dowiedzieć się więcej na temat funkcji przepływ zawartości i sposobu pracy z nim, zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 **Uwaga:** przepływ zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> zachowuje się tak samo jak zawartość śródwierszowa zawarte w innych kontrolek. Na przykład Brak kolumn w <xref:System.Windows.Controls.RichTextBox> i dlatego nie automatyczna zmiana rozmiaru zachowanie. Ponadto wbudowane funkcje, takie jak wyszukiwanie, trybu wyświetlania, Nawigacja strony i powiększenia nie są dostępne w ramach <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Sprawdzanie pisowni w czasie rzeczywistym  
 Można włączyć sprawdzania czasie rzeczywistym pisowni <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>. Gdy sprawdzanie pisowni jest włączone, czerwoną linią pojawi się poniżej żadnych pisowni (patrz rysunek poniżej).  
  
 ![Pole tekstowe z pisowni &#45; sprawdzanie](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobacz [włączyć sprawdzanie pisowni w formancie edycji tekstu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) Aby dowiedzieć się, jak włączyć sprawdzanie pisowni.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Menu kontekstowe  
 Domyślnie oba <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> ma menu kontekstowego, który jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy wewnątrz formantu. Menu kontekstowe zezwala użytkownikowi na wycinanie, kopiowanie lub wklejanie (zobacz rysunek poniżej).  
  
 ![Pole tekstowe z menu kontekstowego](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Możesz utworzyć własne menu kontekstowe niestandardowe, aby zastąpić domyślny. Zobacz [pozycji Menu kontekstowego niestandardowe w kontrolce RichTextBox](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md) Aby uzyskać więcej informacji.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Poleceń edycji  
 Edytowanie polecenia umożliwianie użytkownikom edytowalnej zawartości w formacie <xref:System.Windows.Controls.RichTextBox>. Oprócz basic polecenia, edycji <xref:System.Windows.Controls.RichTextBox> zawiera polecenia formatowania, który <xref:System.Windows.Controls.TextBox> nie obsługuje. Na przykład podczas edycji w <xref:System.Windows.Controls.RichTextBox>, użytkownik może nacisnąć kont. + B Przełącz ustawienie opcji formatowania pogrubioną. Zobacz <xref:System.Windows.Documents.EditingCommands> pełną listę dostępnych poleceń. Oprócz za pomocą skrótów klawiaturowych, zostanie utworzenie punktu zaczepienia poleceń do inne formanty, takie jak przyciski. Poniższy przykład przedstawia sposób tworzenia prostego narzędzia paska zawierający przycisków, które użytkownik może użyć do zmiany formatowania tekstu.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono sposób wyświetlania w tym przykładzie.  
  
 ![RichTextBox z paskiem narzędzi](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Wykryj, kiedy zmienia zawartości  
 Zazwyczaj <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia mają być używane do wykrywania po każdej zmianie tekstu w <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox> zmienia zamiast <xref:System.Windows.UIElement.KeyDown> zgodnie z oczekiwaniami może. Zobacz [wykryć gdy tekst w pole tekstowe został zmieniony](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) przykład.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Zapisz, ładuj i drukuj zawartość RichTextBox  
 Poniższy przykład pokazuje, jak można zapisać zawartości <xref:System.Windows.Controls.RichTextBox> do pliku, załadować tego treść z powrotem do <xref:System.Windows.Controls.RichTextBox>i Drukuj zawartość. Poniżej znajduje się kod znaczników dla przykładu.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Poniżej znajduje się za przykładowy kod.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)
