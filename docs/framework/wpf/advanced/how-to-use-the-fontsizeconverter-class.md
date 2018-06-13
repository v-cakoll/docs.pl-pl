---
title: Jak użyć klasy FontSizeConverter
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545129"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="cea5d-102">Jak użyć klasy FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="cea5d-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="cea5d-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="cea5d-103">Example</span></span>  
 <span data-ttu-id="cea5d-104">W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i użyj go, aby zmienić rozmiar czcionki.</span><span class="sxs-lookup"><span data-stu-id="cea5d-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="cea5d-105">W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, aby wystąpienie <xref:System.Double>lub nowszy w <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cea5d-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="cea5d-106">Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="cea5d-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="cea5d-107">Ta wartość jest następnie przekazywany z powrotem jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="cea5d-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="cea5d-108">W tym przykładzie zdefiniowano także drugi niestandardowej metody, która jest wywoływana `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="cea5d-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="cea5d-109">Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="cea5d-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="cea5d-110">W tym przykładzie nie działa.</span><span class="sxs-lookup"><span data-stu-id="cea5d-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cea5d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cea5d-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
