---
title: 'Instrukcje: Tworzenie prostego powiązania'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931572"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="1d2ff-102">Instrukcje: Tworzenie prostego powiązania</span><span class="sxs-lookup"><span data-stu-id="1d2ff-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="1d2ff-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2ff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d2ff-104">Example</span></span>  
 <span data-ttu-id="1d2ff-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="1d2ff-106">`Person` Obiekt jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="1d2ff-107">Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="1d2ff-108">Jest to realizowane w `Resources` sekcji i przypisane `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="1d2ff-109">Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> kontrolę `PersonName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="1d2ff-110">W rezultacie <xref:System.Windows.Controls.TextBlock> pojawi się wartość "Jan".</span><span class="sxs-lookup"><span data-stu-id="1d2ff-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2ff-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d2ff-111">See also</span></span>

- [<span data-ttu-id="1d2ff-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="1d2ff-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="1d2ff-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1d2ff-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
