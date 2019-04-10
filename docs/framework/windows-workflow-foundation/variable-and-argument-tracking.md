---
title: Śledzenie argumentów i zmiennych
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 7062e44a18cfd4b07cc63f4b490c08fbbfeeb8a3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300895"
---
# <a name="variable-and-argument-tracking"></a>Śledzenie argumentów i zmiennych
Podczas śledzenia wykonywania przepływu pracy, jest często przydatne w celu wyodrębnienia danych. Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], można wyodrębnić wszystkie widoczne zmiennej lub argumentu w zakresie wszelkie działania w przepływie pracy przy użyciu śledzenia. Profile śledzenia ułatwiają do wyodrębniania danych.  
  
## <a name="variables-and-arguments"></a>Zmienne i argumenty  
 Zmienne i argumenty są wyodrębniane, gdy działanie wyemituje ActivityStateRecord.  Zmienna jest dostępna do wyodrębnienia, tylko wtedy, gdy jest w zakresie działania. Zmienna ma zostać wyodrębniony w ramach działania jest określony w następujący sposób:  
  
-   Jeśli zmienna jest określona przez nazwę zmiennej, śledzenie wygląda zmiennej w ramach bieżącego działania, które są śledzone i działania nadrzędnego. Zmienna jest przeszukiwany w bieżącym zakresie działania, a także w zakresie nadrzędnym.  
  
-   Jeśli określono za pomocą nazwy zmiennych, które ma zostać wyodrębniony = "*", a następnie są wyodrębniane wszystkie zmienne w obrębie bieżącego działania, które są śledzone. W tym przypadku zmienne znajdują się w zakresie ale zdefiniowany w elemencie nadrzędnym, które nie zostały wyodrębnione działań.  
  
 Podczas wyodrębniania argumentów, argumenty wyodrębnione zależą od stanu działania. Jeśli stan działania jest wykonywanie, następnie tylko `InArguments` są dostępne do wyodrębnienia. Dla dowolnego innego działania stanu (zamknięte, Faulted anulowane) wszystkie argumenty InArguments i OutArguments, są dostępne do wyodrębnienia.  
  
 W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane. Zmienne i argumenty wyodrębniania tylko z <xref:System.Activities.Tracking.ActivityStateRecord> i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Ochrona informacji przechowywanych w ramach zmienne i argumenty  
 Śledzone zmiennej lub argumentu jest domyślnie widoczny przez środowisko uruchomieniowe programu WF. Projektant przepływu pracy można go chronić przed dostępem, wykonując następujące czynności:  
  
1. Szyfrowanie wartość zmiennej.  
  
2. Formant tworzenia profilu śledzenia, aby uniknąć wyodrębniania zmiennej lub argumentu.  
  
3. Dla uczestników śledzenia niestandardowego upewnij się, że kod WF nie ujawniają poufne informacje, które są przechowywane w zmiennych lub argumentów.  
  
## <a name="see-also"></a>Zobacz także

- [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
