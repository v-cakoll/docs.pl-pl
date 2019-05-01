---
title: 'Instrukcje: Konwertowanie powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020936"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="0b64b-102">Instrukcje: Konwertowanie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="0b64b-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="0b64b-103">Ten przykład przedstawia sposób zastosowania konwersji na dane, które jest używane w powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="0b64b-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="0b64b-104">Aby dokonać konwersji danych podczas tworzenia powiązania, należy utworzyć klasę, która implementuje <xref:System.Windows.Data.IValueConverter> interfejsu, który zawiera <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0b64b-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b64b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b64b-105">Example</span></span>  
 <span data-ttu-id="0b64b-106">Poniższy przykład pokazuje implementację konwerter daty, która konwertuje wartość daty przekazanej tak, aby pokazywał tylko rok, miesiąc i dzień.</span><span class="sxs-lookup"><span data-stu-id="0b64b-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="0b64b-107">Podczas implementowania <xref:System.Windows.Data.IValueConverter> interfejsu, jest dobrym rozwiązaniem do dekorowania implementacji przy użyciu <xref:System.Windows.Data.ValueConversionAttribute> atrybutu, aby wskazać programowania narzędzi typy danych związane z konwersją, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0b64b-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="0b64b-108">Po utworzeniu konwertera można dodać go jako zasób w swojej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="0b64b-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="0b64b-109">W poniższym przykładzie *src* mapuje do przestrzeni nazw, w którym *DateConverter* jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="0b64b-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="0b64b-110">Na koniec konwertera można używać w Twoje powiązanie, używając następującej składni.</span><span class="sxs-lookup"><span data-stu-id="0b64b-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="0b64b-111">W poniższym przykładzie, zawartość tekstu <xref:System.Windows.Controls.TextBlock> jest powiązany z *StartDate*, który jest właściwością zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0b64b-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="0b64b-112">Zasoby stylów, do których odwołuje się w powyższym przykładzie są zdefiniowane w sekcji zasobów nie są wyświetlane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="0b64b-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b64b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b64b-113">See also</span></span>

- [<span data-ttu-id="0b64b-114">Implementowanie powiązanej walidacji</span><span class="sxs-lookup"><span data-stu-id="0b64b-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="0b64b-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="0b64b-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="0b64b-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0b64b-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
