---
title: "Jak utworzyć proste powiązanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73ed25406aa398aa35c275b20da1deee48b119ab
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="aad9a-102">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="aad9a-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="aad9a-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad9a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aad9a-104">Example</span></span>  
 <span data-ttu-id="aad9a-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="aad9a-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="aad9a-106">`Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="aad9a-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="aad9a-107">Poniższy przykład tworzy `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="aad9a-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="aad9a-108">Jest to wykonywane w `Resources` sekcji i przypisaniu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="aad9a-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml)]  
  
 <span data-ttu-id="aad9a-109">Aby powiązać `PersonName` właściwość, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="aad9a-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="aad9a-110">W związku z tym <xref:System.Windows.Controls.TextBlock> pojawi się o wartości "Jan".</span><span class="sxs-lookup"><span data-stu-id="aad9a-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad9a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aad9a-111">See Also</span></span>  
 [<span data-ttu-id="aad9a-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="aad9a-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="aad9a-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="aad9a-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
