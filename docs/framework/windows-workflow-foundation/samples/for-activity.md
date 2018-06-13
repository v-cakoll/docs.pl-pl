---
title: Dla działania
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: c79f295e7880f845c606a55f9c56ad65350f9c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515448"
---
# <a name="for-activity"></a>Dla działania
Przykładowe For demonstruje sposób tworzenia działań niestandardowych, która dziedziczy <xref:System.Activities.NativeActivity>i używać go w przepływie pracy można wykonać przykład rzeczywistych. Niestandardowe działania zawarte w tej funkcji próbki, takich jak C# `for` instrukcji. T  
  
 `For` Działania niestandardowego ma właściwości o nazwie `InitAction`, `IterationAction`, `Condition`, i `Body` odpowiadają inicjowania instrukcji, instrukcji iteracji, warunek kontynuacji i odpowiednio body — instrukcja znaleziono w standardowej C# `For` instrukcji.  
  
 W poniższej tabeli opisano pliki klucza w próbce.  
  
|Plik|Opis|  
|----------|-----------------|  
|For.CS|Definicja klasy `For` działań niestandardowych, które rozszerza <xref:System.Activities.NativeActivity> klasę, aby umożliwić korzystanie z funkcji języka C# `For` instrukcji.|  
|Program.cs|Aplikacji klienckiej, która wykonuje podstawowe pracy iteracji w kolekcji przy użyciu niestandardowego `For` działania.|  
  
> [!NOTE]
>  Korzystając z `For` działań niestandardowych, upewnij się, że `Condition` ustawiono właściwość; w przeciwnym razie mogą wystąpić Pętla nieskończona.  
  
## <a name="demonstrates"></a>Demonstracje  
 Tworzenie niestandardowego działania, która dziedziczy <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Omówienie  
 W poniższej tabeli opisano właściwości działań zawarty w tym przykładzie.  
  
 InitAction  
 Inicjowanie — instrukcja  
  
 IterationAction  
 Iteracyjny — instrukcja  
  
 Warunek  
 Kontynuacja — instrukcja  
  
 Treści  
 Treść instrukcji  
  
 Działanie dziedziczy <xref:System.Activities.NativeActivity> do uzyskania dostępu do środowiska wykonawczego funkcje, takie jak planowanie dodatkowe działania, aby uruchomić, przy użyciu jednej z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania For.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie, naciskając klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`