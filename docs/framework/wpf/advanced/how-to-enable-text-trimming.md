---
title: "Jak włączyć przycinanie tekstu"
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
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8f0f24bb6271e63dc50bd063aedfd8185711e7a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="0b466-102">Jak włączyć przycinanie tekstu</span><span class="sxs-lookup"><span data-stu-id="0b466-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="0b466-103">Przykładzie przedstawiono sposób użycia i skutków dostępnymi w wartości <xref:System.Windows.TextTrimming> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0b466-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b466-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b466-104">Example</span></span>  
 <span data-ttu-id="0b466-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.TextBlock> element z <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> atrybut.</span><span class="sxs-lookup"><span data-stu-id="0b466-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="0b466-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b466-106">Example</span></span>  
 <span data-ttu-id="0b466-107">Ustawienie odpowiadającego <xref:System.Windows.TextTrimming> właściwości w kodzie przedstawiono poniżej.</span><span class="sxs-lookup"><span data-stu-id="0b466-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="0b466-108">Dostępne są obecnie trzy opcje przycinanie tekstu: **CharacterEllipsis**, **WordEllipsis**, i **Brak**.</span><span class="sxs-lookup"><span data-stu-id="0b466-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="0b466-109">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **CharacterEllipsis**, tekst jest ograniczona i nadal z wielokropkiem na najbliższą krawędzią przycinanie znaków.</span><span class="sxs-lookup"><span data-stu-id="0b466-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="0b466-110">To ustawienie zwykle przycinany tekst, który lepiej dopasowania do granicy przycinanie, ale może spowodować wyrazy, gdzie są obcinane częściowo.</span><span class="sxs-lookup"><span data-stu-id="0b466-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="0b466-111">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="0b466-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="0b466-112">![Przykład: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="0b466-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="0b466-113">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **WordEllipsis**, tekst jest ograniczona i nadal z wielokropkiem na końcu pierwszego pełnego wyrazu najbliższą krawędzią przycinania.</span><span class="sxs-lookup"><span data-stu-id="0b466-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="0b466-114">To ustawienie nie zostanie wyświetlone częściowo wycięte wyrazów, ale nie powoduje przycinany tekst używanemu do krawędzi przycinanie jako **CharacterEllipsis** ustawienie.</span><span class="sxs-lookup"><span data-stu-id="0b466-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="0b466-115">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="0b466-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="0b466-116">![Przykład: Opcja TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="0b466-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="0b466-117">Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ma ustawioną wartość **Brak**, przycinanie tekstu, nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="0b466-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="0b466-118">W takim przypadku tekst jest po prostu przycięty do granicy kontenera nadrzędnego tekstu.</span><span class="sxs-lookup"><span data-stu-id="0b466-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="0b466-119">Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="0b466-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="0b466-120">![Przykład: Opcja TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="0b466-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
