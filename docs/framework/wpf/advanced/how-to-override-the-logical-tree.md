---
title: 'Instrukcje: Zastąp drzewo logiczne'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375229"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="a00bd-102">Instrukcje: Zastąp drzewo logiczne</span><span class="sxs-lookup"><span data-stu-id="a00bd-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="a00bd-103">Chociaż nie jest wymagane w większości przypadków, autorzy zaawansowanych kontroli ma możliwość przesłanianie drzewa logicznego.</span><span class="sxs-lookup"><span data-stu-id="a00bd-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a00bd-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a00bd-104">Example</span></span>  
 <span data-ttu-id="a00bd-105">W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> w tym przypadku zastąpić drzewo logiczne, aby wymusić zachowanie, że zespół może mieć tylko i będzie renderować obraz tylko jeden typ elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a00bd-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="a00bd-106">To niekoniecznie praktycznie pożądane zachowania, ale jest pokazany tutaj jako środek pokazujący scenariusz zastępowanie elementu normalne drzewo logiczne.</span><span class="sxs-lookup"><span data-stu-id="a00bd-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="a00bd-107">Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a00bd-107">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>
