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
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Usługa Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) zapewnia bezserwerowe aparatu tworzyć zautomatyzowane przepływy pracy, aby zintegrować aplikacje i dane między usługami w chmurze i systemach lokalnych. Możesz tworzyć przepływy pracy za pomocą projektanta wizualnego. Można wyzwalają przepływy pracy na podstawie zdarzeń lub czasomierze i wykorzystaj łączniki do integracji aplikacji i ułatwiają komunikację business-to-business (B2B). Usługa Logic Apps bezproblemowo integruje się z usługą Azure Functions.

![Logo usługi Azure Logic Apps](./media/logic-apps-logo.png)

Usługa Logic Apps można zrobić więcej niż tylko połączenia usługi w chmurze (na przykład funkcje) z zasobami w chmurze (takie jak kolejki i baz danych). Można też organizować przepływy w środowisku lokalnym za pomocą lokalnej bramy. Na przykład można użyć aplikacji logiki do wyzwolenia procedurę Przechowywaną lokalnie w odpowiedzi na zdarzenie oparte na chmurze lub logikę warunkową w przepływie pracy. Dowiedz się więcej o [nawiązywania połączenia z lokalnymi źródłami danych za pomocą bramy danych lokalnych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architektura aplikacji logiki](./media/logic-apps-architecture.png)

Np. usługi Azure Functions jest rozpoczynane przepływów pracy aplikacji logiki z wyzwalaczem. Istnieje wiele wyzwalaczy dla Ciebie do wyboru. Następujące przechwytywania zawiera kilka więcej popularnych te z setek, które są dostępne.

![Wyzwalacze aplikacji logiki](./media/logic-app-triggers.png)

Po wyzwoleniu aplikacji, można użyć projektanta wizualnego do rozbudowy kroki, pętle, warunki i akcje. Wszelkich danych pozyskanych w poprzednim kroku jest dostępna do użycia w kolejnych krokach. Poniższy przepływ pracy ładuje adresy URL z bazy danych CosmosDB. Znajdzie te hosta `t.co` następnie wyszukuje je w serwisie Twitter. Jeśli znajdzie odpowiednich tweetów, aktualizuje dokumenty przy użyciu powiązanych tweetów przez wywołanie funkcji.

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

Pulpit nawigacyjny aplikacji logiki Wyświetla historię uruchamiania przepływów pracy i tego, czy każdy przebieg został ukończony pomyślnie, lub nie. Można przejść do dowolnego z danym przebiegiem i sprawdzanie danych używanych przez każdy krok do rozwiązywania problemów. Usługa Logic Apps oferuje również istniejących szablonów, można edytować i dobrze nadają się dla przedsiębiorstw złożonych przepływów pracy.

Aby dowiedzieć się więcej, zobacz [usługi Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Poprzednie](application-insights.md)
>[dalej](event-grid.md)
