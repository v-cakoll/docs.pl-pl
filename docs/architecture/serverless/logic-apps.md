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
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Usługa Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) udostępnia bezserwerowy aparat do tworzenia zautomatyzowanych przepływów pracy w celu integracji aplikacji i danych między usługami w chmurze i systemami lokalnymi. Tworzenie przepływów pracy przy użyciu projektanta wizualnego. Można wyzwalać przepływy pracy na podstawie zdarzeń lub czasomierzy i wykorzystywać łączniki do integracji aplikacji i ułatwiać komunikację między firmami (B2B). Aplikacje logiki bezproblemowo integrują się z funkcjami Azure.

![Logo usługi Azure Logic Apps](./media/logic-apps-logo.png)

Usługa Logic Apps może wykonywać więcej niż tylko łączyć usługi w chmurze (takie jak funkcje) z zasobami w chmurze (takimi jak kolejki i bazy danych). Można również aranżować lokalne przepływy pracy za pomocą bramy lokalnej. Na przykład można użyć aplikacji logiki do wyzwalania lokalnej procedury przechowywanej SQL w odpowiedzi na zdarzenie oparte na chmurze lub logiki warunkowej w przepływie pracy. Dowiedz się więcej o [łączeniu się z lokalnymi źródłami danych za pomocą lokalnej bramy danych platformy Azure.](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)

![Architektura aplikacji logiki](./media/logic-apps-architecture.png)

Podobnie jak usługi Azure Functions, uruchamiasz przepływy pracy aplikacji logiki z wyzwalaczem. Istnieje wiele wyzwalaczy do wyboru. Poniższe ujęcie pokazuje tylko kilka z bardziej popularnych z setek, które są dostępne.

![Wyzwalacze usługi Logic Apps](./media/logic-app-triggers.png)

Po wyzwoleniu aplikacji można użyć projektanta wizualnego do tworzenia kroków, pętli, warunków i akcji. Wszystkie dane pochłonięte w poprzednim kroku są dostępne do użycia w kolejnych krokach. Następujący przepływ pracy ładuje adresy URL z bazy danych Usługi CosmosDB. Znajduje te z wielu `t.co` następnie wyszukuje je na Twitterze. Jeśli znajdzie odpowiednie tweety, aktualizuje dokumenty za pomocą powiązanych tweetów, wywołując funkcję.

![Przepływ pracy aplikacji logiki](./media/logic-app-workflow.png)

Pulpit nawigacyjny usługi Logic Apps pokazuje historię uruchamiania przepływów pracy i to, czy każde uruchomienie zostało zakończone pomyślnie, czy nie. Można przejść do dowolnego danego uruchomienia i sprawdzić dane używane przez każdy krok do rozwiązywania problemów. Aplikacje logiki udostępniają również istniejące szablony, które można edytować i dobrze nadają się do złożonych przepływów pracy w przedsiębiorstwie.

Aby dowiedzieć się więcej, zobacz [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Poprzedni](application-insights.md)
>[następny](event-grid.md)
