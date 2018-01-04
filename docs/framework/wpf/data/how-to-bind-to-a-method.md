---
title: "Jak powiązać z metodą"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45f2a141b09c52085c13803b8d338fdc9eebf135
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="8bb6b-102">Jak powiązać z metodą</span><span class="sxs-lookup"><span data-stu-id="8bb6b-102">How to: Bind to a Method</span></span>
<span data-ttu-id="8bb6b-103">Poniższy przykład pokazuje, jak można powiązać je przy użyciu metody <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb6b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb6b-104">Example</span></span>  
 <span data-ttu-id="8bb6b-105">W tym przykładzie `TemperatureScale` jest klasa, która ma metodę `ConvertTemp`, który przyjmuje dwa parametry (jeden z `double` i jeden z `enum` typu `TempType)` i konwertuje jeden temperatury skali podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="8bb6b-106">W poniższym przykładzie <xref:System.Windows.Data.ObjectDataProvider> służy do tworzenia wystąpienia `TemperatureScale` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="8bb6b-107">`ConvertTemp` Metoda jest wywoływana z dwóch określonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="8bb6b-108">Teraz, że metoda jest dostępna jako zasób, można powiązać jej wyników.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="8bb6b-109">W poniższym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> są powiązane z dwa parametry metody.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="8bb6b-110">Umożliwia użytkownikom określanie temperatury do przekonwertowania i skali temperatury do przekonwertowania z.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="8bb6b-111">Należy pamiętać, że <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> ustawiono `true` ponieważ firma Microsoft powiązanie <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> właściwość <xref:System.Windows.Data.ObjectDataProvider> wystąpienie i nie właściwości obiektu opakowane przez <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` obiektu).</span><span class="sxs-lookup"><span data-stu-id="8bb6b-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="8bb6b-112"><xref:System.Windows.Controls.ContentControl.Content%2A> Ostatniego <xref:System.Windows.Controls.Label> aktualizuje, gdy użytkownik modyfikuje zawartość <xref:System.Windows.Controls.TextBox> lub wybór <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="8bb6b-113">Konwerter `DoubleToString` przyjmuje wartość o podwójnej precyzji i konwertuje go na ciąg w <xref:System.Windows.Data.IValueConverter.Convert%2A> kierunek (ze źródła powiązanie do powiązania obiektu docelowego, który jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwości) i konwertuje `string` do `double` w <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> kierunek.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="8bb6b-114">`InvalidationCharacterRule` Jest <xref:System.Windows.Controls.ValidationRule> kontrole nieprawidłowych znaków.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="8bb6b-115">Domyślny szablon błędów, który jest czerwonego obramowania wokół <xref:System.Windows.Controls.TextBox>, wydaje się powiadamianie użytkowników o wartość wejściowa nie jest wartość typu double.</span><span class="sxs-lookup"><span data-stu-id="8bb6b-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb6b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb6b-116">See Also</span></span>  
 [<span data-ttu-id="8bb6b-117">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8bb6b-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="8bb6b-118">Powiązywanie z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="8bb6b-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
