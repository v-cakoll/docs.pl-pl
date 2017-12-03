---
title: "Przykładowe kompensacji niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ace7d38a456bb9d7f5dd59776b9ae5843b7b651
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="6649e-102">Przykładowe kompensacji niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6649e-102">Custom Compensation Sample</span></span>
<span data-ttu-id="6649e-103">Ten przykład przedstawia sposób użycia <xref:System.Activities.Statements.CompensableActivity> i jego kompensacji, aby zdefiniować kompensacji niestandardowej logiki.</span><span class="sxs-lookup"><span data-stu-id="6649e-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="6649e-104">Scenariusz uformowana w tym przykładzie jest agencji wynajem ciężarówka.</span><span class="sxs-lookup"><span data-stu-id="6649e-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6649e-105">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="6649e-105">Sample Details</span></span>  
 <span data-ttu-id="6649e-106">Kroki symulowane są:</span><span class="sxs-lookup"><span data-stu-id="6649e-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="6649e-107">Użytkownik żąda ciężarówki cudzysłowy dzierżawy dla określonej daty.</span><span class="sxs-lookup"><span data-stu-id="6649e-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="6649e-108">Kontaktuje się z trzech firm ciężarówka i trzy cudzysłowy są udostępniane.</span><span class="sxs-lookup"><span data-stu-id="6649e-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="6649e-109">Użytkownik wybiera jeden oferty ciężarówka i przechodzi do kolejności za pomocą karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="6649e-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="6649e-110">Aplikacja anuluje innych cudzysłowy ciężarówka dwa.</span><span class="sxs-lookup"><span data-stu-id="6649e-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="6649e-111">Aplikacja pobiera opłaty za usługę, z systemem innym niż zwrotowi dla inne niż premium konta w przypadku anulowania 10 dni lub mniej wcześniejsza od daty rezerwacji.</span><span class="sxs-lookup"><span data-stu-id="6649e-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="6649e-112">Aplikacja pobiera opłata wynajem ciężarówka.</span><span class="sxs-lookup"><span data-stu-id="6649e-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="6649e-113">Aplikacja oczekuje, aż Data rezerwacji lub do momentu klient postanowiła anulowania rezerwacji, zależnie od zostanie osiągnięty jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="6649e-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="6649e-114">Jeśli klient anuluje rezerwacji, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> kompensacji niestandardowej logiki działa zgodnie z następującą logiką:</span><span class="sxs-lookup"><span data-stu-id="6649e-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="6649e-115">Jeśli klient ma inne niż premium konta i jest krótszy niż 10 dni przed datą rezerwacji, a następnie nadal są naliczane opłaty za usługę; w przeciwnym razie aplikacja zwrotów opłaty za usługę.</span><span class="sxs-lookup"><span data-stu-id="6649e-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="6649e-116">Pozostałe działania compensable (kolejność ciężarówka + opłata kolejności ciężarówka) są uruchamiane zgodnie z logiką kompensacji domyślne, czyli odpowiednio w odwrotnej kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6649e-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6649e-117">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="6649e-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6649e-118">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz rozwiązanie CustomCompensation.sln.</span><span class="sxs-lookup"><span data-stu-id="6649e-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="6649e-119">Znajduje się w katalogu \WF\Basic\Compensation\CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="6649e-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="6649e-120">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6649e-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="6649e-121">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6649e-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6649e-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6649e-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6649e-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6649e-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6649e-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="6649e-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6649e-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6649e-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`