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
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="b7b62-102">Jak implementować logikę walidacji do obiektów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b7b62-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="b7b62-103">W tym przykładzie przedstawiono sposób implementowania logikę weryfikacji dla niestandardowego obiektu, a następnie powiązać.</span><span class="sxs-lookup"><span data-stu-id="b7b62-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7b62-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7b62-104">Example</span></span>  
 <span data-ttu-id="b7b62-105">Możesz podać logiki sprawdzania poprawności na warstwie business, jeśli implementuje obiektu źródłowego <xref:System.ComponentModel.IDataErrorInfo>, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b7b62-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="b7b62-106">W poniższym przykładzie właściwość text pola tekstowego wiąże `Age` właściwość `Person` obiektu, który został udostępniony dla powiązania za pomocą deklaracji zasobu, który znajduje się `x:Key``data`.</span><span class="sxs-lookup"><span data-stu-id="b7b62-106">In the following example, the text property of the text box binds to the `Age` property of the `Person` object, which has been made available for binding through a resource declaration that is given the `x:Key``data`.</span></span> <span data-ttu-id="b7b62-107"><xref:System.Windows.Controls.DataErrorValidationRule> Sprawdza, czy błędy sprawdzania poprawności zgłoszone przez <xref:System.ComponentModel.IDataErrorInfo> implementacji.</span><span class="sxs-lookup"><span data-stu-id="b7b62-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 <span data-ttu-id="b7b62-108">Możesz też zamiast <xref:System.Windows.Controls.DataErrorValidationRule>, można ustawić <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="b7b62-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b62-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7b62-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="b7b62-110">Implementowanie powiązanej walidacji</span><span class="sxs-lookup"><span data-stu-id="b7b62-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="b7b62-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="b7b62-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
