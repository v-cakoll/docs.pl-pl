---
title: Jak utworzyć proste powiązanie
description: Utwórz proste powiązanie dla aplikacji za pomocą tego przykładu w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618704"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="73d13-103">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="73d13-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="73d13-104">Ten przykład pokazuje, jak utworzyć prostą <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="73d13-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73d13-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="73d13-105">Example</span></span>  
 <span data-ttu-id="73d13-106">W tym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="73d13-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="73d13-107">`Person`Obiekt jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="73d13-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="73d13-108">Wyróżniony wiersz, który zawiera `<src>` element w poniższym przykładzie tworzy wystąpienie `Person` obiektu z `PersonName` wartością właściwości `Joe` .</span><span class="sxs-lookup"><span data-stu-id="73d13-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="73d13-109">Jest to wykonywane w `Resources` sekcji i przypisane `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="73d13-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="73d13-110">Wyróżniony wiersz, który zawiera `<TextBlock>` element, następnie wiąże <xref:System.Windows.Controls.TextBlock> formant z `PersonName` właściwością.</span><span class="sxs-lookup"><span data-stu-id="73d13-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="73d13-111">W rezultacie <xref:System.Windows.Controls.TextBlock> pojawia się wartość "Jan".</span><span class="sxs-lookup"><span data-stu-id="73d13-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d13-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73d13-112">See also</span></span>

- [<span data-ttu-id="73d13-113">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="73d13-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="73d13-114">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="73d13-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
