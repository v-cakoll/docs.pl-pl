---
title: "Ładowanie z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca5f830e666ad65ca2162ffd1abb03ce9beca387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="load-from-xaml"></a>Ładowanie z XAML
W tym przykładzie pokazano, jak załadować dynamicznie XAML przepływu pracy bez konieczności uruchamiania narzędzia XamlBuildTask. Przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody. Próbka jest [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] aplikacji klienckiej, która ładuje przy użyciu przepływów pracy XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy i wykonuje je. Po ich zostały załadowane przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy, <xref:System.Activities.DynamicActivity%601> jest zwracany, które mogą być wykonywane.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LoadFromXAML.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`  
  
## <a name="see-also"></a>Zobacz też
