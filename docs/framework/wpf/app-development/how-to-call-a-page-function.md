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
ms.openlocfilehash: e7c7c5ef98feeb4c5557295d92a8b219d9799865
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364151"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="ec655-102">Instrukcje: Wywoływanie funkcji strony</span><span class="sxs-lookup"><span data-stu-id="ec655-102">How to: Call a Page Function</span></span>
<span data-ttu-id="ec655-103">Ten przykład pokazuje, jak wywołać funkcję strony ze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="ec655-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec655-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec655-104">Example</span></span>  
 <span data-ttu-id="ec655-105">Możesz przejść do funkcji strony przy użyciu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], tak jak podczas przechodzenia do strony.</span><span class="sxs-lookup"><span data-stu-id="ec655-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="ec655-106">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ec655-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="ec655-107">Jeśli musisz przekazać dane do funkcji Page, możesz utworzyć wystąpienie tego wystąpienia i przekazać dane przez ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="ec655-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="ec655-108">Lub, jak pokazano na poniższym przykładzie, można przekazać dane przy użyciu konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="ec655-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="ec655-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec655-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
