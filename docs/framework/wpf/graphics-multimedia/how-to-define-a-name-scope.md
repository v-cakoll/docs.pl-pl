---
title: Jak zdefiniować zakres nazw
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 689c8187fcf17ef48a73bc5a6fc4928f3be1a078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559718"
---
# <a name="how-to-define-a-name-scope"></a>Jak zdefiniować zakres nazw
Aby animować z <xref:System.Windows.Media.Animation.Storyboard> w kodzie, należy utworzyć <xref:System.Windows.NameScope> i zarejestrowanie nazwy obiektów docelowych za pomocą elementu będącego właścicielem tego zakresu nazw. W poniższym przykładzie <xref:System.Windows.NameScope> jest tworzona dla `myMainPanel`. Dwa przyciski `button1` i `button2`, są dodawane do panelu oraz ich nazwy zarejestrowane. Kilka animacji i <xref:System.Windows.Media.Animation.Storyboard> są tworzone. Scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody są używane do uruchamiania animacji.  
  
 Ponieważ `button1`, `button2`, i `myMainPanel` wszystkie mają tego samego zakresu nazw, jednego z nich może być używany z <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę, aby uruchomić animacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
