---
title: 'Instrukcje: Używanie klasy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088187"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="6e767-102">Instrukcje: Używanie klasy FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="6e767-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="6e767-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e767-103">Example</span></span>  
 <span data-ttu-id="6e767-104">W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i przy jego użyciu, aby zmienić rozmiar czcionki.</span><span class="sxs-lookup"><span data-stu-id="6e767-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="6e767-105">W przykładzie zdefiniowano niestandardową metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w osobnym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku do wystąpienia <xref:System.Double>i nowsze w <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6e767-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="6e767-106">Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="6e767-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="6e767-107">Ta wartość jest następnie przekazywany jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="6e767-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="6e767-108">W tym przykładzie definiuje również druga metoda niestandardowej, która jest wywoływana `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="6e767-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="6e767-109">Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="6e767-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="6e767-110">W tym przykładzie nie działa.</span><span class="sxs-lookup"><span data-stu-id="6e767-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6e767-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e767-111">See also</span></span>

- <xref:System.Windows.FontSizeConverter>
