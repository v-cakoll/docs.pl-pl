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
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="483c5-102">Instrukcje: Włączanie przycinania tekstu</span><span class="sxs-lookup"><span data-stu-id="483c5-102">How to: Enable Text Trimming</span></span>

<span data-ttu-id="483c5-103">W tym przykładzie przedstawiono użycie i efekty wartości, które są dostępne w <xref:System.Windows.TextTrimming> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="483c5-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>

## <a name="example"></a><span data-ttu-id="483c5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="483c5-104">Example</span></span>

<span data-ttu-id="483c5-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.TextBlock> element z <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> atrybut.</span><span class="sxs-lookup"><span data-stu-id="483c5-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

<span data-ttu-id="483c5-106">Ustawienie odpowiednich <xref:System.Windows.TextTrimming> właściwości w kodzie przedstawiono poniżej.</span><span class="sxs-lookup"><span data-stu-id="483c5-106">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

<span data-ttu-id="483c5-107">Istnieją obecnie trzy opcje przycinanie tekstu: **CharacterEllipsis**, **WordEllipsis**, i **Brak**.</span><span class="sxs-lookup"><span data-stu-id="483c5-107">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>

<span data-ttu-id="483c5-108">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **CharacterEllipsis**, tekst jest przycinana i kontynuowanie z wielokropkiem w najbliższej krawędzi przycinanie znaków.</span><span class="sxs-lookup"><span data-stu-id="483c5-108">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="483c5-109">To ustawienie zwykle przycinanie tekstu do rozmiaru dokładniej do granicy przycinania, ale może spowodować częściowo przycinany słów.</span><span class="sxs-lookup"><span data-stu-id="483c5-109">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="483c5-110">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="483c5-110">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="483c5-111">![Przykład: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="483c5-111">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>

<span data-ttu-id="483c5-112">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **WordEllipsis**, tekst jest przycinana i kontynuowanie z wielokropkiem na końcu pierwszego pełny wyraz najbliższej krawędzi przycinania.</span><span class="sxs-lookup"><span data-stu-id="483c5-112">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="483c5-113">To ustawienie nie zostanie wyświetlone, częściowo przycięty wyrazów, ale zwykle nie przycinany tekst możliwie krawędzi przycinania jako **CharacterEllipsis** ustawienie.</span><span class="sxs-lookup"><span data-stu-id="483c5-113">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="483c5-114">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="483c5-114">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>

<span data-ttu-id="483c5-115">![Przykład: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="483c5-115">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>

<span data-ttu-id="483c5-116">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **Brak**, odbywa się nie przycinanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="483c5-116">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="483c5-117">W tym przypadku tekst jest po prostu przycięte do granicy nadrzędnego kontenera tekstu.</span><span class="sxs-lookup"><span data-stu-id="483c5-117">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="483c5-118">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="483c5-118">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="483c5-119">![Przykład: Opcja TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="483c5-119">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
