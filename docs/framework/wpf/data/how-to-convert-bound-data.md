---
title: Jak konwertować powiązane dane
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458856"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="3d074-102">Jak konwertować powiązane dane</span><span class="sxs-lookup"><span data-stu-id="3d074-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="3d074-103">Ten przykład pokazuje, jak zastosować konwersję do danych, które są używane w powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="3d074-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="3d074-104">Aby przekonwertować dane podczas wiązania, należy utworzyć klasę, która implementuje interfejs <xref:System.Windows.Data.IValueConverter>, który obejmuje metody <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d074-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d074-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d074-105">Example</span></span>  
 <span data-ttu-id="3d074-106">W poniższym przykładzie przedstawiono implementację konwertera daty, który konwertuje przekazaną wartość daty, aby wyświetlić tylko rok, miesiąc i dzień.</span><span class="sxs-lookup"><span data-stu-id="3d074-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="3d074-107">Podczas implementowania interfejsu <xref:System.Windows.Data.IValueConverter>, dobrym sposobem jest dekorować implementacji z atrybutem <xref:System.Windows.Data.ValueConversionAttribute>, aby wskazać narzędziom programistycznym typy danych uwzględnione w konwersji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3d074-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="3d074-108">Po utworzeniu konwertera można go dodać jako zasób do pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d074-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="3d074-109">W poniższym przykładzie *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *DateConverter* .</span><span class="sxs-lookup"><span data-stu-id="3d074-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="3d074-110">Na koniec można użyć konwertera w powiązaniu przy użyciu następującej składni.</span><span class="sxs-lookup"><span data-stu-id="3d074-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="3d074-111">W poniższym przykładzie zawartość tekstowa <xref:System.Windows.Controls.TextBlock> jest powiązana z *StartDate*, która jest właściwością zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="3d074-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="3d074-112">Zasoby stylu, do których odwołuje się powyższy przykład, są zdefiniowane w sekcji zasobów, która nie jest pokazana w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="3d074-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d074-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d074-113">See also</span></span>

- [<span data-ttu-id="3d074-114">Implementowanie powiązanej walidacji</span><span class="sxs-lookup"><span data-stu-id="3d074-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="3d074-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="3d074-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3d074-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3d074-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
