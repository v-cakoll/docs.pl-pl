---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038084"
---
# <a name="load-from-xaml"></a>Ładowanie z pliku XAML
Ten przykład ilustruje sposób dynamicznego ładowania przepływu pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask. Zamiast tego, przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodę. Przykładem jest aplikacja kliencka Windows Presentation Foundation (WPF), która ładuje przepływy pracy <xref:System.Activities.XamlIntegration.ActivityXamlServices> XAML przy użyciu klasy i wykonuje je. Po ich załadowaniu przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy zostanie zwrócona wartość <xref:System.Activities.DynamicActivity%601> , która może zostać wykonana.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania LoadFromXAML. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
