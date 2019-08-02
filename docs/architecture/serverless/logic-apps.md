---
title: Azure Logic Apps — aplikacje bezserwerowe
description: Azure Logic Apps umożliwia tworzenie zautomatyzowanych skalowalnych przepływów pracy, które integrują aplikacje i dane w usługach w chmurze i systemach lokalnych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676752"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) zapewnia aparat bezserwerowy do tworzenia zautomatyzowanych przepływów pracy do integrowania aplikacji i danych między usługami w chmurze i systemami lokalnymi. Tworzenie przepływów pracy przy użyciu projektanta wizualnego. Możesz wyzwolić przepływy pracy na podstawie zdarzeń lub czasomierzy i wykorzystać łączniki do aplikacji integracji i ułatwić komunikację między firmami (B2B). Logic Apps bezproblemowo integruje się z Azure Functions.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps może robić więcej niż tylko łączenie usług w chmurze (takich jak funkcje) z zasobami w chmurze (takimi jak kolejki i bazy danych). Możesz również organizować lokalne przepływy pracy za pomocą bramy lokalnej. Można na przykład użyć aplikacji logiki do wyzwolenia lokalnej procedury składowanej SQL w odpowiedzi na zdarzenie oparte na chmurze lub logikę warunkową w przepływie pracy. Dowiedz się więcej [na temat nawiązywania połączenia z lokalnymi źródłami danych za pomocą lokalnej bramy danych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architektura Logic Apps](./media/logic-apps-architecture.png)

Podobnie jak Azure Functions, można rozpocząć przepływy pracy aplikacji logiki przy użyciu wyzwalacza. Istnieje wiele wyzwalaczy do wyboru. Poniższe przechwytywanie pokazuje zaledwie kilka z bardziej popularnych z setek, które są dostępne.

![Wyzwalacze Logic Apps](./media/logic-app-triggers.png)

Po wyzwoleniu aplikacji możesz użyć projektanta wizualnego, aby skompilować kroki, pętle, warunki i akcje. Wszystkie dane pozyskane w poprzednim kroku są dostępne do użycia w kolejnych krokach. Następujący przepływ pracy ładuje adresy URL z bazy danych CosmosDB. Znajduje je na hoście `t.co` , a następnie wyszukuje je w serwisie Twitter. Jeśli znajdzie odpowiednie tweety, aktualizuje dokumenty za pomocą pokrewnych tweetów przez wywołanie funkcji.

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

Pulpit nawigacyjny Logic Apps przedstawia historię uruchamiania przepływów pracy oraz tego, czy poszczególne przebiegi zostały wykonane pomyślnie, czy nie. Można przechodzić do dowolnego danego przebiegu i sprawdzać dane używane przez poszczególne kroki w celu rozwiązywania problemów. Logic Apps udostępnia również istniejące szablony, które można edytować i są odpowiednie dla złożonych przepływów pracy przedsiębiorstwa.

Aby dowiedzieć się więcej, zobacz [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Poprzedni](application-insights.md)Następny
>[](event-grid.md)
