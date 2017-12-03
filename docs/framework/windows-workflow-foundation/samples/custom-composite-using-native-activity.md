---
title: "Złożone niestandardowych za pomocą działania natywnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384904757e7e5e08f9f624d77d7cca990b3f093d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-using-native-activity"></a>Złożone niestandardowych za pomocą działania natywnego
W tym przykładzie pokazano, jak napisać <xref:System.Activities.NativeActivity> która planuje innych <xref:System.Activities.Activity> obiekty do sterowania przepływem wykonywania przepływu pracy. W przykładzie użyto dwóch typowych przepływami sterowania sekwencji i While, aby zademonstrować, jak to zrobić.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Począwszy od `MySequence`, jest przede wszystkim należy zauważyć, że pochodzi on z <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity>jest <xref:System.Activities.Activity> obiekt ujawniający rozmaitych środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> przekazany do `Execute` metody.  
  
 `MySequence`przedstawia kolekcję publicznego <xref:System.Activities.Activity> obiektów, które pobiera wypełnione przez autora przepływu pracy. Przed wykonaniem przepływu pracy środowiska uruchomieniowego przepływu pracy wywołuje <xref:System.Activities.Activity.CacheMetadata%2A> metody na każde działanie w przepływie pracy. W trakcie tego procesu środowiska uruchomieniowego ustanawia relacje nadrzędny podrzędny w celu zarządzania danymi zakresu i okresem istnienia. Domyślna implementacja <xref:System.Activities.Activity.CacheMetadata%2A> używa metody <xref:System.ComponentModel.TypeDescriptor> wystąpienia klasy dla `MySequence` działanie, aby dodać wszystkie właściwości publiczne typu <xref:System.Activities.Activity> lub <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> jako elementy podrzędne `MySequence` działania.  
  
 Zawsze, gdy działanie udostępnia publiczne zbiór działań podrzędnych, prawdopodobnie stanu udostępniania tych działań podrzędnych. W takim przypadku jest najlepszym rozwiązaniem dla działania nadrzędnego `MySequence`, aby również ujawniać kolekcję zmiennych za pomocą których działania podrzędne można to zrobić. Działania podrzędne, takich jak <xref:System.Activities.Activity.CacheMetadata%2A> metoda dodaje właściwości publiczne typu <xref:System.Activities.Variable> lub <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> jako zmienne skojarzone z `MySequence` działania.  
  
 Oprócz zmiennych publicznych, który manipulować przez element podrzędny elementu `MySequence`, `MySequence` musi również śledzić której jest wykonanie jego elementów podrzędnych. Używa zmiennej prywatnej `currentIndex`, w tym celu. Ta zmienna jest zarejestrowany jako część `MySequence` środowiska przez dodanie wywołanie <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> metody w `MySequence` działania <xref:System.Activities.Activity.CacheMetadata%2A> metody. <xref:System.Activities.Activity> Obiekty dodane do `MySequence` `Activities` kolekcji nie ma dostępu do zmiennych dodane w ten sposób.  
  
 Gdy `MySequence` jest wykonywany przez środowisko uruchomieniowe, wywołania środowiska uruchomieniowego jego <xref:System.Activities.NativeActivity.Execute%2A> metody, przekazując <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> To proxy działania do środowiska wykonawczego dereferencji argumentów i zmienne, a także innych planowania <xref:System.Activities.Activity> obiektów, lub `ActivityDelegates`. `MySequence`używa `InternalExecute` metody hermetyzacji logiki planowania pierwszy element podrzędny i wszystkie kolejne elementy podrzędne w pojedynczej metody. Rozpocznie się dereferencji `currentIndex`. Jeśli jest taka sama jak liczba `Activities` kolekcji, a następnie sekwencji jest zakończone, działanie zwraca bez planowania pracę i środowiska uruchomieniowego, przenosi je do <xref:System.Activities.ActivityInstanceState.Closed> stanu. Jeśli `currentIndex` jest mniejsza niż liczba działań podrzędnych dalej są uzyskiwane z `Activities` kolekcji i `MySequence` wywołania <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazując podrzędnej planowanych i <xref:System.Activities.CompletionCallback> wskazującego na `InternalExecute` Metoda. Na koniec `currentIndex` jest zwiększany i kontroli jest zwróciło wstecz do środowiska wykonawczego. Tak długo, jak wystąpienia `MySequence` ma element podrzędny <xref:System.Activities.Activity> obiektu zaplanowane, środowisko uruchomieniowe uważa się on w stanie wykonywanie.  
  
 Po ukończeniu działania podrzędnego <xref:System.Activities.CompletionCallback> jest wykonywana. Pętla kontynuuje od góry. Podobnie jak `Execute`, <xref:System.Activities.CompletionCallback> przyjmuje <xref:System.Activities.NativeActivityContext>, przyznawanie dostępu implementujący do środowiska wykonawczego.  
  
 `MyWhile`różni się od `MySequence` w tym planowana pojedynczy <xref:System.Activities.Activity> obiektu wielokrotnie, i że używa <xref:System.Activities.Activity%601>< bool\> o nazwie `Condition` do określenia, czy to planowanie powinna się odbyć. Podobnie jak `MySequence`, `MyWhile` używa `InternalExecute` metody, można scentralizować swojej logiki planowania. Planowana `Condition` <xref:System.Activities.Activity>< bool\> z <xref:System.Activities.CompletionCallback%601> \<bool > o nazwie `OnEvaluationCompleted`. Podczas wykonywania `Condition` jest zakończone, wynik staje się dostępna za pośrednictwem to <xref:System.Activities.CompletionCallback> w silnie typizowanym parametr o nazwie `result`. Jeśli `true`, `MyWhile` wywołania <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, przekazując `Body` <xref:System.Activities.Activity> obiektu i `InternalExecute` jako <xref:System.Activities.CompletionCallback>. Podczas wykonywania `Body` zakończeniu `Condition` pobiera zaplanowane ponownie w `InternalExecute`, rozpoczynanie pętli ponownie. Gdy `Condition` zwraca `false`, wystąpienie `MyWhile` zapewnia kontrolę wstecz do środowiska wykonawczego bez planowania `Body` i środowiska uruchomieniowego, przenosi je do <xref:System.Activities.ActivityInstanceState.Closed> stanu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie próbki Composite.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`