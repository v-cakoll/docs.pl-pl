---
title: Ładowanie z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: f17bbf19e4ae97dfb7a281f3f5504618611ace7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514810"
---
# <a name="load-from-xaml"></a>Ładowanie z XAML
W tym przykładzie pokazano, jak załadować dynamicznie XAML przepływu pracy bez konieczności uruchamiania narzędzia XamlBuildTask. Przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody. Próbka jest aplikacja kliencka Windows Presentation Foundation (WPF), który ładuje przy użyciu przepływów pracy XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy i wykonuje je. Po ich zostały załadowane przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy, <xref:System.Activities.DynamicActivity%601> jest zwracany, które mogą być wykonywane.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LoadFromXAML.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`