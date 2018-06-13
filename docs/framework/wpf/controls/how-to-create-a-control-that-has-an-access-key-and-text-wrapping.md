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
ms.openlocfilehash: 8343c660ddeb5487f46e87534e555936d1b86371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553792"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="b4092-102">Jak utworzyć formant z kluczem dostępu i zwijaniem tekstu</span><span class="sxs-lookup"><span data-stu-id="b4092-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="b4092-103">W tym przykładzie przedstawiono sposób tworzenia formant, który ma klucz dostępu i obsługuje zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4092-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b4092-104">W przykładzie użyto <xref:System.Windows.Controls.Label> kontroli w celu zilustrowania koncepcji te.</span><span class="sxs-lookup"><span data-stu-id="b4092-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4092-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4092-105">Example</span></span>  
 <span data-ttu-id="b4092-106">**Dodaj zawijania tekstu do etykiety**</span><span class="sxs-lookup"><span data-stu-id="b4092-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="b4092-107"><xref:System.Windows.Controls.Label> Formant nie obsługuje zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4092-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="b4092-108">Etykiety, który opakowuje w wielu liniach należy można zagnieżdżać inny element, który obsługuje tekstu zawijania i umieszcza elementu w etykiecie.</span><span class="sxs-lookup"><span data-stu-id="b4092-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="b4092-109">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.TextBlock> aby etykiety, który powoduje błąd kilka wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4092-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="b4092-110">**Dodaj klucz dostępu i zawijania tekstu do etykiety**</span><span class="sxs-lookup"><span data-stu-id="b4092-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="b4092-111">Jeśli potrzebujesz <xref:System.Windows.Controls.Label> zawierającego klawisza dostępu (symbol), użyj <xref:System.Windows.Controls.AccessText> element, który znajduje się wewnątrz <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="b4092-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="b4092-112">Określa, takich jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, i <xref:System.Windows.Controls.GroupBox> ma domyślne szablony formantu.</span><span class="sxs-lookup"><span data-stu-id="b4092-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="b4092-113">Te szablony zawierają <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="b4092-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="b4092-114">Jedna z właściwości, które można ustawić na <xref:System.Windows.Controls.ContentPresenter> jest <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", która służy do określania klucza dostępu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="b4092-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="b4092-115">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Label> , który ma klucz dostępu i obsługuje zawijania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4092-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b4092-116">Aby włączyć zawijania tekstu, ustawia przykład <xref:System.Windows.Controls.AccessText.TextWrapping%2A> właściwości i używa podkreślenie znaku do określenia klucza dostępu.</span><span class="sxs-lookup"><span data-stu-id="b4092-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="b4092-117">(Od razu następuje po znaku podkreślenia znak jest klucz dostępu).</span><span class="sxs-lookup"><span data-stu-id="b4092-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b4092-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4092-118">See Also</span></span>  
 [<span data-ttu-id="b4092-119">Porady: Ustaw właściwość Target etykiety</span><span class="sxs-lookup"><span data-stu-id="b4092-119">How to: Set the Target Property of a Label</span></span>](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
