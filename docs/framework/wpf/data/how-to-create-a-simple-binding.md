---
title: Jak utworzyć proste powiązanie
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="0ef05-102">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="0ef05-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="0ef05-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="0ef05-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef05-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ef05-104">Example</span></span>  
 <span data-ttu-id="0ef05-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="0ef05-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="0ef05-106">`Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="0ef05-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="0ef05-107">Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="0ef05-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="0ef05-108">Jest to wykonywane w `Resources` sekcji i przypisaniu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="0ef05-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="0ef05-109">Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> formant `PersonName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="0ef05-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="0ef05-110">W związku z tym <xref:System.Windows.Controls.TextBlock> pojawi się o wartości "Jan".</span><span class="sxs-lookup"><span data-stu-id="0ef05-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef05-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ef05-111">See Also</span></span>  
 [<span data-ttu-id="0ef05-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="0ef05-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0ef05-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0ef05-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
