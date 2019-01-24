---
title: 'Instrukcje: Wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: 9b2d691cb41a48b51bb48291e321d763a9ff7e08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650586"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="2605b-102">Instrukcje: Wyświetlanie wyrównanych poziomo kart przy użyciu formantu TabControl</span><span class="sxs-lookup"><span data-stu-id="2605b-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="2605b-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Właściwość <xref:System.Windows.Forms.TabControl> obsługuje wyświetlanie kart w pionie (wzdłuż lewej lub prawej krawędzi formantu), w przeciwieństwie do poziomo (wzdłuż górnej i dolnej części kontrolki).</span><span class="sxs-lookup"><span data-stu-id="2605b-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="2605b-104">Domyślnie ta pionowe wyświetlanie elementu powoduje niską komfortu ponieważ <xref:System.Windows.Forms.TabPage.Text%2A> właściwość <xref:System.Windows.Forms.TabPage> obiektu nie jest wyświetlane w karcie po włączeniu funkcji stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="2605b-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="2605b-105">Istnieje również ma bezpośredniego sposobu, aby kontrolować kierunek tekstu na karcie. Możesz użyć właściciela rysować na <xref:System.Windows.Forms.TabControl> się udoskonalić to środowisko pracy.</span><span class="sxs-lookup"><span data-stu-id="2605b-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="2605b-106">Poniższa procedura przedstawia sposób renderowania kart wyrównany do prawej, z tekstem kartę uruchomione od lewej do prawej, korzystając z funkcji "draw właściciela".</span><span class="sxs-lookup"><span data-stu-id="2605b-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="2605b-107">Aby wyświetlić karty wyrównany do prawej</span><span class="sxs-lookup"><span data-stu-id="2605b-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="2605b-108">Dodaj <xref:System.Windows.Forms.TabControl> do formularza.</span><span class="sxs-lookup"><span data-stu-id="2605b-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="2605b-109">Ustaw <xref:System.Windows.Forms.TabControl.Alignment%2A> właściwość <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="2605b-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="2605b-110">Ustaw <xref:System.Windows.Forms.TabControl.SizeMode%2A> właściwości <xref:System.Windows.Forms.TabSizeMode.Fixed>, dzięki czemu wszystkie karty są taką samą szerokość.</span><span class="sxs-lookup"><span data-stu-id="2605b-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="2605b-111">Ustaw <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwość preferowany ustalony rozmiar dla karty.</span><span class="sxs-lookup"><span data-stu-id="2605b-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="2605b-112">Należy pamiętać, że <xref:System.Windows.Forms.TabControl.ItemSize%2A> właściwość zachowuje się tak, jakby karty znajdowały się na górze, chociaż są wyrównane do prawej.</span><span class="sxs-lookup"><span data-stu-id="2605b-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="2605b-113">W rezultacie, w celu szerszego karty, należy zmienić <xref:System.Drawing.Size.Height%2A> właściwości, aby były wyższe, musisz zmienić <xref:System.Drawing.Size.Width%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2605b-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="2605b-114">Najlepsze wyniki w poniższym przykładzie kodu, można ustawić <xref:System.Drawing.Size.Width%2A> kart do 25 i <xref:System.Drawing.Size.Height%2A> do 100.</span><span class="sxs-lookup"><span data-stu-id="2605b-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="2605b-115">Ustaw <xref:System.Windows.Forms.TabControl.DrawMode%2A> właściwość <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="2605b-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="2605b-116">Definiowanie procedury obsługi dla <xref:System.Windows.Forms.TabControl.DrawItem> zdarzenia <xref:System.Windows.Forms.TabControl> , powoduje wyświetlenie tekstu od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="2605b-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2605b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2605b-117">See also</span></span>
- [<span data-ttu-id="2605b-118">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="2605b-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
