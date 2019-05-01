---
title: 'Instrukcje: Usuwanie modułu definiowania układów z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 256dd6fa0117f88aec2ef6b60c6dcd4c33b57855
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770763"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="91d2b-102">Instrukcje: Usuwanie modułu definiowania układów z elementu</span><span class="sxs-lookup"><span data-stu-id="91d2b-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="91d2b-103">W tym przykładzie pokazano, jak programowo usunąć określonego modułu definiowania układu kodu z określonym <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="91d2b-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d2b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="91d2b-104">Example</span></span>  
 <span data-ttu-id="91d2b-105">Ten przykład kodu usuwa pierwszy moduł definiowania układu w tablica zwrócona przez moduły definiowania układu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="91d2b-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="91d2b-106">W tym przykładzie stanie się pobrać moduły definiowania układu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="91d2b-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="91d2b-107">Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> ma nie definiowania `null` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="91d2b-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="91d2b-108">Ten kod jawnie sprawdza, czy tablicy o wartości null i jest najbardziej odpowiednia dla aplikacji, których powinien być stosunkowo wspólnej tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="91d2b-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="91d2b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="91d2b-109">Example</span></span>  
 <span data-ttu-id="91d2b-110">Ten przykład kodu skróconego jest funkcjonalnym odpowiednikiem pełny przykład pokazany powyżej.</span><span class="sxs-lookup"><span data-stu-id="91d2b-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="91d2b-111">Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="91d2b-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="91d2b-112">Ten kod jest najbardziej odpowiednie dla aplikacji, których oczekuje się rzadko tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="91d2b-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="91d2b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91d2b-113">See also</span></span>

- [<span data-ttu-id="91d2b-114">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="91d2b-114">Adorners Overview</span></span>](adorners-overview.md)
