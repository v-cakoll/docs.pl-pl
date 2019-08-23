---
title: 'Instrukcje: Pobieranie obiektu wiążącego z powiązanej własności docelowej'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965433"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Instrukcje: Pobieranie obiektu wiążącego z powiązanej własności docelowej
Ten przykład pokazuje, jak uzyskać obiekt powiązania z właściwości docelowej powiązanej z danymi.  
  
## <a name="example"></a>Przykład  
 Aby pobrać obiekt, <xref:System.Windows.Data.Binding> można wykonać następujące czynności:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> Należy określić właściwość zależności dla powiązania, ponieważ jest możliwe, że więcej niż jedna właściwość obiektu docelowego używa powiązania danych.  
  
 Alternatywnie możesz uzyskać <xref:System.Windows.Data.BindingExpression> wartość <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> właściwości, a następnie ją pobrać.  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykładowe sprawdzanie poprawności powiązań](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
> Jeśli powiązanie to <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Jeśli jest <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Jeśli nie masz pewności, czy właściwość docelowa jest powiązana <xref:System.Windows.Data.Binding>przy użyciu <xref:System.Windows.Data.MultiBinding>, a lub <xref:System.Windows.Data.PriorityBinding>a, możesz użyć <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie powiązania w kodzie](how-to-create-a-binding-in-code.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
