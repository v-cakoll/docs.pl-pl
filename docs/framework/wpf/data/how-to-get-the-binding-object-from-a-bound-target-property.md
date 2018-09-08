---
title: Jak pobrać obiekt wiążący z powiązanej własności docelowej
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7cebaf1077fb66420d77d656db32f444dd932b85
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210870"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Jak pobrać obiekt wiążący z powiązanej własności docelowej
W tym przykładzie pokazano, jak uzyskać obiekt wiążący z właściwością target powiązanych z danymi.  
  
## <a name="example"></a>Przykład  
 Można wykonać następujące polecenie, aby pobrać <xref:System.Windows.Data.Binding> obiektu:  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Należy określić właściwość zależności dla powiązania, który ma, ponieważ istnieje możliwość, że więcej niż jednej właściwości obiektu docelowego jest używanie powiązania danych.  
  
 Alternatywnie, możesz uzyskać <xref:System.Windows.Data.BindingExpression> , a następnie wartość <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> właściwości.  
  
 Aby uzyskać kompletny przykład zobacz [powiązania przykładowych weryfikacji](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Jeśli Twoje powiązanie <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Jeśli jest <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Jeśli masz pewności, czy właściwość docelowa jest powiązany, za pomocą <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, lub <xref:System.Windows.Data.PriorityBinding>, możesz użyć <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie powiązania w kodzie](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
