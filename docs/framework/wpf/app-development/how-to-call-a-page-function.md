---
title: 'Instrukcje: Wywoływanie funkcji strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: fb58d50a63cca41420aa102ca0c8b63f3b14c0d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980190"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="13db1-102">Instrukcje: Wywoływanie funkcji strony</span><span class="sxs-lookup"><span data-stu-id="13db1-102">How to: Call a Page Function</span></span>
<span data-ttu-id="13db1-103">W tym przykładzie pokazano, jak wywołać funkcję strony z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="13db1-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13db1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="13db1-104">Example</span></span>  
 <span data-ttu-id="13db1-105">Możesz przejść na stronę funkcji za pośrednictwem [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]tak samo, jak to możliwe po przejściu do strony.</span><span class="sxs-lookup"><span data-stu-id="13db1-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="13db1-106">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="13db1-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="13db1-107">Jeśli potrzebujesz przekazać dane do funkcji strony, można utworzyć jej wystąpienie i przekazać dane przez ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="13db1-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="13db1-108">Lub, jak pokazano na poniższym przykładzie, można przekazać dane przy użyciu innego niż domyślny konstruktor.</span><span class="sxs-lookup"><span data-stu-id="13db1-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="13db1-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13db1-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
