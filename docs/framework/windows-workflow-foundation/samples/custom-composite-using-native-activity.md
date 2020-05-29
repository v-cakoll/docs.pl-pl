---
title: Niestandardowy element złożony przy użyciu działania Native
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: bf2b8123619df8977b0687c72663c6b482e35654
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200874"
---
# <a name="custom-composite-using-native-activity"></a>Niestandardowy element złożony przy użyciu działania Native
W tym przykładzie pokazano, jak napisać <xref:System.Activities.NativeActivity> harmonogram innych <xref:System.Activities.Activity> obiektów w celu sterowania przepływem wykonywania przepływu pracy. Ten przykład używa dwóch typowych przepływów sterowania, sekwencji i czasu, aby zademonstrować, jak to zrobić.

## <a name="sample-details"></a>Przykładowe szczegóły
 Począwszy od `MySequence` , najpierw należy zauważyć, że pochodzi on od <xref:System.Activities.NativeActivity> . <xref:System.Activities.NativeActivity>jest <xref:System.Activities.Activity> obiektem, który ujawnia pełną szerokość środowiska uruchomieniowego przepływu pracy przez <xref:System.Activities.NativeActivityContext> przekazaną do `Execute` metody.

 `MySequence`ujawnia publiczną kolekcję <xref:System.Activities.Activity> obiektów, które są wypełniane przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowisko uruchomieniowe przepływu pracy wywołuje <xref:System.Activities.Activity.CacheMetadata%2A> metodę dla każdego działania w przepływie pracy. W trakcie tego procesu środowisko uruchomieniowe ustanawia relacje nadrzędny-podrzędny do określania zakresu danych i zarządzania okresem istnienia. Domyślna implementacja <xref:System.Activities.Activity.CacheMetadata%2A> metody używa <xref:System.ComponentModel.TypeDescriptor> klasy wystąpienia dla `MySequence` działania, aby dodać jakąkolwiek publiczną właściwość typu <xref:System.Activities.Activity> lub <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Activity>> jako elementy podrzędne `MySequence` działania.

 Za każdym razem, gdy działanie ujawnia publiczną kolekcję działań podrzędnych, prawdopodobnie te działania podrzędne będą miały stan. Najlepszym rozwiązaniem dla działania nadrzędnego jest w tym przypadku `MySequence` ujawnienie kolekcji zmiennych, za pomocą których można wykonać działania podrzędne. Podobnie jak działania podrzędne, <xref:System.Activities.Activity.CacheMetadata%2A> Metoda dodaje publiczne właściwości typu <xref:System.Activities.Variable> lub <xref:System.Collections.IEnumerable> \<<xref:System.Activities.Variable>> jako zmienne skojarzone z `MySequence` działaniem.

 Poza zmiennymi publicznymi, które są manipulowane przez elementy podrzędne `MySequence` , `MySequence` należy również śledzić miejsce, w którym jest wykonywane jego elementy podrzędne. W tym celu używa zmiennej prywatnej `currentIndex` . Ta zmienna jest zarejestrowana w ramach `MySequence` środowiska przez dodanie wywołania <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metody w `MySequence` <xref:System.Activities.Activity.CacheMetadata%2A> metodzie działania. <xref:System.Activities.Activity>Obiekty dodane do `MySequence` `Activities` kolekcji nie mogą uzyskać dostępu do zmiennych dodanych w ten sposób.

 Gdy `MySequence` jest wykonywane przez środowisko uruchomieniowe, środowisko uruchomieniowe wywołuje jego <xref:System.Activities.NativeActivity.Execute%2A> metodę, przekazując w <xref:System.Activities.NativeActivityContext> . <xref:System.Activities.NativeActivityContext>Jest to serwer proxy działania z powrotem do środowiska uruchomieniowego w celu usunięcia odwołań do argumentów i zmiennych, jak również do planowania innych <xref:System.Activities.Activity> obiektów lub `ActivityDelegates` . `MySequence`używa `InternalExecute` metody do hermetyzacji logiki pierwszego elementu podrzędnego i wszystkich kolejnych elementów podrzędnych w pojedynczej metodzie. Zaczyna się od odwołującego się do `currentIndex` . Jeśli wartość jest równa liczbie w `Activities` kolekcji, sekwencja zostanie zakończona, a działanie wraca bez planowania pracy i środowisko uruchomieniowe przenosi je do <xref:System.Activities.ActivityInstanceState.Closed> stanu. Jeśli wartość `currentIndex` jest mniejsza niż liczba działań, następny element podrzędny jest uzyskiwany z `Activities` kolekcji i `MySequence` wywołań <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , co pozwala na zaplanowanie elementu podrzędnego i <xref:System.Activities.CompletionCallback> punkty w tej `InternalExecute` metodzie. Na koniec wartość `currentIndex` jest zwiększana, a kontrolka jest przywracana do środowiska uruchomieniowego. O ile wystąpienie `MySequence` ma <xref:System.Activities.Activity> obiekt podrzędny zaplanowano, środowisko uruchomieniowe traktuje je jako stan wykonywania.

 Po zakończeniu działania podrzędnego <xref:System.Activities.CompletionCallback> jest wykonywane. Pętla jest kontynuowana z góry. Podobnie jak w `Execute` przypadku, gdy program <xref:System.Activities.CompletionCallback> ma <xref:System.Activities.NativeActivityContext> dostęp do środowiska uruchomieniowego.

 `MyWhile`różni się od `MySequence` w tym, że planuje <xref:System.Activities.Activity> powtarzanie pojedynczego obiektu, a w tym przypadku używa <xref:System.Activities.Activity%601><bool \> o nazwie `Condition` do określenia, czy ma być wykonywane planowanie. Podobnie jak `MySequence` , `MyWhile` używa `InternalExecute` metody do scentralizowania logiki planowania. Planuje `Condition` <xref:System.Activities.Activity><bool \> o <xref:System.Activities.CompletionCallback%601> \<bool> nazwie `OnEvaluationCompleted` . Po `Condition` zakończeniu wykonywania, jego wynik jest dostępny za pomocą tego <xref:System.Activities.CompletionCallback> w parametrze o jednoznacznie określonym typie o nazwie `result` . Jeśli `true` , `MyWhile` wywołuje <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> , przekazuje `Body` <xref:System.Activities.Activity> obiekt i `InternalExecute` jako <xref:System.Activities.CompletionCallback> . Po wykonaniu tej operacji `Body` program zostanie `Condition` ponownie zaplanowany w programie, co spowoduje `InternalExecute` ponowne uruchomienie pętli. Gdy `Condition` zwraca `false` , wystąpienie `MyWhile` daje kontrolę z powrotem do środowiska uruchomieniowego bez planowania, `Body` a środowisko uruchomieniowe przenosi je do <xref:System.Activities.ActivityInstanceState.Closed> stanu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Otwórz przykładowe złożone rozwiązanie. sln w programie Visual Studio 2010.

2. Skompiluj i uruchom rozwiązanie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
