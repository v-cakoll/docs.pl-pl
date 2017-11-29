---
title: "Jak wykazać podzbiór kolejek drukowania"
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
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 393d1692526551b1eb9aa16f48d3c78c3cd6692f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="77a33-102">Jak wykazać podzbiór kolejek drukowania</span><span class="sxs-lookup"><span data-stu-id="77a33-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="77a33-103">Typowe sytuacji przez specjalistów technologii informatycznych (IT) Zarządzanie zbiór drukarki w firmie, które muszą ponieść polega na generowaniu listę drukarek posiadające niektórych właściwości.</span><span class="sxs-lookup"><span data-stu-id="77a33-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="77a33-104">Ta funkcja jest zapewniana przez <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody <xref:System.Printing.PrintServer> obiektu i <xref:System.Printing.EnumeratedPrintQueueTypes> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="77a33-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77a33-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="77a33-105">Example</span></span>  
 <span data-ttu-id="77a33-106">W poniższym przykładzie kodu rozpoczyna się od utworzenia tablicy flagi określające właściwości kolejki wydruku, którą chcemy, aby wyświetlić listę.</span><span class="sxs-lookup"><span data-stu-id="77a33-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="77a33-107">W tym przykładzie czekamy dla kolejek drukowania, które są instalowane lokalnie na serwerze wydruku i są współdzielone.</span><span class="sxs-lookup"><span data-stu-id="77a33-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="77a33-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Wyliczenie zawiera wiele innych możliwości.</span><span class="sxs-lookup"><span data-stu-id="77a33-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="77a33-109">Następnie tworzony <xref:System.Printing.LocalPrintServer> obiektu, klasą pochodną <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="77a33-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="77a33-110">Lokalny serwer wydruku jest komputer, na którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="77a33-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="77a33-111">Ostatni krok istotne jest przekazanie tablicy, tak aby <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77a33-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="77a33-112">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="77a33-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="77a33-113">W tym przykładzie można rozszerzyć przez `foreach` pętli, które kroki do każdej kolejki wydruku przeprowadzić dalszą kontroli.</span><span class="sxs-lookup"><span data-stu-id="77a33-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="77a33-114">Na przykład użytkownik może odfiltrowania drukarki, które nie obsługują drukowania dwustronnego przez wywołanie pętli każdej kolejki wydruku <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> — metoda i testowania zwrócona wartość obecność dupleksu.</span><span class="sxs-lookup"><span data-stu-id="77a33-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a33-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77a33-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="77a33-116">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="77a33-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="77a33-117">Omówienie drukowania</span><span class="sxs-lookup"><span data-stu-id="77a33-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="77a33-118">Moduł zapisywania dokumentów XPS firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="77a33-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
