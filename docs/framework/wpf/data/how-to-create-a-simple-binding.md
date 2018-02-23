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
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="cdb7f-102">Jak utworzyć proste powiązanie</span><span class="sxs-lookup"><span data-stu-id="cdb7f-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="cdb7f-103">W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb7f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdb7f-104">Example</span></span>  
 <span data-ttu-id="cdb7f-105">W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="cdb7f-106">`Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="cdb7f-107">Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="cdb7f-108">Jest to wykonywane w `Resources` sekcji i przypisaniu `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="cdb7f-109">Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> formant `PersonName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="cdb7f-110">W związku z tym <xref:System.Windows.Controls.TextBlock> pojawi się o wartości "Jan".</span><span class="sxs-lookup"><span data-stu-id="cdb7f-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb7f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdb7f-111">See Also</span></span>  
 [<span data-ttu-id="cdb7f-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="cdb7f-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="cdb7f-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cdb7f-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
