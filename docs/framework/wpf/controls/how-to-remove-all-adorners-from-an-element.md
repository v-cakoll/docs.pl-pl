---
title: 'Instrukcje: Usuń wszystkie moduły definiowania układów z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 6b2b1832898a847f54f11cca26ecd50dbd7285ff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374170"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="3d7a0-102">Instrukcje: Usuń wszystkie moduły definiowania układów z elementu</span><span class="sxs-lookup"><span data-stu-id="3d7a0-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="3d7a0-103">W tym przykładzie pokazano, jak programowo usunąć wszystkie moduły definiowania układów z określonym <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d7a0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d7a0-104">Example</span></span>  
 <span data-ttu-id="3d7a0-105">Ten przykład kodu usuwa wszystkie moduły definiowania układu w tablica zwrócona przez moduły definiowania układu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="3d7a0-106">W tym przykładzie stanie się pobrać moduły definiowania układu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="3d7a0-107">Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> ma nie definiowania `null` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="3d7a0-108">Ten kod jawnie sprawdza, czy tablicy o wartości null i jest najbardziej odpowiednia dla aplikacji, których powinien być stosunkowo wspólnej tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="3d7a0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d7a0-109">Example</span></span>  
 <span data-ttu-id="3d7a0-110">Ten przykład kodu skróconego jest funkcjonalnym odpowiednikiem pełny przykład pokazany powyżej.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="3d7a0-111">Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="3d7a0-112">Ten kod jest najbardziej odpowiednie dla aplikacji, których oczekuje się rzadko tablicy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="3d7a0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d7a0-113">See also</span></span>
- [<span data-ttu-id="3d7a0-114">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="3d7a0-114">Adorners Overview</span></span>](adorners-overview.md)
