---
title: Dla działania
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206266"
---
# <a name="for-activity"></a>Dla działania
Przykład dla pokazuje, jak utworzyć niestandardowe działanie, która dziedziczy z <xref:System.Activities.NativeActivity>i korzystać z niego w przepływie pracy można wykonać przykład rzeczywistych. Niestandardowe działanie zawarte w tej funkcji próbki, takich jak C# `for` instrukcji. T  
  
 `For` Niestandardowe działanie ma właściwości o nazwie `InitAction`, `IterationAction`, `Condition`, i `Body` odpowiadają inicjowania instrukcji, instrukcja iteracyjne, warunek kontynuacji i odpowiednio treść instrukcji znaleziono w standard języka C# `For` instrukcji.  
  
 W poniższej tabeli opisano pliki klucza w próbce.  
  
|Plik|Opis|  
|----------|-----------------|  
|For.CS|Definicja klasy `For` działania niestandardowe, które rozszerza <xref:System.Activities.NativeActivity> klasy w celu zapewnienia funkcji języka C# `For` instrukcji.|  
|Program.cs|Aplikacja kliencka, która wykonuje podstawowe prace kolekcji za pomocą niestandardowej `For` działania.|  
  
> [!NOTE]
>  Korzystając z `For` działania niestandardowego, upewnij się, że `Condition` ustawiono właściwość; w przeciwnym razie mogą wystąpić wejścia w nieskończoną pętlę.  
  
## <a name="demonstrates"></a>Demonstracje  
 Utwórz niestandardowe działanie, która dziedziczy <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Dyskusja  
 W poniższej tabeli opisano właściwości działań zawarty w tym przykładzie.  
  
 InitAction  
 Inicjowanie — instrukcja  
  
 IterationAction  
 Iteracyjne — instrukcja  
  
 Warunek  
 Instrukcja kontynuacji  
  
 Treść  
 Treść instrukcji  
  
 Działanie dziedziczy <xref:System.Activities.NativeActivity> do uzyskania dostępu do funkcji środowiska uruchomieniowego, takich jak dodatkowe działania, aby uruchomić, planowania, przy użyciu jednej z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania For.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie, naciskając klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`