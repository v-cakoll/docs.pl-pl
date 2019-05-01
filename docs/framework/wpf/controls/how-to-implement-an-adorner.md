---
title: 'Instrukcje: Implementowanie modułu definiowania układu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: da318fee42b4628351217774de2a2225cfb21ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770984"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="6a3ae-102">Instrukcje: Implementowanie modułu definiowania układu</span><span class="sxs-lookup"><span data-stu-id="6a3ae-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="6a3ae-103">Ten przykład pokazuje implementację minimalny moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="6a3ae-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="6a3ae-104">Uwagi dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="6a3ae-104">Notes for Implementers</span></span>  
 <span data-ttu-id="6a3ae-105">Ważne jest, aby należy pamiętać, moduły definiowania układu nie ma żadnych zachowań nieprzerwaną pracę renderowania; zapewnienie, że moduł definiowania układu renderuje spoczywa implementujący moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="6a3ae-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="6a3ae-106">Często stosowaną metodą wdrażania zachowanie renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i używać co najmniej jednej <xref:System.Windows.Media.DrawingContext> obiekty do renderowania moduł definiowania układu wizualizacji, zgodnie z potrzebami (jak pokazano w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="6a3ae-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a3ae-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a3ae-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6a3ae-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6a3ae-108">Description</span></span>  
 <span data-ttu-id="6a3ae-109">Niestandardowy moduł definiowania układu, w której jest tworzona poprzez implementację klasy, która dziedziczy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a3ae-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="6a3ae-110">Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> przy użyciu kółka przez zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6a3ae-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6a3ae-111">Kod</span><span class="sxs-lookup"><span data-stu-id="6a3ae-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="6a3ae-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a3ae-112">See also</span></span>

- [<span data-ttu-id="6a3ae-113">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="6a3ae-113">Adorners Overview</span></span>](adorners-overview.md)
