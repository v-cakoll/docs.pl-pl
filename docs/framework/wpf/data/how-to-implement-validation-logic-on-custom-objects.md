---
title: Jak implementować logikę walidacji do obiektów niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Jak implementować logikę walidacji do obiektów niestandardowych
W tym przykładzie przedstawiono sposób implementowania logikę weryfikacji dla niestandardowego obiektu, a następnie powiązać.  
  
## <a name="example"></a>Przykład  
 Możesz podać logiki sprawdzania poprawności na warstwie business, jeśli implementuje obiektu źródłowego <xref:System.ComponentModel.IDataErrorInfo>, jak w poniższym przykładzie:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 W poniższym przykładzie właściwość text pola tekstowego wiąże `Age` właściwość `Person` obiektu, który został udostępniony dla powiązania za pomocą deklaracji zasobu, który znajduje się `x:Key``data`. <xref:System.Windows.Controls.DataErrorValidationRule> Sprawdza, czy błędy sprawdzania poprawności zgłoszone przez <xref:System.ComponentModel.IDataErrorInfo> implementacji.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 Możesz też zamiast <xref:System.Windows.Controls.DataErrorValidationRule>, można ustawić <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwości `true`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [Implementowanie powiązanej walidacji](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
