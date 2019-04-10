---
title: Używanie niestandardowego działania
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 47ddd42168445aa23eaaded6fd19ffe4698e4117
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309618"
---
# <a name="using-a-custom-activity"></a>Używanie niestandardowego działania
Działania, które wynikają z <xref:System.Activities.Activity> lub jej podklasach mogą być składające się na większe przepływów pracy i utworzonych bezpośrednio w kodzie. W tym temacie opisano sposób używania działań niestandardowych w przepływach pracy utworzone w kodzie lub w projektancie.  
  
> [!NOTE]
>  Niestandardowe można używać działań w tym samym projekcie, w której są zdefiniowane, tak długo, jak niestandardowe działanie i działanie, które korzysta z niego są kompilowane (czyli obciążeniu przez typ instantiating generowany przez proces kompilacji) Jeśli odwołującym się działanie jest ładowany. dynamiczne (np. przy użyciu ActivityXAMLServices), zestaw z odwołania powinny zostać następnie umieszczony w innym projekcie lub wygenerowany przez projektanta XAML musi być ręcznie edytowany Aby włączyć tę opcję.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Przy użyciu działań niestandardowych do projektu przepływu pracy  
  
1. Dodaj odwołanie z projektu hosta do projektu biblioteki działania zawierające niestandardowe działania.  
  
2. Skompiluj rozwiązanie.  
  
3. Aby użyć niestandardowego działania w projektancie, Znajdź niestandardowe działania w przyborniku, a następnie przeciągnij działanie na powierzchni projektanta.  
  
4. Aby użyć niestandardowego działania w kodzie, Dodaj instrukcję Using, która odwołuje się do projektu niestandardowe działanie, a następnie przekazać nowe wystąpienie klasy działania na <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
