---
title: 'Instrukcje: Uzyskaj wartość w oparciu o listę powiązanych elementów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: 77c832c1460749ced58e7a20af333c5ed9dd1555
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368128"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="ecec6-102">Instrukcje: Uzyskaj wartość w oparciu o listę powiązanych elementów</span><span class="sxs-lookup"><span data-stu-id="ecec6-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="ecec6-103"><xref:System.Windows.Data.MultiBinding> Umożliwia powiązanie właściwość target powiązania do listy właściwości źródła, a następnie stosuje logikę w celu utworzenia wartości danego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ecec6-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="ecec6-104">W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="ecec6-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecec6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecec6-105">Example</span></span>  
 <span data-ttu-id="ecec6-106">W poniższym przykładzie `NameListData` odwołuje się do kolekcji `PersonName` obiektów, które są obiektami, które zawierają dwie właściwości, `firstName` i `lastName`.</span><span class="sxs-lookup"><span data-stu-id="ecec6-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="ecec6-107">Poniższy przykład tworzy <xref:System.Windows.Controls.TextBlock> imiona i nazwiska osoby o nazwisku przedstawiająca pierwszy.</span><span class="sxs-lookup"><span data-stu-id="ecec6-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="ecec6-108">Aby dowiedzieć się, jak jest generowany format ostatnia nazwa pierwszego, Przyjrzyjmy się na implementacji `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="ecec6-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="ecec6-109">`NameConverter` implementuje <xref:System.Windows.Data.IMultiValueConverter> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ecec6-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="ecec6-110">`NameConverter` przyjmuje wartości od poszczególnych powiązania i przechowuje je w tablicy obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="ecec6-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="ecec6-111">Kolejność, w której <xref:System.Windows.Data.Binding> elementy są wyświetlane w obszarze <xref:System.Windows.Data.MultiBinding> element polega na kolejności, w której te wartości są przechowywane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ecec6-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="ecec6-112">Wartość <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atrybut odwołuje się do niej argumentu parametru <xref:System.Windows.Data.MultiBinding.Converter%2A> metody, która wykonuje przełącznikiem parametru do określenia, jak format nazwy.</span><span class="sxs-lookup"><span data-stu-id="ecec6-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecec6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecec6-113">See also</span></span>
- [<span data-ttu-id="ecec6-114">Konwertowanie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="ecec6-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="ecec6-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="ecec6-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="ecec6-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ecec6-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
