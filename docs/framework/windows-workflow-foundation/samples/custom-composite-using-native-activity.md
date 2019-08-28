---
title: Niestandardowy element złożony przy użyciu działania Native
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 8a0d1077c058ecdbad10a2e7bd61ff5eb75e1cb5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044308"
---
# <a name="custom-composite-using-native-activity"></a>Niestandardowy element złożony przy użyciu działania Native
W tym przykładzie pokazano <xref:System.Activities.NativeActivity> , jak napisać harmonogram innych <xref:System.Activities.Activity> obiektów w celu sterowania przepływem wykonywania przepływu pracy. Ten przykład używa dwóch typowych przepływów sterowania, sekwencji i czasu, aby zademonstrować, jak to zrobić.

## <a name="sample-details"></a>Przykładowe szczegóły
 Począwszy od <xref:System.Activities.NativeActivity>, najpierw należy zauważyć, że pochodzi on od. `MySequence` <xref:System.Activities.NativeActivity>jest obiektem, który ujawnia pełną szerokość środowiska uruchomieniowego przepływu pracy <xref:System.Activities.NativeActivityContext> przez przekazaną `Execute` do metody. <xref:System.Activities.Activity>

 `MySequence`ujawnia publiczną kolekcję <xref:System.Activities.Activity> obiektów, które są wypełniane przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowisko uruchomieniowe przepływu pracy wywołuje <xref:System.Activities.Activity.CacheMetadata%2A> metodę dla każdego działania w przepływie pracy. W trakcie tego procesu środowisko uruchomieniowe ustanawia relacje nadrzędny-podrzędny do określania zakresu danych i zarządzania okresem istnienia. Domyślna implementacja <xref:System.Activities.Activity.CacheMetadata%2A> metody <xref:System.Collections.IEnumerable> <xref:System.Activities.Activity> <xref:System.Activities.Activity> `MySequence` <xref:System.ComponentModel.TypeDescriptor> używa klasy wystąpienia dla działania, aby dodać jakąkolwiek publiczną właściwość typu lub \<> jako elementy podrzędne elementu `MySequence` działanie.

 Za każdym razem, gdy działanie ujawnia publiczną kolekcję działań podrzędnych, prawdopodobnie te działania podrzędne będą miały stan. Najlepszym rozwiązaniem dla działania nadrzędnego jest w tym przypadku `MySequence`ujawnienie kolekcji zmiennych, za pomocą których można wykonać działania podrzędne. Podobnie jak działania podrzędne, <xref:System.Activities.Activity.CacheMetadata%2A> Metoda dodaje publiczne właściwości typu <xref:System.Activities.Variable> lub <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako zmienne skojarzone z `MySequence` działaniem.

 Poza zmiennymi publicznymi, które są manipulowane przez elementy podrzędne `MySequence`, `MySequence` należy również śledzić miejsce, w którym jest wykonywane jego elementy podrzędne. W tym celu używa zmiennej `currentIndex`prywatnej. Ta zmienna `MySequence` jest zarejestrowana w ramach środowiska przez dodanie wywołania <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> <xref:System.Activities.Activity.CacheMetadata%2A> metody w `MySequence` metodzie działania. <xref:System.Activities.Activity> Obiekty dodane `MySequence` dokolekcjiniemogąuzyskaćdostępudozmiennychdodanych`Activities` w ten sposób.

 Gdy `MySequence` jest wykonywane przez środowisko uruchomieniowe, środowisko uruchomieniowe <xref:System.Activities.NativeActivity.Execute%2A> wywołuje jego <xref:System.Activities.NativeActivityContext>metodę, przekazując w. Jest to serwer proxy działania z powrotem do środowiska uruchomieniowego w celu usunięcia odwołań do argumentów i zmiennych, jak <xref:System.Activities.Activity> również do planowania innych obiektów lub `ActivityDelegates`. <xref:System.Activities.NativeActivityContext> `MySequence``InternalExecute` używa metody do hermetyzacji logiki pierwszego elementu podrzędnego i wszystkich kolejnych elementów podrzędnych w pojedynczej metodzie. Zaczyna się od odwołującego `currentIndex`się do. Jeśli wartość jest równa liczbie w `Activities` kolekcji, sekwencja zostanie zakończona, a działanie wraca bez planowania pracy i środowisko uruchomieniowe przenosi je <xref:System.Activities.ActivityInstanceState.Closed> do stanu. <xref:System.Activities.CompletionCallback> `MySequence` `Activities` `InternalExecute` <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>Jeśli wartość jestmniejszaniżliczbadziałań,następnyelementpodrzędnyjestuzyskiwanyzkolekcjiiwywołań,przekazywaniewelemenciepodrzędnymdozaplanowaniaiwskazujena`currentIndex` Method. Na koniec wartość `currentIndex` jest zwiększana, a kontrolka jest przywracana do środowiska uruchomieniowego. O ile wystąpienie `MySequence` ma obiekt podrzędny <xref:System.Activities.Activity> zaplanowano, środowisko uruchomieniowe traktuje je jako stan wykonywania.

 Po zakończeniu <xref:System.Activities.CompletionCallback> działania podrzędnego jest wykonywane. Pętla jest kontynuowana z góry. Podobnie `Execute`jak w <xref:System.Activities.CompletionCallback> przypadku, <xref:System.Activities.NativeActivityContext>gdy program ma dostęp do środowiska uruchomieniowego.

 `MyWhile`różni się `MySequence` od w tym, że planuje powtarzanie pojedynczego <xref:System.Activities.Activity> obiektu, a w tym <xref:System.Activities.Activity%601>przypadku używa\> < `Condition` bool o nazwie do określenia, czy ma być wykonywane planowanie. Podobnie `MySequence`jak `MyWhile` , używa`InternalExecute` metody do scentralizowania logiki planowania. Planuje `Condition` <xref:System.Activities.Activity>< bool\> z <xref:System.Activities.CompletionCallback%601>> bool o nazwie`OnEvaluationCompleted`. \< Po zakończeniu wykonywania `Condition` , jego wynik jest dostępny za pomocą tego <xref:System.Activities.CompletionCallback> parametru w parametrze o jednoznacznie określonym typie o `result`nazwie. Jeśli `true`, `MyWhile` wywołuje<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>,przekazuje obiekti`InternalExecute` jako .<xref:System.Activities.CompletionCallback> `Body` <xref:System.Activities.Activity> Po wykonaniu `Body` tej operacji program `Condition` zostanie ponownie zaplanowany w `InternalExecute`programie, co spowoduje ponowne uruchomienie pętli. `Condition` Gdy zwraca `false`, <xref:System.Activities.ActivityInstanceState.Closed> wystąpienie `MyWhile` daje`Body` kontrolę z powrotem do środowiska uruchomieniowego bez planowania, a środowisko uruchomieniowe przenosi je do stanu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Otwórz przykładowe złożone rozwiązanie. sln w programie Visual Studio 2010.

2. Kompiluj i uruchamiaj rozwiązanie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
