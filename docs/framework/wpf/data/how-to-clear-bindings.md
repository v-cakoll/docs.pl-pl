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
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458879"
---
# <a name="how-to-clear-bindings"></a>Jak wyczyścić powiązania
Ten przykład pokazuje, jak wyczyścić powiązania z obiektu.  
  
## <a name="example"></a>Przykład  
 Aby usunąć powiązanie z pojedynczej właściwości obiektu, wywołaj <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie. Poniższy przykład usuwa powiązanie z <xref:System.Windows.Controls.TextBlock.TextProperty> obiektu "<xref:System.Windows.Controls.TextBlock>".  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Wyczyszczenie powiązania usuwa powiązanie, tak aby wartość właściwości Dependency była zmieniana na niezależnie od powiązania. Ta wartość może być wartością domyślną, dziedziczona wartością lub wartością z powiązania szablonu danych.  
  
 Aby wyczyścić powiązania ze wszystkimi możliwymi właściwościami obiektu, użyj <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.BindingOperations>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
