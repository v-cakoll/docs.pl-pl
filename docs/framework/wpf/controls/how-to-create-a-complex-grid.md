---
title: Jak utworzyć siatkę złożoną
description: Przykład o tym, jak można użyć formantu siatki, aby utworzyć układ, który wygląda jak kalendarza miesięcznego.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: dd17dfeea85e2b404f7a284f93faceec63145b1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911001"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="6cff9-103">Jak utworzyć siatkę złożoną</span><span class="sxs-lookup"><span data-stu-id="6cff9-103">How to create a complex Grid</span></span>

<span data-ttu-id="6cff9-104">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.Grid> formantu, aby utworzyć układ, który wygląda jak kalendarza miesięcznego.</span><span class="sxs-lookup"><span data-stu-id="6cff9-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="6cff9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cff9-105">Example</span></span>

<span data-ttu-id="6cff9-106">W poniższym przykładzie zdefiniowano osiem wierszy i kolumn osiem przy użyciu <xref:System.Windows.Controls.RowDefinition> i <xref:System.Windows.Controls.ColumnDefinition> klasy.</span><span class="sxs-lookup"><span data-stu-id="6cff9-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="6cff9-107">Używa ona <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> dołączonych właściwości, wraz z <xref:System.Windows.Shapes.Rectangle> elementy, które wypełnienia tła różnych kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="6cff9-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="6cff9-108">Ten projekt jest możliwe, ponieważ więcej niż jeden element może znajdować się w każdej komórki w <xref:System.Windows.Controls.Grid>, główna różnica między <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="6cff9-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="6cff9-109">W przykładzie użyto pionowy gradientów do <xref:System.Windows.Shapes.Shape.Fill%2A> kolumny i wiersze do poprawy wizualnej prezentacji i czytelności kalendarza.</span><span class="sxs-lookup"><span data-stu-id="6cff9-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="6cff9-110">Różne <xref:System.Windows.Controls.TextBlock> elementy reprezentują dat i dni tygodnia.</span><span class="sxs-lookup"><span data-stu-id="6cff9-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="6cff9-111"><xref:System.Windows.Controls.TextBlock> elementy są pozycjonowane absolutnie w komórkach ich za pomocą <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i właściwości wyrównanie, które są zdefiniowane w stylu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cff9-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="6cff9-112">Na poniższej ilustracji przedstawiono wynikowy formant kalendarza można dostosowywać:</span><span class="sxs-lookup"><span data-stu-id="6cff9-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Zrzut ekranu przedstawiający wynikowy formant](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="6cff9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cff9-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="6cff9-115">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="6cff9-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="6cff9-116">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="6cff9-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="6cff9-117">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="6cff9-117">Table Overview</span></span>](../advanced/table-overview.md)