---
title: 'Instrukcje: Zarządzanie kolumnami i wierszami przy użyciu ColumnDefinitionsCollections i RowDefinitionsCollections'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: f316cced076223edba1d39c9cfb21b9a504b9eee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017673"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a><span data-ttu-id="a1294-102">Instrukcje: Zarządzanie kolumnami i wierszami przy użyciu ColumnDefinitionsCollections i RowDefinitionsCollections</span><span class="sxs-lookup"><span data-stu-id="a1294-102">How to: Manipulate Columns and Rows by Using ColumnDefinitionsCollections and RowDefinitionsCollections</span></span>
<span data-ttu-id="a1294-103">W tym przykładzie pokazano, jak używać metod w <xref:System.Windows.Controls.ColumnDefinitionCollection> i <xref:System.Windows.Controls.RowDefinitionCollection> klasy do wykonywania akcji, takich jak dodawanie, wyczyszczenia lub zliczanie zawartość wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="a1294-103">This example shows how to use the methods in the <xref:System.Windows.Controls.ColumnDefinitionCollection> and <xref:System.Windows.Controls.RowDefinitionCollection> classes to perform actions like adding, clearing, or counting the contents of rows or columns.</span></span> <span data-ttu-id="a1294-104">Można na przykład <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, lub <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> elementy, które są objęte <xref:System.Windows.Controls.ColumnDefinition> lub <xref:System.Windows.Controls.RowDefinition>.</span><span class="sxs-lookup"><span data-stu-id="a1294-104">For example, you can <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, or <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> the items that are included in a <xref:System.Windows.Controls.ColumnDefinition> or <xref:System.Windows.Controls.RowDefinition>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1294-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1294-105">Example</span></span>  
 <span data-ttu-id="a1294-106">Poniższy przykład tworzy <xref:System.Windows.Controls.Grid> element z <xref:System.Windows.FrameworkElement.Name%2A> z `grid1`.</span><span class="sxs-lookup"><span data-stu-id="a1294-106">The following example creates a <xref:System.Windows.Controls.Grid> element with a <xref:System.Windows.FrameworkElement.Name%2A> of `grid1`.</span></span> <span data-ttu-id="a1294-107"><xref:System.Windows.Controls.Grid> Zawiera <xref:System.Windows.Controls.StackPanel> przechowuje <xref:System.Windows.Controls.Button> elementów, każdy kontrolowane za pomocą metody innej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a1294-107">The <xref:System.Windows.Controls.Grid> contains a <xref:System.Windows.Controls.StackPanel> that holds <xref:System.Windows.Controls.Button> elements, each controlled by a different collection method.</span></span> <span data-ttu-id="a1294-108">Po kliknięciu <xref:System.Windows.Controls.Button>, zostaje uaktywniony wywołania metody w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="a1294-108">When you click a <xref:System.Windows.Controls.Button>, it activates a method call in the code-behind file.</span></span>  
  
 [!code-xaml[ColumnDefinitionsGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a1294-109">Ten przykład definiuje szereg metod niestandardowych każdej odpowiadającej <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="a1294-109">This example defines a series of custom methods, each corresponding to a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="a1294-110">Można zmienić liczbę wierszy i kolumn w <xref:System.Windows.Controls.Grid> na kilka sposobów, w tym dodawanie lub usuwanie wierszy i kolumn; i całkowitej liczby wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="a1294-110">You can change the number of columns and rows in the <xref:System.Windows.Controls.Grid> in several ways, which includes adding or removing rows and columns; and counting the total number of rows and columns.</span></span> <span data-ttu-id="a1294-111">Aby zapobiec <xref:System.ArgumentOutOfRangeException> i <xref:System.ArgumentException> wyjątki, możesz skorzystać z funkcji sprawdzania błędów, <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> zapewnia metody.</span><span class="sxs-lookup"><span data-stu-id="a1294-111">To prevent <xref:System.ArgumentOutOfRangeException> and <xref:System.ArgumentException> exceptions, you can use the error-checking functionality that the <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> method provides.</span></span>  
  
 [!code-csharp[ColumnDefinitionsGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a1294-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1294-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.ColumnDefinitionCollection>
- <xref:System.Windows.Controls.RowDefinitionCollection>
