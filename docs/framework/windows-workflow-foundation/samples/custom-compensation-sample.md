---
title: Przykładowe Kompensacja niestandardowa
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503722"
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="b7f0a-102">Przykładowe Kompensacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="b7f0a-102">Custom Compensation Sample</span></span>
<span data-ttu-id="b7f0a-103">Ten przykład ilustruje sposób używania <xref:System.Activities.Statements.CompensableActivity> i jego procedurę obsługi do definiowania logiki Kompensacja niestandardowa.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="b7f0a-104">Scenariusz, w tym przykładzie w modelu jest agencji wypożyczeń Truck.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b7f0a-105">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="b7f0a-105">Sample Details</span></span>  
 <span data-ttu-id="b7f0a-106">Procedura symulowane jest następująca:</span><span class="sxs-lookup"><span data-stu-id="b7f0a-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="b7f0a-107">Użytkownik żąda ciężarówki oferty dzierżawy dla określonej daty.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="b7f0a-108">Kontaktować się z trzech firm truck i znajdują się trzy cudzysłowów.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="b7f0a-109">Użytkownik wybiera jeden truck oferty i przechodzi do kolejności przy użyciu karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="b7f0a-110">Aplikacja anuluje inne oferty truck dwa.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="b7f0a-111">Aplikacja pobiera opłaty za usługę, czyli niepodlegającego zwrotowi środków dla kont innych niż premium w przypadku anulowania się stanie w ciągu 10 dni lub mniej przed datą rezerwacji.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="b7f0a-112">Aplikacja opłaty za opłatą wypożyczeń truck.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="b7f0a-113">Aplikacja czeka, aż Data rezerwacji lub do momentu klient zdecydowała się anulowania rezerwacji, osiągnięta jako pierwsza.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="b7f0a-114">Jeśli klient anuluje rezerwację, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Kompensacja niestandardowa logiki jest uruchamiany zgodnie z następującą logiką:</span><span class="sxs-lookup"><span data-stu-id="b7f0a-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="b7f0a-115">Jeśli klient ma konto inne niż premium i jest mniej niż 10 dni przed datą rezerwacji, a następnie nadal są naliczane opłaty za usługę; w przeciwnym razie aplikacja zwroty opłata za usługę.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="b7f0a-116">Pozostałe kompensacyjne działań (kolejność truck + opłata kolejności truck) są uruchamiane zgodnie z domyślnej logiki wynagrodzenie, która jest wyrównanie w odwrotnej kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7f0a-117">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b7f0a-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b7f0a-118">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz rozwiązanie CustomCompensation.sln.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="b7f0a-119">Znajduje się on w katalogu \WF\Basic\Compensation\CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="b7f0a-120">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="b7f0a-121">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7f0a-122">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7f0a-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b7f0a-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7f0a-124">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7f0a-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b7f0a-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`