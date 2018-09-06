---
title: Jak utworzyć formant z kluczem dostępu i zwijaniem tekstu
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: bc170334496ca4c2a2028b9c493385674d235ca6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745612"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="aafb9-102">Jak utworzyć formant z kluczem dostępu i zwijaniem tekstu</span><span class="sxs-lookup"><span data-stu-id="aafb9-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="aafb9-103">W tym przykładzie pokazano, jak utworzyć formant, który ma klucz dostępu i obsługuje zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="aafb9-104">W przykładzie użyto <xref:System.Windows.Controls.Label> kontroli w celu zilustrowania koncepcji te.</span><span class="sxs-lookup"><span data-stu-id="aafb9-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aafb9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="aafb9-105">Example</span></span>  
 <span data-ttu-id="aafb9-106">**Dodaj zawijania tekstu do etykiety**</span><span class="sxs-lookup"><span data-stu-id="aafb9-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="aafb9-107"><xref:System.Windows.Controls.Label> Kontrolka nie obsługuje operacji zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="aafb9-108">Jeśli potrzebujesz etykiety, która otacza w wielu wierszach, można zagnieżdżać inny element, który obsługuje tekst opakowywanie i umieść element w etykiecie.</span><span class="sxs-lookup"><span data-stu-id="aafb9-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="aafb9-109">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.TextBlock> się etykietę, która otacza kilka wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="aafb9-110">**Dodaj klucz dostępu i zwijaniem tekstu do etykiety**</span><span class="sxs-lookup"><span data-stu-id="aafb9-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="aafb9-111">Jeśli potrzebujesz <xref:System.Windows.Controls.Label> zawierający klawisza dostępu (Mnemonik), należy użyć <xref:System.Windows.Controls.AccessText> element, który znajduje się wewnątrz <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="aafb9-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="aafb9-112">Określa, takich jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, i <xref:System.Windows.Controls.GroupBox> mają domyślne szablony kontrolek.</span><span class="sxs-lookup"><span data-stu-id="aafb9-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="aafb9-113">Te szablony zawierają <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="aafb9-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="aafb9-114">Jedna z właściwości, które mogą być ustawione na <xref:System.Windows.Controls.ContentPresenter> jest <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", którego można użyć do określenia klucza dostępu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="aafb9-115">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Label> który ma klucz dostępu i obsługuje zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="aafb9-116">Aby włączyć zawijania tekstu, przykład ustawia <xref:System.Windows.Controls.AccessText.TextWrapping%2A> właściwości i używa podkreślenia znaków do określenia klucza dostępu.</span><span class="sxs-lookup"><span data-stu-id="aafb9-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="aafb9-117">(Znak, który następuje bezpośrednio po znaku podkreślenia jest klucz dostępu).</span><span class="sxs-lookup"><span data-stu-id="aafb9-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="aafb9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aafb9-118">See Also</span></span>  
 [<span data-ttu-id="aafb9-119">Porady: Ustawianie właściwości docelowej etykiety</span><span class="sxs-lookup"><span data-stu-id="aafb9-119">How to: Set the Target Property of a Label</span></span>](https://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
