---
title: Usługa Azure Logic Apps — aplikacje niekorzystające z serwera
description: Usługa Azure Logic Apps, włączyć tworzenie zautomatyzowanych skalowalnych przepływów pracy, które integrują aplikacje i usługi danych w chmurze i systemach lokalnych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638805"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="0c451-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="0c451-103">Azure Logic Apps</span></span>

<span data-ttu-id="0c451-104">[Usługa Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) zapewnia bezserwerowe aparatu tworzyć zautomatyzowane przepływy pracy, aby zintegrować aplikacje i dane między usługami w chmurze i systemach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0c451-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="0c451-105">Możesz tworzyć przepływy pracy za pomocą projektanta wizualnego.</span><span class="sxs-lookup"><span data-stu-id="0c451-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="0c451-106">Można wyzwalają przepływy pracy na podstawie zdarzeń lub czasomierze i wykorzystaj łączniki do integracji aplikacji i ułatwiają komunikację business-to-business (B2B).</span><span class="sxs-lookup"><span data-stu-id="0c451-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="0c451-107">Usługa Logic Apps bezproblemowo integruje się z usługą Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="0c451-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo usługi Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="0c451-109">Usługa Logic Apps można zrobić więcej niż tylko połączenia usługi w chmurze (na przykład funkcje) z zasobami w chmurze (takie jak kolejki i baz danych).</span><span class="sxs-lookup"><span data-stu-id="0c451-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="0c451-110">Można też organizować przepływy w środowisku lokalnym za pomocą lokalnej bramy.</span><span class="sxs-lookup"><span data-stu-id="0c451-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="0c451-111">Na przykład można użyć aplikacji logiki do wyzwolenia procedurę Przechowywaną lokalnie w odpowiedzi na zdarzenie oparte na chmurze lub logikę warunkową w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0c451-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="0c451-112">Dowiedz się więcej o [nawiązywania połączenia z lokalnymi źródłami danych za pomocą bramy danych lokalnych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="0c451-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura aplikacji logiki](./media/logic-apps-architecture.png)

<span data-ttu-id="0c451-114">Np. usługi Azure Functions jest rozpoczynane przepływów pracy aplikacji logiki z wyzwalaczem.</span><span class="sxs-lookup"><span data-stu-id="0c451-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="0c451-115">Istnieje wiele wyzwalaczy dla Ciebie do wyboru.</span><span class="sxs-lookup"><span data-stu-id="0c451-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="0c451-116">Następujące przechwytywania zawiera kilka więcej popularnych te z setek, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="0c451-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Wyzwalacze aplikacji logiki](./media/logic-app-triggers.png)

<span data-ttu-id="0c451-118">Po wyzwoleniu aplikacji, można użyć projektanta wizualnego do rozbudowy kroki, pętle, warunki i akcje.</span><span class="sxs-lookup"><span data-stu-id="0c451-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="0c451-119">Wszelkich danych pozyskanych w poprzednim kroku jest dostępna do użycia w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="0c451-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="0c451-120">Poniższy przepływ pracy ładuje adresy URL z bazy danych CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="0c451-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="0c451-121">Znajdzie te hosta `t.co` następnie wyszukuje je w serwisie Twitter.</span><span class="sxs-lookup"><span data-stu-id="0c451-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="0c451-122">Jeśli znajdzie odpowiednich tweetów, aktualizuje dokumenty przy użyciu powiązanych tweetów przez wywołanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="0c451-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

<span data-ttu-id="0c451-124">Pulpit nawigacyjny aplikacji logiki Wyświetla historię uruchamiania przepływów pracy i tego, czy każdy przebieg został ukończony pomyślnie, lub nie.</span><span class="sxs-lookup"><span data-stu-id="0c451-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="0c451-125">Można przejść do dowolnego z danym przebiegiem i sprawdzanie danych używanych przez każdy krok do rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="0c451-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="0c451-126">Usługa Logic Apps oferuje również istniejących szablonów, można edytować i dobrze nadają się dla przedsiębiorstw złożonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="0c451-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="0c451-127">Aby dowiedzieć się więcej, zobacz [usługi Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="0c451-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0c451-128">[Poprzednie](application-insights.md)
>[dalej](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="0c451-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
