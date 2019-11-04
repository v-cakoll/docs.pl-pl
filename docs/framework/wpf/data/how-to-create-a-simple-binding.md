---
title: Jak utworzyć proste powiązanie
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453510"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="58f43-102">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="58f43-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="58f43-103">Ten przykład pokazuje, jak utworzyć prostą <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="58f43-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f43-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="58f43-104">Example</span></span>  
 <span data-ttu-id="58f43-105">W tym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="58f43-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="58f43-106">Obiekt `Person` jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="58f43-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="58f43-107">Wyróżniony wiersz, który zawiera element `<src>` w poniższym przykładzie tworzy wystąpienie obiektu `Person` z wartością właściwości `PersonName` `Joe`.</span><span class="sxs-lookup"><span data-stu-id="58f43-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="58f43-108">Należy to zrobić w sekcji `Resources` i przypisać `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="58f43-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="58f43-109">Wyróżniony wiersz zawierający element `<TextBlock>` następnie wiąże formant <xref:System.Windows.Controls.TextBlock> z właściwością `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="58f43-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="58f43-110">W związku z tym <xref:System.Windows.Controls.TextBlock> pojawia się z wartością "Jan".</span><span class="sxs-lookup"><span data-stu-id="58f43-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f43-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58f43-111">See also</span></span>

- [<span data-ttu-id="58f43-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="58f43-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="58f43-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="58f43-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
