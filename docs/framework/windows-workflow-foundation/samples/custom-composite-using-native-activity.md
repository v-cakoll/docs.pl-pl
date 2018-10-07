---
title: Niestandardowy element złożony przy użyciu działania Native
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 4d7cd64d5a7d581a81d10c39638b63f1f6787570
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840459"
---
# <a name="custom-composite-using-native-activity"></a>Niestandardowy element złożony przy użyciu działania Native
W tym przykładzie pokazano, jak napisać <xref:System.Activities.NativeActivity> planujące innych <xref:System.Activities.Activity> obiekty do sterowania przepływem wykonania przepływu pracy. W tym przykładzie użyto dwóch typowych przepływów sterowania sekwencjonowania i While, aby wykazać, jak to zrobić.

## <a name="sample-details"></a>Przykład szczegółów
 Począwszy od `MySequence`, jest przede wszystkim należy zauważyć, że pochodzi od <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> jest <xref:System.Activities.Activity> obiekt ujawniający pełnego zakresu środowiska wykonawczego przepływów pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> przekazany do `Execute` metody.

 `MySequence` udostępnia publiczne zbiór <xref:System.Activities.Activity> obiektów, które jest wypełniana przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowiska uruchomieniowego przepływu pracy wywołuje <xref:System.Activities.Activity.CacheMetadata%2A> metody na każde działanie w przepływie pracy. W trakcie tego procesu środowisko uruchomieniowe ustanawia relacje nadrzędny podrzędny, zakresu i czasu życia zarządzania danymi. Domyślna implementacja klasy <xref:System.Activities.Activity.CacheMetadata%2A> metoda używa <xref:System.ComponentModel.TypeDescriptor> wystąpienia klasy dla `MySequence` działanie, aby dodać wszystkie właściwość publiczną typu <xref:System.Activities.Activity> lub <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> jako elementy podrzędne `MySequence` działania.

 Po każdym działaniu udostępnia publiczne zbiór działania podrzędne, prawdopodobnie te działania podrzędne udostępnianie stanu. W tym przypadku jest najlepszym rozwiązaniem dla działania nadrzędnego `MySequence`, można także udostępnić to zbiór zmiennych, przez które działania podrzędne można to zrobić. Działania podrzędne, takie jak <xref:System.Activities.Activity.CacheMetadata%2A> metoda dodaje publicznymi właściwościami typu <xref:System.Activities.Variable> lub <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako zmienne skojarzone z `MySequence` działania.

 Oprócz publicznego zmiennych, które manipulowane przez elementy podrzędne `MySequence`, `MySequence` musi również śledzić, gdzie są dostępne w realizacji jego elementów podrzędnych. Używa zmienną prywatną `currentIndex`, w tym celu. Ta zmienna jest zarejestrowany jako część `MySequence` środowiska, dodając wywołania <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metodę w ramach `MySequence` działania <xref:System.Activities.Activity.CacheMetadata%2A> metody. <xref:System.Activities.Activity> Obiekty dodane do `MySequence` `Activities` kolekcji nie może uzyskać dostęp do zmiennych, dodane w ten sposób.

 Gdy `MySequence` jest wykonywany przez środowisko uruchomieniowe, środowisko uruchomieniowe wywołuje swoją <xref:System.Activities.NativeActivity.Execute%2A> metody, przekazując <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> To proxy działania Wstecz w czasie wykonywania wyłuskanie argumentów i zmiennych, jak również innych planowania <xref:System.Activities.Activity> obiektów, lub `ActivityDelegates`. `MySequence` używa `InternalExecute` metody do hermetyzacji logiki planowania pierwszego elementu podrzędnego, a wszystkie kolejne elementy podrzędne w jednej metody. Rozpoczyna wyłuskanie `currentIndex`. Jeśli jest taki sam, jak liczba `Activities` kolekcji, a następnie sekwencja zakończeniu zwracanych przez działanie bez żadnych działań do planowania i środowisko uruchomieniowe, przenosi je do <xref:System.Activities.ActivityInstanceState.Closed> stanu. Jeśli `currentIndex` jest mniejsza niż liczba działań, następny element podrzędny jest uzyskiwana z `Activities` kolekcji i `MySequence` wywołania <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazując podrzędnych do zaplanowania i <xref:System.Activities.CompletionCallback> wskazującego na `InternalExecute` Metoda. Na koniec `currentIndex` jest zwiększany i kontroli jest uzyskane z powrotem do środowiska uruchomieniowego. Tak długo, jak wystąpienie `MySequence` ma element podrzędny <xref:System.Activities.Activity> obiektu zaplanowane, środowisko uruchomieniowe uważa się on w stanie wykonywanie.

 Po ukończeniu działania podrzędnego <xref:System.Activities.CompletionCallback> jest wykonywany. Pętla jest kontynuowane od góry. Podobnie jak `Execute`, <xref:System.Activities.CompletionCallback> przyjmuje <xref:System.Activities.NativeActivityContext>, przyznawania dostępu implementujący w czasie wykonywania.

 `MyWhile` różni się od `MySequence` , planuje ona pojedynczy <xref:System.Activities.Activity> obiektu wielokrotnie, przy czym w tym <xref:System.Activities.Activity%601>< bool\> o nazwie `Condition` do określenia, czy to planowanie powinny być wykonywane. Podobnie jak `MySequence`, `MyWhile` używa `InternalExecute` metody, można scentralizować swojej logiki planowania. Planuje ona `Condition` <xref:System.Activities.Activity>< wartość logiczna\> z <xref:System.Activities.CompletionCallback%601> \<bool > o nazwie `OnEvaluationCompleted`. Podczas wykonywania `Condition` jest zakończone, jego wynik staje się dostępna za pośrednictwem to <xref:System.Activities.CompletionCallback> w silnie typizowane parametr o nazwie `result`. Jeśli `true`, `MyWhile` wywołania <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazując `Body` <xref:System.Activities.Activity> obiektu i `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Podczas wykonywania `Body` zakończeniu `Condition` pobiera zaplanowane ponownie w `InternalExecute`, rozpoczynanie pętli ponownie. Podczas `Condition` zwraca `false`, wystąpienie `MyWhile` zapewnia kontrolę powrót do środowiska uruchomieniowego bez planowania `Body` i środowisko uruchomieniowe przenosi jego <xref:System.Activities.ActivityInstanceState.Closed> stanu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Otwórz Composite.sln przykładowe rozwiązanie w programie Visual Studio 2010.

2.  Skompiluj i uruchom rozwiązanie.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`