---
title: Azure Logic Apps — aplikacje bezserwerowe
description: Aplikacje Azure Logic Umożliwiają tworzenie zautomatyzowanych skalowalnych przepływów pracy, które integrują aplikacje i dane w usługach w chmurze i systemach lokalnych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676752"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="20665-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="20665-103">Azure Logic Apps</span></span>

<span data-ttu-id="20665-104">[Usługa Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) udostępnia bezserwerowy aparat do tworzenia zautomatyzowanych przepływów pracy w celu integracji aplikacji i danych między usługami w chmurze i systemami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="20665-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="20665-105">Tworzenie przepływów pracy przy użyciu projektanta wizualnego.</span><span class="sxs-lookup"><span data-stu-id="20665-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="20665-106">Można wyzwalać przepływy pracy na podstawie zdarzeń lub czasomierzy i wykorzystywać łączniki do integracji aplikacji i ułatwiać komunikację między firmami (B2B).</span><span class="sxs-lookup"><span data-stu-id="20665-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="20665-107">Aplikacje logiki bezproblemowo integrują się z funkcjami Azure.</span><span class="sxs-lookup"><span data-stu-id="20665-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo usługi Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="20665-109">Usługa Logic Apps może wykonywać więcej niż tylko łączyć usługi w chmurze (takie jak funkcje) z zasobami w chmurze (takimi jak kolejki i bazy danych).</span><span class="sxs-lookup"><span data-stu-id="20665-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="20665-110">Można również aranżować lokalne przepływy pracy za pomocą bramy lokalnej.</span><span class="sxs-lookup"><span data-stu-id="20665-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="20665-111">Na przykład można użyć aplikacji logiki do wyzwalania lokalnej procedury przechowywanej SQL w odpowiedzi na zdarzenie oparte na chmurze lub logiki warunkowej w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="20665-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="20665-112">Dowiedz się więcej o [łączeniu się z lokalnymi źródłami danych za pomocą lokalnej bramy danych platformy Azure.](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)</span><span class="sxs-lookup"><span data-stu-id="20665-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura aplikacji logiki](./media/logic-apps-architecture.png)

<span data-ttu-id="20665-114">Podobnie jak usługi Azure Functions, uruchamiasz przepływy pracy aplikacji logiki z wyzwalaczem.</span><span class="sxs-lookup"><span data-stu-id="20665-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="20665-115">Istnieje wiele wyzwalaczy do wyboru.</span><span class="sxs-lookup"><span data-stu-id="20665-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="20665-116">Poniższe ujęcie pokazuje tylko kilka z bardziej popularnych z setek, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="20665-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Wyzwalacze usługi Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="20665-118">Po wyzwoleniu aplikacji można użyć projektanta wizualnego do tworzenia kroków, pętli, warunków i akcji.</span><span class="sxs-lookup"><span data-stu-id="20665-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="20665-119">Wszystkie dane pochłonięte w poprzednim kroku są dostępne do użycia w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="20665-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="20665-120">Następujący przepływ pracy ładuje adresy URL z bazy danych Usługi CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="20665-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="20665-121">Znajduje te z wielu `t.co` następnie wyszukuje je na Twitterze.</span><span class="sxs-lookup"><span data-stu-id="20665-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="20665-122">Jeśli znajdzie odpowiednie tweety, aktualizuje dokumenty za pomocą powiązanych tweetów, wywołując funkcję.</span><span class="sxs-lookup"><span data-stu-id="20665-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

<span data-ttu-id="20665-124">Pulpit nawigacyjny usługi Logic Apps pokazuje historię uruchamiania przepływów pracy i to, czy każde uruchomienie zostało zakończone pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="20665-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="20665-125">Można przejść do dowolnego danego uruchomienia i sprawdzić dane używane przez każdy krok do rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="20665-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="20665-126">Aplikacje logiki udostępniają również istniejące szablony, które można edytować i dobrze nadają się do złożonych przepływów pracy w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="20665-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="20665-127">Aby dowiedzieć się więcej, zobacz [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="20665-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="20665-128">[Poprzedni](application-insights.md)
>[następny](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="20665-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
