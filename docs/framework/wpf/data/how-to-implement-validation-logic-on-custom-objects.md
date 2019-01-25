---
title: 'Instrukcje: Implementuj logikę walidacji do obiektów niestandardowych'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: e2b77ef65c92ae596c5620c9122dcf3db0bf9462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525992"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Instrukcje: Implementuj logikę walidacji do obiektów niestandardowych
W tym przykładzie pokazano, jak można implementować logikę walidacji do obiektów niestandardowych, a następnie wiążą się do niego.  
  
## <a name="example"></a>Przykład  
 Można udostępniać logikę weryfikacji w warstwie biznesowej, jeśli obiekt źródłowy implementuje <xref:System.ComponentModel.IDataErrorInfo>, jak w poniższym przykładzie, który definiuje `Person` obiekt, który implementuje <xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 W poniższym przykładzie właściwość tekst pola tekstowego wiąże `Person.Age` właściwości, które zostały udostępnione dla powiązania za pomocą deklaracji zasobu, który znajduje się `x:Key` `data`. <xref:System.Windows.Controls.DataErrorValidationRule> Sprawdza, czy są wywoływane przez błędy sprawdzania poprawności <xref:System.ComponentModel.IDataErrorInfo> implementacji.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 Alternatywnie zamiast korzystać z <xref:System.Windows.Controls.DataErrorValidationRule>, można ustawić <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwość `true`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ExceptionValidationRule>
- [Implementowanie powiązanej walidacji](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
