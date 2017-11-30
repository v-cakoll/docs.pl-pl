---
title: "Dla działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e77800b21d671a0de0cab6f442919f50ce5ca51b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="for-activity"></a>Dla działania
Przykładowe For demonstruje sposób tworzenia działań niestandardowych, która dziedziczy <xref:System.Activities.NativeActivity>i używać go w przepływie pracy można wykonać przykład rzeczywistych. Niestandardowe działania zawarte w tej funkcji próbki, takich jak C# `for` instrukcji. T  
  
 `For` Działania niestandardowego ma właściwości o nazwie `InitAction`, `IterationAction`, `Condition`, i `Body` odpowiadają inicjowania instrukcji, instrukcji iteracji, warunek kontynuacji i odpowiednio body — instrukcja znaleziono w standardowej C# `For` instrukcji.  
  
 W poniższej tabeli opisano pliki klucza w próbce.  
  
|Plik|Opis|  
|----------|-----------------|  
|For.CS|Definicja klasy `For` działań niestandardowych, które rozszerza <xref:System.Activities.NativeActivity> klasę, aby umożliwić korzystanie z funkcji języka C# `For` instrukcji.|  
|Plik program.CS|Aplikacji klienckiej, która wykonuje podstawowe pracy iteracji w kolekcji przy użyciu niestandardowego `For` działania.|  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`