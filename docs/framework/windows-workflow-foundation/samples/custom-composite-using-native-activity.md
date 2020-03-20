---
title: Niestandardowy element złożony przy użyciu działania Native
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 2b922ef721ab4d125f390e908eb8ea4d3b087035
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142800"
---
# <a name="custom-composite-using-native-activity"></a>Niestandardowy element złożony przy użyciu działania Native
W tym przykładzie pokazano, jak <xref:System.Activities.NativeActivity> <xref:System.Activities.Activity> napisać, że planuje inne obiekty do kontrolowania przepływu wykonywania przepływu pracy. W tym przykładzie użyto dwóch typowych przepływów kontroli, Sequence i While, aby zademonstrować, jak to zrobić.

## <a name="sample-details"></a>Przykładowe szczegóły
 Począwszy `MySequence`od , pierwszą rzeczą, aby <xref:System.Activities.NativeActivity>zauważyć, że pochodzi od . <xref:System.Activities.NativeActivity>jest <xref:System.Activities.Activity> obiektem, który udostępnia pełny zakres środowiska wykonawczego <xref:System.Activities.NativeActivityContext> przepływu pracy `Execute` za pośrednictwem przekazany do metody.

 `MySequence`udostępnia publiczną kolekcję <xref:System.Activities.Activity> obiektów, która zostanie wypełniona przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowisko uruchomieniowe <xref:System.Activities.Activity.CacheMetadata%2A> przepływu pracy wywołuje metodę dla każdego działania w przepływie pracy. Podczas tego procesu środowisko wykonawcze ustanawia relacje nadrzędny podrzędny dla zakresu danych i zarządzania okresem istnienia. Domyślna implementacja <xref:System.Activities.Activity.CacheMetadata%2A> metody używa <xref:System.ComponentModel.TypeDescriptor> klasy wystąpienia `MySequence` dla działania, aby <xref:System.Activities.Activity> dodać <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity> dowolną własność publiczną `MySequence` typu lub> jako element podrzędny działania.

 Za każdym razem, gdy działanie udostępnia publicznej kolekcji działań podrzędnych, jest prawdopodobne, że te działania podrzędne współużytkują stan. Jest to najlepsza praktyka dla działania `MySequence`nadrzędnego, w tym przypadku, aby również udostępnić kolekcję zmiennych, za pomocą których działania podrzędne można to osiągnąć. Podobnie jak działania <xref:System.Activities.Activity.CacheMetadata%2A> podrzędne, metoda dodaje <xref:System.Activities.Variable> <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable> właściwości publiczne typu lub> jako `MySequence` zmienne skojarzone z działaniem.

 Oprócz zmiennych publicznych, które są manipulowane `MySequence` `MySequence` przez dzieci , musi również śledzić, gdzie jest w wykonywaniu swoich dzieci. Używa zmiennej prywatnej, `currentIndex`aby to osiągnąć. Ta zmienna jest rejestrowana jako `MySequence` część środowiska <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> przez `MySequence` dodanie wywołania metody w ramach <xref:System.Activities.Activity.CacheMetadata%2A> metody działania. Obiekty <xref:System.Activities.Activity> dodane do `MySequence` `Activities` kolekcji nie mogą uzyskać dostępu do zmiennych dodanych w ten sposób.

 Gdy `MySequence` jest wykonywany przez środowisko wykonawcze, <xref:System.Activities.NativeActivity.Execute%2A> środowisko uruchomieniowe wywołuje jego metodę, przekazując w . <xref:System.Activities.NativeActivityContext> Jest <xref:System.Activities.NativeActivityContext> to serwer proxy działania z powrotem do środowiska wykonawczego dla argumentów i <xref:System.Activities.Activity> zmiennych `ActivityDelegates`dereferencji, a także planowania innych obiektów lub . `MySequence`używa `InternalExecute` metody do hermetyzacji logiki planowania pierwszego dziecka i wszystkich kolejnych obrażeń podrzędnych w jednej metodzie. Zaczyna się od dereferencing `currentIndex`. Jeśli jest równa liczbie w `Activities` kolekcji, a następnie sekwencja jest zakończona, działanie zwraca bez planowania <xref:System.Activities.ActivityInstanceState.Closed> żadnej pracy i środowisko wykonawcze przenosi go do stanu. Jeśli `currentIndex` jest mniejsza niż liczba działań, następne dziecko `Activities` jest `MySequence` uzyskiwane z kolekcji i <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> <xref:System.Activities.CompletionCallback> wywołuje , `InternalExecute` przekazując w dziecko do zaplanowania i że punkty w metodzie. Na koniec `currentIndex` jest zwiększane i kontroli jest yielded z powrotem do środowiska wykonawczego. Tak długo, jak `MySequence` wystąpienie <xref:System.Activities.Activity> ma obiekt podrzędny zaplanowane, środowisko wykonawcze uważa, że jest w stanie wykonywania.

 Po zakończeniu działania podrzędnego <xref:System.Activities.CompletionCallback> jest wykonywana. Pętla jest kontynuowana od góry. Like `Execute`, <xref:System.Activities.CompletionCallback> a <xref:System.Activities.NativeActivityContext>takes an , dając realizatorowi dostęp do środowiska wykonawczego.

 `MyWhile`różni się `MySequence` tym, że planuje <xref:System.Activities.Activity> pojedynczy obiekt wielokrotnie i w <xref:System.Activities.Activity%601> tym używa<\> bool nazwie, `Condition` aby ustalić, czy to planowanie powinno wystąpić. Like `MySequence` `MyWhile` , używa `InternalExecute` metody do scentralizowania logiki planowania. `Condition` <xref:System.Activities.Activity> Planuje<\> bool z <xref:System.Activities.CompletionCallback%601> \<bool> nazwie `OnEvaluationCompleted`. Po zakończeniu `Condition` wykonywania jego wynik staje się <xref:System.Activities.CompletionCallback> dostępny za pośrednictwem tego `result`w silnie typizowanym parametrze o nazwie . Jeśli `true` `MyWhile` , <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>wywołuje , `Body` <xref:System.Activities.Activity> przechodząc `InternalExecute` w <xref:System.Activities.CompletionCallback>obiekcie i jako . Po `Body` zakończeniu, `Condition` zostanie zaplanowane ponownie w `InternalExecute`, uruchamianie pętli na nowo. Po `Condition` `false`zwróceniu , `MyWhile` wystąpienie daje kontrolę z powrotem do środowiska wykonawczego bez planowania `Body` i środowiska wykonawczego przenosi go do <xref:System.Activities.ActivityInstanceState.Closed> stanu.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Otwórz przykładowe rozwiązanie Composite.sln w programie Visual Studio 2010.

2. Skompiluj i uruchom rozwiązanie.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
