---
title: Jak zastąpić drzewo logiczne
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542893"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="06cf8-102">Jak zastąpić drzewo logiczne</span><span class="sxs-lookup"><span data-stu-id="06cf8-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="06cf8-103">Chociaż nie jest konieczne w większości przypadków, autorzy formantu zaawansowanego istnieje możliwość zastąpienia drzewa logicznego.</span><span class="sxs-lookup"><span data-stu-id="06cf8-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06cf8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="06cf8-104">Example</span></span>  
 <span data-ttu-id="06cf8-105">W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> do zastąpienia drzewo logiczne, w tym przypadku aby wymusić zachowanie czy panelu może mieć tylko i będzie renderować obraz tylko pojedynczym elemencie podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="06cf8-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="06cf8-106">To nie zawsze jest praktycznie pożądane zachowanie, ale podano tutaj jako środek pokazujący scenariusz dotyczący przesłonięcia elementu normalne drzewa logicznego.</span><span class="sxs-lookup"><span data-stu-id="06cf8-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="06cf8-107">Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="06cf8-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
