---
title: "Przy użyciu działań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e534f9a3e8d0a7d675e43bc03266e4863f95d45d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-custom-activity"></a>Przy użyciu działań niestandardowych
Działania, które pochodzą z <xref:System.Activities.Activity> ani jej podklasy mogą być składane do większych przepływy pracy lub tworzone bezpośrednio w kodzie. W tym temacie opisano sposób używania działań niestandardowych w przepływach pracy utworzone w kodzie lub w projektancie.  
  
> [!NOTE]
>  Niestandardowych można używać działań w tym samym projekcie, w którym są zdefiniowane tak długo, jak zarówno działań niestandardowych, jak i działanie, które korzysta z niego są kompilowane (tj. załadować według typu instantiating wygenerowanych przez proces kompilacji) Jeśli ładowany jest odwołaniem do działania dynamicznie (np. przy użyciu obiekt ActivityXAMLServices), następnie przywoływanego zestawu należy umieścić w innym projekcie, lub wygenerowany przez projektanta XAML musi być ręcznie modyfikować aby je włączyć.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Przy użyciu działań niestandardowych do projektu przepływu pracy  
  
1.  Dodaj odwołanie z projektu hosta do projektu biblioteki działania zawierające działania niestandardowego.  
  
2.  Skompiluj rozwiązanie.  
  
3.  Aby używać działań niestandardowych w projektancie, Znajdź w przyborniku działań niestandardowych i przeciągnij działanie na powierzchnię projektanta.  
  
4.  Aby używać działań niestandardowych w kodzie, Dodaj instrukcję Using, która odwołuje się do projektu działań niestandardowych i podaj nowe wystąpienie klasy działanie, aby <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
