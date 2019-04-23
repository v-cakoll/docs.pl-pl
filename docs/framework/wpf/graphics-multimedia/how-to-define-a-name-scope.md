---
title: 'Instrukcje: Definiowanie zakresu nazw'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: a03f477dd31909e8cb9dde9cd29da6f38d665758
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086822"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="be682-102">Instrukcje: Definiowanie zakresu nazw</span><span class="sxs-lookup"><span data-stu-id="be682-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="be682-103">Aby animować z <xref:System.Windows.Media.Animation.Storyboard> w kodzie, należy utworzyć <xref:System.Windows.NameScope> i Zarejestruj nazwy obiektów docelowych przy użyciu elementu, który jest właścicielem tego zakresu nazw.</span><span class="sxs-lookup"><span data-stu-id="be682-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="be682-104">W poniższym przykładzie <xref:System.Windows.NameScope> jest tworzona dla `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="be682-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="be682-105">Dwa przyciski o `button1` i `button2`, są dodawane do panelu i ich nazwy zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="be682-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="be682-106">Kilku animacji i <xref:System.Windows.Media.Animation.Storyboard> są tworzone.</span><span class="sxs-lookup"><span data-stu-id="be682-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="be682-107">Scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody są używane do uruchamiania animacji.</span><span class="sxs-lookup"><span data-stu-id="be682-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="be682-108">Ponieważ `button1`, `button2`, i `myMainPanel` wszystkie mają ten sam zakres nazw, jednej z nich mogą być używane z <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę, aby uruchomić animacji.</span><span class="sxs-lookup"><span data-stu-id="be682-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be682-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="be682-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="be682-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be682-110">See also</span></span>

- [<span data-ttu-id="be682-111">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="be682-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="be682-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="be682-112">Animation Overview</span></span>](animation-overview.md)
