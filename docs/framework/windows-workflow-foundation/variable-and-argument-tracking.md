---
title: Zmienna i śledzenia argumentu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c0857830b52b2f71df5d81f4bd232b62b894da63
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="variable-and-argument-tracking"></a>Zmienna i śledzenia argumentu
Podczas śledzenia wykonywanie przepływu pracy, często jest przydatne w celu wyodrębnienia danych. Zapewnia dodatkowy kontekst podczas uzyskiwania dostępu do wykonywania post rekordu śledzenia. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], można wyodrębnić wszelkie widoczne zmiennej lub argumentu w zakresie wszystkie działania w przepływie pracy za pomocą śledzenia. Śledzenie profile ułatwiają wyodrębnić dane.  
  
## <a name="variables-and-arguments"></a>Argumenty i zmienne  
 Gdy działanie emituje ActivityStateRecord są wyodrębniane zmienne i argumentów.  Zmienna jest niedostępna do wyodrębnienia tylko wtedy, gdy znajduje się w zakresie działania. Zmienna do wyodrębnienia w działaniu jest określony w następujący sposób:  
  
-   Jeśli zmienna jest określona przez nazwę zmiennej, śledzenie wygląda zmiennej w ramach bieżącego działania jest włączone śledzenie i działania nadrzędnego. Zmienna jest przeszukiwane w bieżącym zakresie działania i w zakresie nadrzędnym.  
  
-   Jeśli zmienne, które mają zostać wyodrębnione są określane przy użyciu nazwy = "*", a następnie są wyodrębniane wszystkie zmienne w ramach bieżącego działania, które są śledzone. W takim przypadku zmienne znajdują się w zakresie ale zdefiniowany w obiekcie nadrzędnym, które nie są wyodrębniane działań.  
  
 Podczas wyodrębniania argumenty, argumenty wyodrębnione zależą od stanu działania. Gdy stan działania to Executing, następnie tylko `InArguments` są dostępne do wyodrębnienia. Wszystkie inne działania stanu (zamknięte, Faulted Canceled) wszystkie argumenty, zarówno InArguments i OutArguments, są dostępne do wyodrębnienia.  
  
 W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany. Argumenty i zmienne można wyodrębnić tylko z <xref:System.Activities.Tracking.ActivityStateRecord> i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Chroni dane przechowywane w zmiennych i argumenty  
 Śledzonych zmiennej lub argumentu jest domyślnie widoczne przez środowisko uruchomieniowe programu WF. Projektant przepływu pracy można chronić przed dostępem w następujący sposób:  
  
1.  Wartość zmiennej szyfrowania.  
  
2.  Formant tworzenia profilu śledzenia, aby zapobiec wyodrębniania zmiennej lub argumentu.  
  
3.  Uczestników śledzenia niestandardowych upewnij się, że kodzie WF nie ujawnia poufne informacje, które są przechowywane w zmiennych lub argumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
