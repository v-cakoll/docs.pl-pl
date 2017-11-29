---
title: "Ograniczenie: układ platformy WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a>Ograniczenie: układ platformy WPF
Układ formantów WPF mogą się nieznacznie zmieniać.  
  
## <a name="impact"></a>Wpływ  
 W wyniku tej zmiany:  
  
-   Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.  
  
-   Umieszczanie obiektu można przenieść co najwyżej jeden piksel.  
  
-   Elementy wyśrodkowany można pionie lub poziomie od środka co najwyżej jeden piksel.  
  
 Domyślnie ten nowy układ jest włączone tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.  
  
## <a name="mitigation"></a>Ograniczenie  
 Ponieważ ta modyfikacja zwykle wyeliminować wycinka prawej lub dolnej formantów WPF w DPIs wysoki, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na .NET Framework 4.6 włączyć do tego nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikacje docelowe .NET Framework 4.6, które mają formantów WPF do renderowania przy użyciu poprzedniej algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
