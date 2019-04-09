---
title: 'Instrukcje: Tworzenie elementu StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: bcf6decff2fbc012b5f8b62794f0d7b2cd9f29fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121813"
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="d5bde-102">Instrukcje: Tworzenie elementu StackPanel</span><span class="sxs-lookup"><span data-stu-id="d5bde-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="d5bde-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="d5bde-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5bde-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5bde-104">Example</span></span>  
 <span data-ttu-id="d5bde-105">A <xref:System.Windows.Controls.StackPanel> pozwala na stosie elementów w określonym kierunku.</span><span class="sxs-lookup"><span data-stu-id="d5bde-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="d5bde-106">Za pomocą właściwości, które są zdefiniowane na <xref:System.Windows.Controls.StackPanel>, zawartość może przepływać zarówno w pionie, co jest ustawieniem domyślnym lub w poziomie.</span><span class="sxs-lookup"><span data-stu-id="d5bde-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="d5bde-107">Poniższy przykład pionowo stosów pięciu <xref:System.Windows.Controls.TextBlock> kontroluje, każdy z inną <xref:System.Windows.Controls.Border> i <xref:System.Windows.Controls.Border.Background%2A>, za pomocą <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="d5bde-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="d5bde-108">Elementy podrzędne, które nie istnieją określone <xref:System.Windows.FrameworkElement.Width%2A> Stretch Database w celu wypełnienia okna nadrzędnego; jednak elementy podrzędne, które mają określoną <xref:System.Windows.FrameworkElement.Width%2A>, jest wyśrodkowywana w oknie.</span><span class="sxs-lookup"><span data-stu-id="d5bde-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="d5bde-109">Domyślny kierunek stosu w <xref:System.Windows.Controls.StackPanel> pionowy.</span><span class="sxs-lookup"><span data-stu-id="d5bde-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="d5bde-110">Do zawartości przepływ sterowania w aplikacjach <xref:System.Windows.Controls.StackPanel>, użyj <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5bde-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="d5bde-111">Wyrównanie w poziomie można kontrolować za pomocą <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5bde-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5bde-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5bde-112">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="d5bde-113">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="d5bde-113">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="d5bde-114">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="d5bde-114">How-to Topics</span></span>](stackpanel-how-to-topics.md)
