---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715950"
---
# <a name="load-from-xaml"></a>Ładowanie z pliku XAML
Ten przykład ilustruje sposób dynamicznego ładowania przepływu pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask. Zamiast tego, przykład wywołuje metodę <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>. Przykładem jest aplikacja kliencka Windows Presentation Foundation (WPF), która ładuje przepływy pracy XAML przy użyciu klasy <xref:System.Activities.XamlIntegration.ActivityXamlServices> i wykonuje je. Po ich załadowaniu przy użyciu klasy <xref:System.Activities.XamlIntegration.ActivityXamlServices> zwracana jest <xref:System.Activities.DynamicActivity%601>, która może zostać wykonana.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania LoadFromXAML. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
