---
title: 'Instrukcje: Wyczyść powiązania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8bffc34864a2bf929bcbed09f16eac282e1ba2a5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360237"
---
# <a name="how-to-clear-bindings"></a>Instrukcje: Wyczyść powiązania
W tym przykładzie pokazano, jak wyczyścić powiązania z obiektu.  
  
## <a name="example"></a>Przykład  
 Aby wyczyścić powiązania z pojedynczej właściwości obiektu, wywołaj <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie. Poniższy przykład umożliwia usunięcie powiązania z <xref:System.Windows.Controls.TextBlock.TextProperty> z *kwerend*, <xref:System.Windows.Controls.TextBlock> obiektu.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Wyczyszczenie powiązanie powoduje usunięcie powiązania, dlatego, że wartość właściwości zależności jest zmieniana na dowolnie byłoby bez powiązania. Ta wartość może być wartość domyślną, odziedziczona wartość lub wartość z zakresu od powiązanie szablonu danych.  
  
 Aby wyczyścić powiązania ze wszystkich możliwych właściwości do obiektu, należy użyć <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.BindingOperations>
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
