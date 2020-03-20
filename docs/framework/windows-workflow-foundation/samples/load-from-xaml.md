---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142722"
---
# <a name="load-from-xaml"></a>Ładowanie z pliku XAML
W tym przykładzie pokazano, jak dynamicznie załadować przepływ pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask. Zamiast tego przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodę. Przykład jest windows presentation foundation (WPF) aplikacja kliencka, która <xref:System.Activities.XamlIntegration.ActivityXamlServices> ładuje przepływy pracy XAML przy użyciu klasy i wykonuje je. Po ich załadowaniu <xref:System.Activities.XamlIntegration.ActivityXamlServices> przy użyciu <xref:System.Activities.DynamicActivity%601> klasy, zwracany jest, które mogą być wykonywane.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania LoadFromXAML.sln.

2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
