---
title: Jak wyczyścić powiązania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: f66477fc857a9e7a065e01b8cddf43789042b59c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555860"
---
# <a name="how-to-clear-bindings"></a>Jak wyczyścić powiązania
W tym przykładzie pokazano, jak można wyczyścić powiązania z obiektu.  
  
## <a name="example"></a>Przykład  
 Aby usunąć powiązanie z poszczególnych właściwości w obiekcie, należy wywołać <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie. Poniższy przykład umożliwia usunięcie powiązania z <xref:System.Windows.Controls.TextBlock.TextProperty> z *tekst*, <xref:System.Windows.Controls.TextBlock> obiektu.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Wyczyszczenie powiązania usuwa powiązanie tak, aby wartość właściwości zależności jest zmieniana na dowolnym byłoby bez powiązania. Ta wartość może być wartość domyślną, dziedziczona wartość lub wartość z zakresu od powiązanie szablonu danych.  
  
 Aby wyczyścić wiązania ze wszystkich możliwych właściwości w obiekcie, należy użyć <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.BindingOperations>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
