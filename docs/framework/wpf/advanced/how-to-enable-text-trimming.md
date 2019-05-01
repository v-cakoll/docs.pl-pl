---
title: 'Instrukcje: Włączanie przycinania tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimming text
- trimming text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 25fff566868e792004a915fee195485c4a1f385f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776129"
---
# <a name="how-to-enable-text-trimming"></a>Instrukcje: Włączanie przycinania tekstu

W tym przykładzie przedstawiono użycie i efekty wartości, które są dostępne w <xref:System.Windows.TextTrimming> wyliczenia.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.TextBlock> element z <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> atrybut.

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

Ustawienie odpowiednich <xref:System.Windows.TextTrimming> właściwości w kodzie przedstawiono poniżej.

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

Istnieją obecnie trzy opcje przycinanie tekstu: **CharacterEllipsis**, **WordEllipsis**, i **Brak**.

Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **CharacterEllipsis**, tekst jest przycinana i kontynuowanie z wielokropkiem w najbliższej krawędzi przycinanie znaków.  To ustawienie zwykle przycinanie tekstu do rozmiaru dokładniej do granicy przycinania, ale może spowodować częściowo przycinany słów.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.

![Przykład: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")

Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **WordEllipsis**, tekst jest przycinana i kontynuowanie z wielokropkiem na końcu pierwszego pełny wyraz najbliższej krawędzi przycinania.  To ustawienie nie zostanie wyświetlone, częściowo przycięty wyrazów, ale zwykle nie przycinany tekst możliwie krawędzi przycinania jako **CharacterEllipsis** ustawienie.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> zdefiniowanych powyżej.

![Przykład: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")

Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **Brak**, odbywa się nie przycinanie tekstu.  W tym przypadku tekst jest po prostu przycięte do granicy nadrzędnego kontenera tekstu.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.

![Przykład: Opcja TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")
