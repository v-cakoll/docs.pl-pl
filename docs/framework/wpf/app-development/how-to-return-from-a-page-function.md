---
title: 'Instrukcje: Wróć z funkcji strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- returning from page functions [WPF]
- page functions [WPF], returning from
- functions [WPF], returning from
ms.assetid: 87804905-7e8f-417b-b0e3-5622da686396
ms.openlocfilehash: 60e1d9d96104a9f4160280ba7208b7fe3680c1c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361047"
---
# <a name="how-to-return-from-a-page-function"></a><span data-ttu-id="9b5a3-102">Instrukcje: Wróć z funkcji strony</span><span class="sxs-lookup"><span data-stu-id="9b5a3-102">How to: Return from a Page Function</span></span>
<span data-ttu-id="9b5a3-103">Ten przykład przedstawia sposób zwrócenia wyniku z funkcji strony.</span><span class="sxs-lookup"><span data-stu-id="9b5a3-103">This example shows how to return a result from a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b5a3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b5a3-104">Example</span></span>  
 <span data-ttu-id="9b5a3-105">Aby wrócić z funkcji strony, należy wywołać <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> i przekaż wystąpienie <xref:System.Windows.Navigation.ReturnEventArgs%601>.</span><span class="sxs-lookup"><span data-stu-id="9b5a3-105">To return from a page function, you need to call <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> and pass an instance of <xref:System.Windows.Navigation.ReturnEventArgs%601>.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml1)]  
[!code-xaml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml2)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml.cs#pagefunctionreturnaresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/GetStringPageFunction.xaml.vb#pagefunctionreturnaresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="9b5a3-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b5a3-106">See also</span></span>
- <xref:System.Windows.Navigation.PageFunction%601>
