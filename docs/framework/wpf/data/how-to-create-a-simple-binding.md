---
title: 'Instrukcje: Utwórz proste powiązanie'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 3e38fa5fd1c7d0a635efd93de6ebe551f1eb1b82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594840"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="9956b-102">Instrukcje: Utwórz proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="9956b-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="9956b-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="9956b-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9956b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9956b-104">Example</span></span>  
 <span data-ttu-id="9956b-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="9956b-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="9956b-106">`Person` Obiekt jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="9956b-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="9956b-107">Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="9956b-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="9956b-108">Jest to realizowane w `Resources` sekcji i przypisane `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="9956b-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="9956b-109">Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> kontrolę `PersonName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9956b-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="9956b-110">W rezultacie <xref:System.Windows.Controls.TextBlock> pojawi się wartość "Jan".</span><span class="sxs-lookup"><span data-stu-id="9956b-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9956b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9956b-111">See also</span></span>
- [<span data-ttu-id="9956b-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="9956b-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9956b-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9956b-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
