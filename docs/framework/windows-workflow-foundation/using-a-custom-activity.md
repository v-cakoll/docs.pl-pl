---
title: Używanie niestandardowego działania
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962222"
---
# <a name="using-a-custom-activity"></a>Używanie niestandardowego działania
Działania pochodzące z <xref:System.Activities.Activity> lub jego podklasy mogą być złożone w większych przepływach pracy lub tworzone bezpośrednio w kodzie. W tym temacie opisano sposób używania działań niestandardowych w przepływach pracy utworzonych w kodzie lub w projektancie.  
  
> [!NOTE]
> Działań niestandardowych można używać w tym samym projekcie, w którym są zdefiniowane, tak długo jak działanie niestandardowe i działanie, które go używa, są kompilowane (tj. ładowane przez typ tworzenia wystąpienia generowanego przez proces kompilacji), jeśli zostanie załadowane działanie odwołujące dynamicznie (np. przy użyciu obiekt ActivityXamlServices), zestaw, do którego istnieje odwołanie, powinien być umieszczony w innym projekcie lub kod XAML wygenerowany przez projektanta musi być edytowany ręcznie, aby go włączyć.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Używanie niestandardowego działania do projektu przepływu pracy  
  
1. Dodaj odwołanie z projektu hosta do projektu biblioteki działań zawierającego działanie niestandardowe.  
  
2. Skompiluj rozwiązanie.  
  
3. Aby użyć działania niestandardowego w projektancie, zlokalizuj działanie niestandardowe w przyborniku i przeciągnij działanie na powierzchnię projektanta.  
  
4. Aby użyć działania niestandardowego w kodzie, Dodaj instrukcję using, która odwołuje się do projektu działania niestandardowego, i przekaż nowe wystąpienie działania do <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
