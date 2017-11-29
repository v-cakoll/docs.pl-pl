---
title: "Jak usunąć moduł definiowania układów z elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe11dc8df1a29518ba05792877bd26670f96b29d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="639d2-102">Jak usunąć moduł definiowania układów z elementu</span><span class="sxs-lookup"><span data-stu-id="639d2-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="639d2-103">W tym przykładzie pokazano, jak programowane usuwanie określonego modułu definiowania układu kodu z określonej <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="639d2-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="639d2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="639d2-104">Example</span></span>  
 <span data-ttu-id="639d2-105">W tym przykładzie kodu usuwa pierwszego modułu definiowania układu kodu w tablicy definiowania układu zwrócony przez <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="639d2-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="639d2-106">W tym przykładzie stanie się pobrać modułu definiowania układu kodu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="639d2-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="639d2-107">Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nie ma takich modułów, `null` jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="639d2-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="639d2-108">Ten kod jawnie sprawdza tablicy o wartości null i jest najbardziej odpowiednie dla aplikacji, gdzie powinien być stosunkowo wspólnej tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="639d2-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="639d2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="639d2-109">Example</span></span>  
 <span data-ttu-id="639d2-110">W tym przykładzie kodu skrócone jest funkcjonalnym odpowiednikiem pełne przykładzie przedstawionym powyżej.</span><span class="sxs-lookup"><span data-stu-id="639d2-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="639d2-111">Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="639d2-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="639d2-112">Ten kod jest najbardziej odpowiednie dla aplikacji, gdzie powinien być rzadko tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="639d2-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="639d2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="639d2-113">See Also</span></span>  
 [<span data-ttu-id="639d2-114">Omówienie modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="639d2-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
