---
title: Jak powiązać z wynikami zapytania LINQ
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d21ac5f366e001ea76d6eda64ed62583248796f6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454415"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="d5daa-102">Jak powiązać z wynikami zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="d5daa-102">How to: Bind to the Results of a LINQ Query</span></span>

<span data-ttu-id="d5daa-103">W tym przykładzie pokazano, jak uruchomić zapytanie LINQ, a następnie powiązać z wynikami.</span><span class="sxs-lookup"><span data-stu-id="d5daa-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>

## <a name="example"></a><span data-ttu-id="d5daa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5daa-104">Example</span></span>

<span data-ttu-id="d5daa-105">Poniższy przykład tworzy dwa pola listy.</span><span class="sxs-lookup"><span data-stu-id="d5daa-105">The following example creates two list boxes.</span></span> <span data-ttu-id="d5daa-106">Pierwsze pole listy zawiera trzy elementy listy.</span><span class="sxs-lookup"><span data-stu-id="d5daa-106">The first list box contains three list items.</span></span>

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

<span data-ttu-id="d5daa-107">Wybranie elementu z pierwszego pola listy powoduje wywołanie poniższego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5daa-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="d5daa-108">W tym przykładzie `Tasks` jest kolekcją obiektów `Task`.</span><span class="sxs-lookup"><span data-stu-id="d5daa-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="d5daa-109">Klasa `Task` ma właściwość o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="d5daa-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="d5daa-110">Ten program obsługi zdarzeń uruchamia zapytanie LINQ, które zwraca kolekcję `Task` obiektów, które mają wybraną wartość priorytetu, a następnie ustawia ten element jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="d5daa-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

<span data-ttu-id="d5daa-111">Drugie pole listy tworzy powiązanie z tą kolekcją, ponieważ jej wartość <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jest ustawiona na `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="d5daa-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="d5daa-112">W efekcie zostanie wyświetlona zwracana kolekcja (oparta na `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="d5daa-112">As a result, it displays the returned collection (based on the `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5daa-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5daa-113">See also</span></span>

- [<span data-ttu-id="d5daa-114">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="d5daa-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="d5daa-115">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="d5daa-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="d5daa-116">Nowości w WPF w wersji 4.5</span><span class="sxs-lookup"><span data-stu-id="d5daa-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="d5daa-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5daa-117">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
