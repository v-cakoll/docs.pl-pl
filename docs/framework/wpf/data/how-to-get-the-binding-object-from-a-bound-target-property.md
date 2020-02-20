---
title: Jak pobrać obiekt wiążący z powiązanej własności docelowej
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453055"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Jak pobrać obiekt wiążący z powiązanej własności docelowej
Ten przykład pokazuje, jak uzyskać obiekt powiązania z właściwości docelowej powiązanej z danymi.

## <a name="example"></a>Przykład
 Aby uzyskać <xref:System.Windows.Data.Binding> obiekt, można wykonać następujące czynności:

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Należy określić właściwość zależności dla powiązania, ponieważ jest możliwe, że więcej niż jedna właściwość obiektu docelowego używa powiązania danych.

 Alternatywnie możesz uzyskać <xref:System.Windows.Data.BindingExpression> a następnie pobrać wartość właściwości <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.

 Aby zapoznać się z kompletnym przykładem, zobacz [przykładowe sprawdzanie poprawności powiązań](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).

> [!NOTE]
> Jeśli powiązanie jest <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>. Jeśli jest to <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>. Jeśli nie masz pewności, czy właściwość docelowa jest powiązana przy użyciu <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>lub <xref:System.Windows.Data.PriorityBinding>, możesz użyć <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz też

- [Tworzenie powiązania w kodzie](how-to-create-a-binding-in-code.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
