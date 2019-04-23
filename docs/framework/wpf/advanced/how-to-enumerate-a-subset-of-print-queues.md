---
title: 'Instrukcje: Wyliczanie podzbioru kolejek drukowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: adcfff0196bd0430ec1ae563fbd5489062de11f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217188"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="f86ee-102">Instrukcje: Wyliczanie podzbioru kolejek drukowania</span><span class="sxs-lookup"><span data-stu-id="f86ee-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="f86ee-103">Typowe sytuacji sterowaną przez specjalistów technologii informatycznych (IT), zarządzanie zbiór drukarek w firmie polega na generowaniu listę drukarek mające określoną wspólną charakterystykę.</span><span class="sxs-lookup"><span data-stu-id="f86ee-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="f86ee-104">Ta funkcjonalność jest dostarczana przez <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody <xref:System.Printing.PrintServer> obiektu i <xref:System.Printing.EnumeratedPrintQueueTypes> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f86ee-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f86ee-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f86ee-105">Example</span></span>  
 <span data-ttu-id="f86ee-106">W poniższym przykładzie na początku kodu, tworząc tablicę flagi określające właściwości kolejki wydruku, którą chcemy, aby wyświetlić listę.</span><span class="sxs-lookup"><span data-stu-id="f86ee-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="f86ee-107">W tym przykładzie firma Microsoft szuka kolejki wydruku, są instalowane lokalnie na serwerze wydruku, które są udostępniane.</span><span class="sxs-lookup"><span data-stu-id="f86ee-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="f86ee-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Wyliczenia zawiera wiele innych możliwości.</span><span class="sxs-lookup"><span data-stu-id="f86ee-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="f86ee-109">Następnie kod tworzy <xref:System.Printing.LocalPrintServer> obiektu z klasą pochodną <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="f86ee-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="f86ee-110">Lokalny serwer wydruku jest komputer, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f86ee-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="f86ee-111">Ostatnim krokiem znaczące służy do przekazywania macierzy <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f86ee-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="f86ee-112">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="f86ee-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="f86ee-113">W tym przykładzie można rozszerzyć przez `foreach` pętli, który przeprowadza użytkownika przez proces każdej kolejki wydruku do dalszego kontroli.</span><span class="sxs-lookup"><span data-stu-id="f86ee-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="f86ee-114">Na przykład użytkownik może sprawia, drukarki, które nie obsługują drukowania dwustronnego przez wywołanie pętli każdej kolejki wydruku <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody i testowania zwracanej wartości na obecność dupleksu.</span><span class="sxs-lookup"><span data-stu-id="f86ee-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86ee-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f86ee-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="f86ee-116">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="f86ee-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="f86ee-117">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="f86ee-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="f86ee-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="f86ee-118">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
