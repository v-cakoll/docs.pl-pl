---
title: 'Porady: wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532464"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="7f54f-102">Porady: wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl</span><span class="sxs-lookup"><span data-stu-id="7f54f-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="7f54f-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Właściwość <xref:System.Windows.Forms.TabControl> obsługuje wyświetlanie kart pionie (wzdłuż lewej lub prawej krawędzi formantu), w przeciwieństwie do poziomo (za pośrednictwem góry lub u dołu formantu).</span><span class="sxs-lookup"><span data-stu-id="7f54f-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="7f54f-104">Domyślnie ta wyświetlania pionowego powoduje niską użytkowników, ponieważ <xref:System.Windows.Forms.TabPage.Text%2A> właściwość <xref:System.Windows.Forms.TabPage> obiektu nie są wyświetlane na karcie podczas style wizualne są włączone.</span><span class="sxs-lookup"><span data-stu-id="7f54f-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="7f54f-105">Istnieje również bezpośrednim sposobem kontrolować kierunek tekstu w karcie. Można użyć właściciela Rysowanie w <xref:System.Windows.Forms.TabControl> aby poprawić działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f54f-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="7f54f-106">Poniższa procedura przedstawia sposób renderowania wyrównany karty tekstem kartę systemem od lewej do prawej, korzystając z funkcji "rysowania przez właściciela".</span><span class="sxs-lookup"><span data-stu-id="7f54f-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="7f54f-107">Aby wyświetlić karty wyrównany do prawej</span><span class="sxs-lookup"><span data-stu-id="7f54f-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="7f54f-108">Dodaj <xref:System.Windows.Forms.TabControl> do formularza.</span><span class="sxs-lookup"><span data-stu-id="7f54f-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="7f54f-109">Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwości <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="7f54f-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="7f54f-110">Ustaw <xref:System.Windows.Forms.TabControl.SizeMode%2A> właściwości <xref:System.Windows.Forms.TabSizeMode.Fixed>, tak aby wszystkie karty są tej samej szerokości.</span><span class="sxs-lookup"><span data-stu-id="7f54f-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="7f54f-111">Ustaw <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwości preferowany stały rozmiar kart.</span><span class="sxs-lookup"><span data-stu-id="7f54f-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="7f54f-112">Należy pamiętać, że <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwości zachowuje się tak, jakby były karty w górnej części, chociaż są wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="7f54f-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="7f54f-113">W związku z tym w celu karty szersze, należy zmienić <xref:System.Drawing.Size.Height%2A> właściwości, oraz w celu zapewnienia ich wyższe, należy zmienić <xref:System.Drawing.Size.Width%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7f54f-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="7f54f-114">Aby uzyskać najlepsze wyniki w poniższym przykładzie kodu, należy ustawić <xref:System.Drawing.Size.Width%2A> kart do 25 i <xref:System.Drawing.Size.Height%2A> do 100.</span><span class="sxs-lookup"><span data-stu-id="7f54f-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="7f54f-115">Ustaw <xref:System.Windows.Forms.TabControl.DrawMode%2A> właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="7f54f-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="7f54f-116">Definiowanie procedury obsługi dla <xref:System.Windows.Forms.TabControl.DrawItem> zdarzenie <xref:System.Windows.Forms.TabControl> która renderuje tekstu od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="7f54f-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7f54f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f54f-117">See Also</span></span>  
 [<span data-ttu-id="7f54f-118">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7f54f-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
