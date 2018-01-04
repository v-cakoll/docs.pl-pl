---
title: "Jak utworzyć proste powiązanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 108b532e3aea27571c8a3b1290d931e2b0769be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="cd793-102">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="cd793-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="cd793-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="cd793-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd793-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd793-104">Example</span></span>  
 <span data-ttu-id="cd793-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="cd793-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="cd793-106">`Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="cd793-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="cd793-107">Poniższy przykład tworzy `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="cd793-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="cd793-108">Jest to wykonywane w `Resources` sekcji i przypisaniu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="cd793-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xaml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 <span data-ttu-id="cd793-109">Aby powiązać `PersonName` właściwość, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cd793-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="cd793-110">W związku z tym <xref:System.Windows.Controls.TextBlock> pojawi się o wartości "Jan".</span><span class="sxs-lookup"><span data-stu-id="cd793-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd793-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd793-111">See Also</span></span>  
 [<span data-ttu-id="cd793-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="cd793-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="cd793-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cd793-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
