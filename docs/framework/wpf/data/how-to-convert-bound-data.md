---
title: "Jak konwertować powiązane dane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="32b05-102">Jak konwertować powiązane dane</span><span class="sxs-lookup"><span data-stu-id="32b05-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="32b05-103">Ten przykład przedstawia sposób stosowania konwersji danych, który jest używany w powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="32b05-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="32b05-104">Aby dokonać konwersji danych podczas tworzenia powiązania, należy utworzyć klasę implementującą <xref:System.Windows.Data.IValueConverter> interfejsu, który zawiera <xref:System.Windows.Data.IValueConverter.Convert%2A> i <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="32b05-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b05-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="32b05-105">Example</span></span>  
 <span data-ttu-id="32b05-106">W poniższym przykładzie przedstawiono implementacji konwertera daty, który konwertuje wartości typu date przekazano, tak aby pokazywane są tylko rok, miesiąc i dzień.</span><span class="sxs-lookup"><span data-stu-id="32b05-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="32b05-107">Podczas implementowania <xref:System.Windows.Data.IValueConverter> interfejsu, jest dobrym rozwiązaniem do dekoracji implementacji z <xref:System.Windows.Data.ValueConversionAttribute> atrybut do wskazania programowanie narzędzia typy danych objętego konwersji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="32b05-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="32b05-108">Po utworzeniu konwertera można dodać go jako zasób w Twojej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="32b05-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="32b05-109">W poniższym przykładzie *src* mapowania do przestrzeni nazw, w którym *DateConverter* jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="32b05-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="32b05-110">Ponadto można użyć konwertera w Twoje powiązanie, używając następującej składni.</span><span class="sxs-lookup"><span data-stu-id="32b05-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="32b05-111">W poniższym przykładzie, zawartość tekstu <xref:System.Windows.Controls.TextBlock> jest powiązany z *data_rozpoczęcia*, która jest właściwością zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="32b05-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="32b05-112">Zasoby stylu w powyższym przykładzie są definiowane w sekcji zasobów nie są wyświetlane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="32b05-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b05-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32b05-113">See Also</span></span>  
 [<span data-ttu-id="32b05-114">Implementowanie powiązanej walidacji</span><span class="sxs-lookup"><span data-stu-id="32b05-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="32b05-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="32b05-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="32b05-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="32b05-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
