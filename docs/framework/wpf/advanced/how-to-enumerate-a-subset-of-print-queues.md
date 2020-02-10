---
title: Jak wykazać podzbiór kolejek drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094543"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="1d067-102">Jak wykazać podzbiór kolejek drukowania</span><span class="sxs-lookup"><span data-stu-id="1d067-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="1d067-103">Powszechną sytuacją, jaką specjaliści z technologią informatyczną (IT) do zarządzania zestawem drukarek w całej firmie jest generowanie listy drukarek mających pewne cechy.</span><span class="sxs-lookup"><span data-stu-id="1d067-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="1d067-104">Ta funkcja jest udostępniana przez metodę <xref:System.Printing.PrintServer.GetPrintQueues%2A> obiektu <xref:System.Printing.PrintServer> i wyliczenia <xref:System.Printing.EnumeratedPrintQueueTypes>.</span><span class="sxs-lookup"><span data-stu-id="1d067-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d067-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d067-105">Example</span></span>  
 <span data-ttu-id="1d067-106">W poniższym przykładzie kod rozpoczyna się od utworzenia tablicy flag, które określają charakterystyki kolejek wydruku, które chcemy wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="1d067-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="1d067-107">W tym przykładzie szukasz kolejek wydruku zainstalowanych lokalnie na serwerze wydruku i są one udostępnione.</span><span class="sxs-lookup"><span data-stu-id="1d067-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="1d067-108">Wyliczenie <xref:System.Printing.EnumeratedPrintQueueTypes> zapewnia wiele innych możliwości.</span><span class="sxs-lookup"><span data-stu-id="1d067-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="1d067-109">Następnie kod tworzy obiekt <xref:System.Printing.LocalPrintServer>, klasy pochodnej z <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="1d067-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="1d067-110">Lokalny serwer wydruku to komputer, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="1d067-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="1d067-111">Ostatni znaczący krok polega na przejściu tablicy do metody <xref:System.Printing.PrintServer.GetPrintQueues%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d067-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="1d067-112">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="1d067-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="1d067-113">Możesz rozszerzyć ten przykład, wykonując pętlę `foreach`, która przechodzi przez każdą kolejkę wydruku w celu dalszej kontroli.</span><span class="sxs-lookup"><span data-stu-id="1d067-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="1d067-114">Na przykład można wypróbować drukarki, które nie obsługują drukowania dwustronnego, ponieważ pętla wywołuje każdą metodę <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> kolejki wydruku i testuje zwracaną wartość dla obecności dupleksu.</span><span class="sxs-lookup"><span data-stu-id="1d067-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d067-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d067-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="1d067-116">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="1d067-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="1d067-117">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="1d067-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="1d067-118">Moduł zapisywania dokumentów XPS firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="1d067-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
