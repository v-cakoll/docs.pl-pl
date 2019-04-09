---
title: 'Instrukcje: Implementowanie logiki weryfikacji w obiektach niestandardowych'
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
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085925"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Instrukcje: Implementowanie logiki weryfikacji w obiektach niestandardowych
W tym przykładzie pokazano, jak można implementować logikę walidacji do obiektów niestandardowych, a następnie wiążą się do niego.  
  
## <a name="example"></a>Przykład  
 Można udostępniać logikę weryfikacji w warstwie biznesowej, jeśli obiekt źródłowy implementuje <xref:System.ComponentModel.IDataErrorInfo>, jak w poniższym przykładzie, który definiuje `Person` obiekt, który implementuje <xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 W poniższym przykładzie właściwość tekst pola tekstowego wiąże `Person.Age` właściwości, które zostały udostępnione dla powiązania za pomocą deklaracji zasobu, który znajduje się `x:Key` `data`. <xref:System.Windows.Controls.DataErrorValidationRule> Sprawdza, czy są wywoływane przez błędy sprawdzania poprawności <xref:System.ComponentModel.IDataErrorInfo> implementacji.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 Alternatywnie zamiast korzystać z <xref:System.Windows.Controls.DataErrorValidationRule>, można ustawić <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwość `true`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [Implementowanie weryfikacji wiązania](how-to-implement-binding-validation.md)
- [— Tematy porad](data-binding-how-to-topics.md)
