---
title: 'Instrukcje: Tworzenie i używanie obiektu GridLengthConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 498d2b9c531f391f4cbeb1478469a99d381deec7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050990"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="755d5-102">Instrukcje: Tworzenie i używanie obiektu GridLengthConverter</span><span class="sxs-lookup"><span data-stu-id="755d5-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="755d5-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="755d5-103">Example</span></span>  
 <span data-ttu-id="755d5-104">Poniższy przykład pokazuje, jak utworzyć i używać wystąpienia <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="755d5-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="755d5-105">W przykładzie zdefiniowano niestandardową metodę o nazwie `changeCol`, które przechodzą <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.GridLengthConverter> konwertująca <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="755d5-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="755d5-106">Przekonwertowana wartości jest następnie przekazywany jako wartość <xref:System.Windows.Controls.ColumnDefinition.Width%2A> właściwość <xref:System.Windows.Controls.ColumnDefinition> elementu.</span><span class="sxs-lookup"><span data-stu-id="755d5-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="755d5-107">W przykładzie zdefiniowano też druga metoda niestandardowej o nazwie `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="755d5-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="755d5-108">Ta metoda niestandardowe konwertuje <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> do <xref:System.String> i przekazuje następnie, w których wartość z powrotem na <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="755d5-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="755d5-109">Należy pamiętać, że oddzielnego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik definiuje zawartość <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="755d5-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="755d5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="755d5-110">See also</span></span>

- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
