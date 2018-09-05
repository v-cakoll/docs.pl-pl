---
title: Argumenty dynamiczne
ms.date: 03/30/2017
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
ms.openlocfilehash: dcf6b84889f3bd7d043f736336c39634cd5384c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530444"
---
# <a name="dynamic-arguments"></a>Argumenty dynamiczne
Ten przykład demonstruje sposób implementacji działania, dla której argumenty są definiowane przez konsumenta działania, a nie Autor działania. Robi to poprzez zastąpienie jej środowisko uruchomieniowe tworzy metadane działań.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Przed wykonywania środowisko uruchomieniowe tworzy opis działania, sprawdzając publiczne elementy członkowskie typu działania i automatycznie deklarowanie argumentów, zmienne, działania podrzędne i działania delegatach jako część metadane działań. Robi to, aby zapewnić poprawne konstrukcji przepływu pracy oraz aby zarządzać relacjami środowiska wykonawczego i okresu istnienia reguły. Zwykle definiuje argumenty działanie Autor działań, określając publiczne elementy członkowskie typu działania, który pochodzi od <xref:System.Activities.Argument>. Dla każdego publicznego elementu członkowskiego, która pochodzi od klasy <xref:System.Activities.Argument>, środowisko uruchomieniowe tworzy <xref:System.Activities.RuntimeArgument> i wiąże go do argumentu dostarczone przez użytkownika, ustaw na ten element członkowski. W niektórych przypadkach konsument działania zapewnia jednak niektórych konfiguracji, który określa zestaw argumentów. Zastępuje Autor działania <xref:System.Activities.Activity.CacheMetadata%2A> dostosować sposób działania metadanych został opracowany, która obejmuje zestaw argumenty skojarzone z działaniem.  
  
 W tym przykładzie przedstawiono sposób tworzenia listy argumentów dynamicznie do działania, które wywołuje metodę. Konsument działania określa typ i nazwę metody, którą chcą wywoływać wraz z kolekcją argumenty do przekazania do tej metody.  
  
> [!NOTE]
>  W tym przykładzie ma na celu pokazują, jak zastąpić <xref:System.Activities.CodeActivity.CacheMetadata%2A> i sposobu używania <xref:System.Activities.RuntimeArgument>. Istnieje kilka zastrzeżeń w odniesieniu do rodzajów metod, które można wywołać tego działania. Na przykład czy nie współpracuje z typy ogólne i tablice parametrów. <xref:System.Activities.Statements.InvokeMethod> Działania, który jest dostarczany w zestawach.NET Framework obsługuje te przypadki i nie tylko.  
  
 `MethodInvoke` Działania zastąpienia <xref:System.Activities.CodeActivity.CacheMetadata%2A> i rozpoczyna się od utworzenia <xref:System.Activities.RuntimeArgument> do obsługi dowolnej w wyniku wywołania metody. Powiąże to <xref:System.Activities.RuntimeArgument> do publicznie Ustawialne <xref:System.Activities.OutArgument> o nazwie `Result`. Jeśli `MethodInvoke.Result` jest `null`, środowisko wykonawcze automatycznie wypełnia ją za pomocą <xref:System.Activities.OutArgument> skonfigurowane za pomocą wyrażenia domyślne dla tego typu. To zachowanie oznacza, że autor działania nigdy nie można sprawdzić, czy jest właściwością argumentu `null`.  
  
 Następnie <xref:System.Activities.CodeActivity.CacheMetadata%2A> określa przesłonięcie `MethodInfo` używa wywołania z podanego przez użytkownika `MethodName` i `TargetType`. `DetermineMethodInfo` Metoda przyjmuje <xref:System.Activities.CodeActivityMetadata> parametr przekazany do <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienie tak, aby wszelkie błędy konfiguracji mogą być zgłaszane jako błędy sprawdzania poprawności. Jest to realizowane przez wywołanie `metadata.AddValidationError`.  
  
 Gdy `MethodInfo` został ustawiony, przykład wykonuje iterację na `MethodInfo` parametrów. Dla każdego parametru tworzy <xref:System.Activities.RuntimeArgument> i wiąże go do odpowiedniego argumentu w kolekcji dostarczone przez użytkownika z `Parameters` właściwości. Na koniec kolekcji <xref:System.Activities.RuntimeArgument>s jest skojarzony z działania, wywołując `metadata.SetArgumentsCollection`.  
  
 Należy pamiętać, że argument rozwiązanie można wykonać przy użyciu <xref:System.Activities.RuntimeArgument>, jak w przypadku `resultArgument` lub argumentu dostarczone przez użytkownika, tak jak w przypadku `Parameters` kolekcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik DynamicArguments.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`