---
title: Niestandardowy element złożony przy użyciu działania Native
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 57c724ad55c3aa2960e9a2d11fcd8419a94a0c72
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715175"
---
# <a name="custom-composite-using-native-activity"></a>Niestandardowy element złożony przy użyciu działania Native
Ten przykład pokazuje, jak napisać <xref:System.Activities.NativeActivity>, który planuje inne obiekty <xref:System.Activities.Activity> do sterowania przepływem wykonywania przepływu pracy. Ten przykład używa dwóch typowych przepływów sterowania, sekwencji i czasu, aby zademonstrować, jak to zrobić.

## <a name="sample-details"></a>Przykładowe szczegóły
 Rozpoczynając od `MySequence`, najpierw należy zauważyć, że pochodzi on z <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> jest obiektem <xref:System.Activities.Activity>, który uwidacznia pełną szerokość środowiska uruchomieniowego przepływu pracy przez <xref:System.Activities.NativeActivityContext> przekazaną do metody `Execute`.

 `MySequence` uwidacznia publiczną kolekcję obiektów <xref:System.Activities.Activity>, które są wypełniane przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowisko uruchomieniowe przepływu pracy wywołuje metodę <xref:System.Activities.Activity.CacheMetadata%2A> dla każdego działania w przepływie pracy. W trakcie tego procesu środowisko uruchomieniowe ustanawia relacje nadrzędny-podrzędny do określania zakresu danych i zarządzania okresem istnienia. Domyślna implementacja metody <xref:System.Activities.Activity.CacheMetadata%2A> używa klasy wystąpienia <xref:System.ComponentModel.TypeDescriptor> dla działania `MySequence`, aby dodać jakąkolwiek publiczną właściwość typu <xref:System.Activities.Activity> lub <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Activity>, > jako elementy podrzędne działania `MySequence`.

 Za każdym razem, gdy działanie ujawnia publiczną kolekcję działań podrzędnych, prawdopodobnie te działania podrzędne będą miały stan. Najlepszym rozwiązaniem dla działania nadrzędnego jest w tym przypadku `MySequence`, aby również uwidocznić kolekcję zmiennych, za pomocą których można wykonać działania podrzędne. Podobnie jak działania podrzędne, Metoda <xref:System.Activities.Activity.CacheMetadata%2A> dodaje publiczne właściwości typu <xref:System.Activities.Variable> lub <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Variable>> jako zmienne skojarzone z działaniem `MySequence`.

 Poza zmiennymi publicznymi, które są manipulowane przez elementy podrzędne `MySequence`, `MySequence` muszą również śledzić miejsce, w którym jest wykonywane jego elementy podrzędne. W tym celu używa zmiennej prywatnej, `currentIndex`. Ta zmienna jest zarejestrowana w ramach środowiska `MySequence` przez dodanie wywołania metody <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> w ramach metody <xref:System.Activities.Activity.CacheMetadata%2A> działania `MySequence`. Obiekty <xref:System.Activities.Activity> dodane do kolekcji `MySequence` `Activities` nie mogą uzyskać dostępu do zmiennych dodanych w ten sposób.

 Gdy `MySequence` jest wykonywane przez środowisko uruchomieniowe, środowisko uruchomieniowe wywołuje metodę <xref:System.Activities.NativeActivity.Execute%2A>, przekazując w <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> to serwer proxy działania z powrotem do środowiska uruchomieniowego w celu usunięcia odwołań do argumentów i zmiennych, jak również do planowania innych obiektów <xref:System.Activities.Activity> lub `ActivityDelegates`. `MySequence` używa metody `InternalExecute` do hermetyzowania logiki pierwszego elementu podrzędnego i wszystkich kolejnych elementów podrzędnych w pojedynczej metodzie. Zaczyna się od odwołującego się do `currentIndex`. Jeśli wartość jest równa liczbie w kolekcji `Activities`, sekwencja zostanie zakończona, a działanie zwróci wartość bez planowania pracy i środowisko uruchomieniowe przenosi je do stanu <xref:System.Activities.ActivityInstanceState.Closed>. Jeśli `currentIndex` jest mniejsza niż liczba działań, następny element podrzędny jest uzyskiwany z kolekcji `Activities` i wywołań `MySequence` <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazywanie w celu zaplanowania elementu podrzędnego i <xref:System.Activities.CompletionCallback> wskazujące na metodę `InternalExecute`. Na koniec `currentIndex` jest zwiększany, a sterowanie jest przywracane do środowiska uruchomieniowego. Tak długo, jak wystąpienie `MySequence` ma obiekt podrzędny <xref:System.Activities.Activity> zaplanowano, środowisko uruchomieniowe traktuje je jako stan wykonywania.

 Po zakończeniu działania podrzędnego <xref:System.Activities.CompletionCallback> jest wykonywane. Pętla jest kontynuowana z góry. Podobnie jak `Execute`, <xref:System.Activities.CompletionCallback> pobiera <xref:System.Activities.NativeActivityContext>, zapewniając dostęp implementujący do środowiska uruchomieniowego.

 `MyWhile` różni się od `MySequence` w tym, że wielokrotnie planuje pojedynczy <xref:System.Activities.Activity> obiekt, a w tym przypadku używa <xref:System.Activities.Activity%601>< bool\> o nazwie `Condition`, aby określić, czy ma być wykonywane planowanie. Podobnie jak `MySequence`, `MyWhile` używa metody `InternalExecute` do scentralizowania logiki planowania. Planuje `Condition`<xref:System.Activities.Activity>< bool\> z <xref:System.Activities.CompletionCallback%601>\<bool > o nazwie `OnEvaluationCompleted`. Po zakończeniu wykonywania `Condition` jego wynik zostanie udostępniony za pomocą tego <xref:System.Activities.CompletionCallback> w parametrze o jednoznacznie określonym typie o nazwie `result`. Jeśli `true`, `MyWhile` wywołania <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazując w `Body`<xref:System.Activities.Activity> obiektu i `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Po zakończeniu wykonywania `Body` `Condition` ponownie zostanie zaplanowana w `InternalExecute`, co spowoduje ponowne uruchomienie pętli. Gdy `Condition` zwraca `false`, wystąpienie `MyWhile` zapewnia kontrolę z powrotem do środowiska uruchomieniowego bez planowania `Body`, a środowisko uruchomieniowe przenosi je do stanu <xref:System.Activities.ActivityInstanceState.Closed>.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Otwórz przykładowe złożone rozwiązanie. sln w programie Visual Studio 2010.

2. Kompiluj i uruchamiaj rozwiązanie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
