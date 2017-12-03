---
title: "Za pomocą międzyoperacyjności z programem Exchange danych zewnętrznych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f62d5a468e3730ec4f636d57cb9d0c6c3973a8d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="8d767-102">Za pomocą międzyoperacyjności z programem Exchange danych zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="8d767-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="8d767-103"><xref:System.Activities.Statements.Interop> Działanie może być używane do wykonywania czynności z [!INCLUDE[wf](../../../../includes/wf-md.md)] w [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] i [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) i przepływów pracy w ramach [!INCLUDE[wf2](../../../../includes/wf2-md.md)] w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="8d767-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from [!INCLUDE[wf](../../../../includes/wf-md.md)] in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within [!INCLUDE[wf2](../../../../includes/wf2-md.md)] in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="8d767-104">W tym przykładzie przedstawiono sposób konfigurowania i uruchamiania WF3 przepływu pracy, który używa <xref:System.Workflow.Activities.ExternalDataExchangeService> (i odpowiednich działań niestandardowych do wywoływania metody i obsługi zdarzeń) przy użyciu <xref:System.Activities.Statements.Interop> działania w WF4 usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d767-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d767-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8d767-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d767-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8d767-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d767-107">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8d767-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d767-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d767-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8d767-109">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="8d767-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="8d767-110">Otwórz plik ExternalDataExchange.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d767-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d767-111">Aby samodzielnie tworzyć przykładowy, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8d767-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="8d767-112">Aby uruchomić przykład, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="8d767-112">To run the sample, press F5.</span></span>
