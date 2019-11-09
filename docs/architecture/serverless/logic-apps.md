---
title: Azure Logic Apps — aplikacje bezserwerowe
description: Azure Logic Apps umożliwia tworzenie zautomatyzowanych skalowalnych przepływów pracy, które integrują aplikacje i dane w usługach w chmurze i systemach lokalnych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676752"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="0a8b1-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="0a8b1-103">Azure Logic Apps</span></span>

<span data-ttu-id="0a8b1-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) zapewnia aparat bezserwerowy do tworzenia zautomatyzowanych przepływów pracy do integrowania aplikacji i danych między usługami w chmurze i systemami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="0a8b1-105">Tworzenie przepływów pracy przy użyciu projektanta wizualnego.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="0a8b1-106">Możesz wyzwolić przepływy pracy na podstawie zdarzeń lub czasomierzy i wykorzystać łączniki do aplikacji integracji i ułatwić komunikację między firmami (B2B).</span><span class="sxs-lookup"><span data-stu-id="0a8b1-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="0a8b1-107">Logic Apps bezproblemowo integruje się z Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="0a8b1-109">Logic Apps może robić więcej niż tylko łączenie usług w chmurze (takich jak funkcje) z zasobami w chmurze (takimi jak kolejki i bazy danych).</span><span class="sxs-lookup"><span data-stu-id="0a8b1-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="0a8b1-110">Możesz również organizować lokalne przepływy pracy za pomocą bramy lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="0a8b1-111">Można na przykład użyć aplikacji logiki do wyzwolenia lokalnej procedury składowanej SQL w odpowiedzi na zdarzenie oparte na chmurze lub logikę warunkową w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="0a8b1-112">Dowiedz się więcej [na temat nawiązywania połączenia z lokalnymi źródłami danych za pomocą lokalnej bramy danych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="0a8b1-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura Logic Apps](./media/logic-apps-architecture.png)

<span data-ttu-id="0a8b1-114">Podobnie jak Azure Functions, można rozpocząć przepływy pracy aplikacji logiki przy użyciu wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="0a8b1-115">Istnieje wiele wyzwalaczy do wyboru.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="0a8b1-116">Poniższe przechwytywanie pokazuje zaledwie kilka z bardziej popularnych z setek, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Wyzwalacze Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="0a8b1-118">Po wyzwoleniu aplikacji możesz użyć projektanta wizualnego, aby skompilować kroki, pętle, warunki i akcje.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="0a8b1-119">Wszystkie dane pozyskane w poprzednim kroku są dostępne do użycia w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="0a8b1-120">Następujący przepływ pracy ładuje adresy URL z bazy danych CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="0a8b1-121">Znajduje je na hoście `t.co` następnie wyszukuje je w serwisie Twitter.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="0a8b1-122">Jeśli znajdzie odpowiednie tweety, aktualizuje dokumenty za pomocą pokrewnych tweetów przez wywołanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

<span data-ttu-id="0a8b1-124">Pulpit nawigacyjny Logic Apps przedstawia historię uruchamiania przepływów pracy oraz tego, czy poszczególne przebiegi zostały wykonane pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="0a8b1-125">Można przechodzić do dowolnego danego przebiegu i sprawdzać dane używane przez poszczególne kroki w celu rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="0a8b1-126">Logic Apps udostępnia również istniejące szablony, które można edytować i są odpowiednie dla złożonych przepływów pracy przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="0a8b1-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="0a8b1-127">Aby dowiedzieć się więcej, zobacz [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="0a8b1-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0a8b1-128">[Poprzedni](application-insights.md)
>[dalej](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="0a8b1-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
