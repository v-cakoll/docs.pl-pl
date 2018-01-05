---
title: "Uczestnicy trwałości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b85acf2e3c4d885988e92948481182b7cf8c32c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-participants"></a>Uczestnicy trwałości
Uczestnika trwałości mogą uczestniczyć w operacji trwałości (Zapisz lub obciążenia) wyzwalane przez hosta aplikacji. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Jest dostarczany z dwóch klas abstrakcyjnych, **PersistenceParticipant** i **PersistenceIOParticipant**, które służy do tworzenia uczestnika trwałości. Uczestnika trwałości pochodzi z jednego z tych klas, implementuje metody zainteresowań, a następnie dodanie wystąpienia klasy do <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> kolekcji na <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Host aplikacji może wyglądać dla tych rozszerzeń przepływu pracy po trwałym wystąpienia przepływu pracy i wywołać odpowiednie metody uczestnika trwałości w odpowiednim czasie.  
  
 Na poniższej liście opisano zadania wykonywane przez podsystem trwałości na różnych etapach operacji utrwalania (Zapisz). Uczestnicy trwałości są używane w trzecim i czwartym etapach. Jeśli uczestnik jest uczestnika we/wy (trwałości uczestnika, który również uczestniczy w operacjach we/wy), uczestnik jest również używane w fazie szóstego.  
  
1.  Zbiera informacje o wbudowanych wartości, w tym stanu przepływu pracy, zakładki zamapowanych zmienne i sygnatura czasowa.  
  
2.  Zbiera informacje o wszystkich uczestników trwałości, które zostały dodane do kolekcji rozszerzeń skojarzonej z wystąpieniem przepływu pracy.  
  
3.  Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metoda zaimplementowana przez wszystkich uczestników trwałości.  
  
4.  Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metoda zaimplementowana przez wszystkich uczestników trwałości.  
  
5.  Utrwalić lub zapisać ten przepływ pracy w magazynie informacji o trwałości.  
  
6.  Wywołuje <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> metody dla wszystkich uczestników we/wy trwałości. Jeśli go nie ma uczestnika we/wy, to zadanie zostanie pominięte. Jeśli epizodu trwałości jest transakcyjna, transakcja jest świadczona w Właściwość Transaction.Current.  
  
7.  Czeka na zakończenie wszystkich uczestników trwałości. W przypadku wszystkich uczestników w trwałych danych wystąpienia, zatwierdza transakcji.  
  
 Uczestnika trwałości pochodną **PersistenceParticipant** klasy i może wdrożyć **obiektu CollectValues** i **obiektu MapValues** metody. We/Wy uczestnika trwałości pochodną **PersistenceIOParticipant** klasy i może wdrożyć **BeginOnSave** metodę oprócz wykonania **obiektu CollectValues**i **obiektu MapValues** metody.  
  
 Na każdym z etapów zostało ukończone przed rozpoczęciem kolejnego etapu. Na przykład wartości pochodzą z **wszystkie** uczestników trwałości podczas pierwszego etapu. Następnie wszystkie wartości zebranych podczas pierwszego etapu są przekazywane do wszystkich uczestników trwałości w drugim etapie mapowania. Następnie wszystkie wartości zbierane i zamapowana pierwszego i drugiego etapu są dostarczane do dostawcy trwałości w trzecim etapie i tak dalej.  
  
 Na poniższej liście opisano zadania wykonywane przez podsystem trwałości na różnych etapach operacji ładowania. Uczestnicy trwałości są używane w czwartym etapie. Trwałość uczestników we/wy (uczestników trwałości, które również uczestniczyć w operacji We/Wy) są również używane w trzecim etapie.  
  
1.  Zbiera informacje o wszystkich uczestników trwałości, które zostały dodane do kolekcji rozszerzeń skojarzonej z wystąpieniem przepływu pracy.  
  
2.  Ładuje przepływu pracy w sklepie trwałości.  
  
3.  Wywołuje <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> dla wszystkich uczestników we/wy trwałości i czeka na wszystkich uczestników trwałości do wykonania. Jeśli epizodu trwałości jest transakcyjna, transakcja znajduje się w operacji Transaction.Current.  
  
4.  Ładuje wystąpienia przepływu pracy w pamięci na podstawie danych pobrana z magazynu trwałości.  
  
5.  Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> na każdym uczestnika trwałości.  
  
 Uczestnika trwałości pochodną **PersistenceParticipant** klasy i może wdrożyć **PublishValues** metody. We/Wy uczestnika trwałości pochodną **PersistenceIOParticipant** klasy i może wdrożyć **BeginOnLoad** metodę oprócz wykonania **PublishValues**metody.  
  
 Podczas ładowania wystąpienia przepływu pracy dostawca trwałości tworzy blokady w tym wystąpieniu. Uniemożliwia to wystąpienie ładowany przez więcej niż jednego hosta w scenariuszu z wieloma węzłami. Jeśli próba załadowania wystąpienia przepływu pracy, który został zablokowany w sposób zobaczysz wyjątek podobnie do następującej: wyjątek "System.ServiceModel.Persistence.InstanceLockException: nie można ukończyć żądanej operacji, ponieważ blokady dla wystąpienia" 00000000-0000-0000-0000-000000000000 "nie można uzyskać". Ten błąd występuje, gdy wystąpi jedno z następujących czynności:  
  
-   W scenariuszu z wieloma węzłami wystąpienie jest załadowany przez innego hosta.  Istnieje kilka różnych sposobów, aby rozwiązać konfliktów tego typu: przekazywania przetwarzania do węzła, który jest właścicielem blokady i spróbuj ponownie lub wymusić obciążenia, co spowoduje innych hostów można będzie zapisanie pracy.  
  
-   W scenariuszu jednym węzłem i host awaria.  Po uruchomieniu hosta ponownie (odtworzenia procesu lub tworzenia nowych fabryki dostawców trwałości) nowy host próbuje załadować do wystąpienia, które nadal jest zablokowany przez stary host, ponieważ blokada nie jeszcze wygasł.  
  
-   W scenariuszu jednym węzłem i wystąpieniem zagrożona zostało przerwane w pewnym momencie i jest tworzony nowe wystąpienie dostawcy trwałości, który ma identyfikator inny host.  
  
 Wartość limitu czasu blokady ma wartość domyślna wynosi 5 minut, można określić wartość innego limitu czasu podczas wywoływania metody <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Instrukcje: Tworzenie niestandardowego uczestnika stanów trwałych](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)
