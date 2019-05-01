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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904153"
---
# <a name="how-to-define-a-name-scope"></a>Instrukcje: Definiowanie zakresu nazw
Aby animować z <xref:System.Windows.Media.Animation.Storyboard> w kodzie, należy utworzyć <xref:System.Windows.NameScope> i Zarejestruj nazwy obiektów docelowych przy użyciu elementu, który jest właścicielem tego zakresu nazw. W poniższym przykładzie <xref:System.Windows.NameScope> jest tworzona dla `myMainPanel`. Dwa przyciski o `button1` i `button2`, są dodawane do panelu i ich nazwy zarejestrowane. Kilku animacji i <xref:System.Windows.Media.Animation.Storyboard> są tworzone. Scenorysu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody są używane do uruchamiania animacji.  
  
 Ponieważ `button1`, `button2`, i `myMainPanel` wszystkie mają ten sam zakres nazw, jednej z nich mogą być używane z <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę, aby uruchomić animacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animacja — przegląd](animation-overview.md)
