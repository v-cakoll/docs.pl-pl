---
title: "Argumentów dynamicznych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96e03aac921cfeb69811a0c51ad2151b7e70cd93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dynamic-arguments"></a>Argumentów dynamicznych
W tym przykładzie pokazano, jak zaimplementować działanie, dla którego argumenty są definiowane przez konsumentów działania, a nie przez autora działania. Robi to przez zastąpienie sposób środowiska uruchomieniowego tworzy metadane działań.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Przed wykonaniem środowisko uruchomieniowe kompilacje opis działania, sprawdzając publiczne elementy członkowskie tego typu działania i automatycznie deklarowanie argumenty, zmienne, działania podrzędne i delegatów działanie jako część metadane działań. Robi to, aby zapewnić poprawne konstrukcji przepływu pracy oraz aby zarządzać relacjami środowiska wykonawczego i okres istnienia reguły. Zwykle przez autora działania definiuje argumentów działania, określając publicznych elementów członkowskich w typie działania, która pochodzi z <xref:System.Activities.Argument>. Dla każdego członka publicznego pochodzącego od <xref:System.Activities.Argument>, tworzy środowisko uruchomieniowe <xref:System.Activities.RuntimeArgument> i wiąże ją ustawić na ten element członkowski argument dostarczane przez użytkownika. W niektórych przypadkach konsumenta działania zapewnia jednak niektóre konfiguracji, który określa zestaw argumentów. Przesłania przez autora działania <xref:System.Activities.Activity.CacheMetadata%2A> można dostosować sposób działania jest wbudowana metadanych, w tym zestawie argumenty skojarzone z działaniem.  
  
 Ten przykład demonstruje sposób tworzenia listy argumentów dynamicznie dla działania, która wywołuje metodę. Konsument działania określa typ i nazwę metody, które mają być wywołanie wraz z kolekcją argumenty do przekazania do tej metody.  
  
> [!NOTE]
>  Ten przykład ma na celu pokazują, jak zastąpić <xref:System.Activities.CodeActivity.CacheMetadata%2A> i sposobu użycia <xref:System.Activities.RuntimeArgument>. Istnieje kilka zastrzeżeń względem rodzajów metod, które można wywołać tego działania. Na przykład czy nie współpracuje z ogólne i tablice parametrów. <xref:System.Activities.Statements.InvokeMethod> Działania, który jest dostarczany in.NET Framework obsługi tych przypadkach i inne.  
  
 `MethodInvoke` Działania zastąpienia <xref:System.Activities.CodeActivity.CacheMetadata%2A> i rozpoczyna się od utworzenia <xref:System.Activities.RuntimeArgument> do obsługi dowolnej w wyniku wywołania metody. Tworzy ona powiązanie to <xref:System.Activities.RuntimeArgument> do publicznie można ustawić <xref:System.Activities.OutArgument> o nazwie `Result`. Jeśli `MethodInvoke.Result` jest `null`, środowisko uruchomieniowe automatycznie wypełni go przy użyciu <xref:System.Activities.OutArgument> skonfigurowano wyrażenie wartości domyślnej dla jego typu. Oznacza to zachowanie przez autora działania nigdy nie można sprawdzić, czy jest właściwością argumentu `null`.  
  
 Następnie <xref:System.Activities.CodeActivity.CacheMetadata%2A> określa zastąpienie `MethodInfo` używa wywołania z dostarczonych przez użytkownika `MethodName` i `TargetType`. `DetermineMethodInfo` Ma metodę <xref:System.Activities.CodeActivityMetadata> parametr przekazany do <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienie tak, aby wszelkie błędy konfiguracji mogą być zgłaszane jako błędy sprawdzania poprawności. Jest to realizowane przez wywołanie `metadata.AddValidationError`.  
  
 Raz `MethodInfo` skonfigurowano, próbki przechodzi przez `MethodInfo` parametrów. Dla każdego parametru tworzy <xref:System.Activities.RuntimeArgument> i wiąże go do odpowiedniego argumentu w kolekcji dostarczane przez użytkownika z `Parameters` właściwości. Na koniec kolekcji <xref:System.Activities.RuntimeArgument>s jest skojarzona z działaniem przez wywołanie metody `metadata.SetArgumentsCollection`.  
  
 Należy pamiętać, że rozwiązanie argument można wykonać przy użyciu <xref:System.Activities.RuntimeArgument>, jak w przypadku `resultArgument` lub argumentu dostarczane przez użytkownika, tak jak w przypadku `Parameters` kolekcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik DynamicArguments.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`