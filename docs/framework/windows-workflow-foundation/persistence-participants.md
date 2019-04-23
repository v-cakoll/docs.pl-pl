---
title: Uczestnicy stanów trwałych
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 18614962708eafa192d8163638fce2b8154d6106
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316365"
---
# <a name="persistence-participants"></a>Uczestnicy stanów trwałych
Uczestnika stanów trwałych mogą uczestniczyć w operacji trwałości (Zapisz lub obciążenia) wyzwolone przez aplikację hosta. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Jest dostarczany z dwóch klas abstrakcyjnych, **PersistenceParticipant** i **PersistenceIOParticipant**, którego można użyć do utworzenia uczestnika stanów trwałych. Uczestnika stanów trwałych pochodzi z jednej z tych klas, implementuje metody zainteresowań, a następnie dodaje wystąpienie klasy do <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> kolekcji na <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Host aplikacji może poszukaj takie rozszerzenia przepływu pracy po przechowywanie wystąpienia przepływu pracy i wywoływać właściwe metody na uczestnicy stanów trwałych we właściwym czasie.  
  
 Na poniższej liście opisano zadania wykonywane przez podsystem trwałości na różnych etapach operacji utrwalania (Zapisz). Uczestnicy stanów trwałych są używane w etapach trzecia i czwarta. Jeśli uczestnik uczestnika operacji We/Wy (trwałość uczestnika, który również uczestniczy w operacjach we/wy), uczestnika również służy szóstego etapu.  
  
1. Zbiera wartości wbudowanych, w tym stanu przepływu pracy, zakładek, zamapowanego zmienne i sygnatura czasowa.  
  
2. Zbiera wszystkie uczestnicy stanów trwałych, które zostały dodane do kolekcji rozszerzenie skojarzone z wystąpieniem przepływu pracy.  
  
3. Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metody implementowane przez wszystkich uczestników trwałości.  
  
4. Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metody implementowane przez wszystkich uczestników trwałości.  
  
5. Utrwalanie lub Zapisz przepływ pracy w magazynie w trwałości.  
  
6. Wywołuje <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> metody wszyscy uczestnicy stanów trwałych operacji We/Wy. Jeśli uczestnik nie jest uczestnikiem operacji We/Wy, to zadanie zostanie pominięte. Jeśli ten odcinek trwałości jest transakcyjna, transakcja jest podana we właściwości Transaction.Current.  
  
7. Czeka, aż wszyscy uczestnicy stanów trwałych do ukończenia. Jeśli uda się wszyscy uczestnicy utrwalanie dane wystąpienia, zatwierdzeń transakcji.  
  
 Pochodzi od klasy uczestnika stanów trwałych **PersistenceParticipant** klasy i mogą implementować **CollectValues** i **MapValues** metody. Trwałość operacji We/Wy uczestnika, który pochodzi od klasy **PersistenceIOParticipant** klasy i może wdrożyć **BeginOnSave** metoda oprócz Implementowanie **CollectValues**i **MapValues** metody.  
  
 Każdy z etapów zostało zakończone przed rozpoczęciem kolejnego etapu. Na przykład, wartości są zbierane z **wszystkich** uczestnicy stanów trwałych w pierwszym etapie. Następnie wszystkie wartości, które są zbierane w pierwszym etapie podano wszyscy uczestnicy stanów trwałych drugiego etapu dla mapowania. Następnie wszystkie wartości zbierane i mapowane na pierwszym i drugim etapie prowadzą zamieszczone linki do dostawcy stanów trwałych trzeciego etapu i tak dalej.  
  
 Na poniższej liście opisano zadania wykonywane przez podsystem trwałości na różnych etapach operacji ładowania. Uczestnicy stanów trwałych są używane w czwartym etapie. Uczestnicy operacji We/Wy stanów trwałych (Uczestnicy stanów trwałych, które także uczestniczyć w operacji We/Wy) są również używane w trzecim etapie.  
  
1. Zbiera wszystkie uczestnicy stanów trwałych, które zostały dodane do kolekcji rozszerzenie skojarzone z wystąpieniem przepływu pracy.  
  
2. Ładuje przepływu pracy w trwałości sklepie.  
  
3. Wywołuje <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> na wszystkich uczestnicy stanów trwałych operacji We/Wy i czeka na uczestnicy stanów trwałych do ukończenia. Jeśli ten odcinek trwałości jest transakcyjna, transakcja jest przekazywany w Transaction.Current.  
  
4. Ładuje wystąpienie przepływu pracy w oparciu o dane pobierane z magazynu stanu trwałego pamięci.  
  
5. Wywołuje <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> na każdym uczestnika stanów trwałych.  
  
 Pochodzi od klasy uczestnika stanów trwałych **PersistenceParticipant** klasy i mogą implementować **PublishValues** metody. Trwałość operacji We/Wy uczestnika, który pochodzi od klasy **PersistenceIOParticipant** klasy i może wdrożyć **BeginOnLoad** metoda oprócz Implementowanie **PublishValues**metody.  
  
 Podczas ładowania wystąpienia przepływu pracy dostawcy stanów trwałych tworzy blokady w tym wystąpieniu. Zapobiega to ładowany przez więcej niż jednego hosta w przypadku scenariusza z wieloma węzłami wystąpienia. Jeśli użytkownik podejmie próbę załadowania wystąpienia przepływu pracy, który został zablokowany pojawią się wyjątek, jak pokazano poniżej: Wyjątek "System.ServiceModel.Persistence.InstanceLockException: Nie można ukończyć żądanej operacji, ponieważ blokada na przykład "00000000-0000-0000-0000-000000000000" nie można uzyskać ". Ten błąd występuje, gdy wystąpi jedno z następujących czynności:  
  
-   W przypadku scenariusza z wieloma węzłami wystąpienie jest ładowany przez innego hosta.  Istnieje kilka różnych sposobów, aby rozwiązać tego rodzaju konfliktów: do przodu przetwarzania węzła, który posiada blokadę i spróbuj ponownie lub wymusić obciążona, co spowoduje, że innych hostów nie było możliwe zapisać swoją pracę.  
  
-   W scenariuszu jednym węzłem i host wystąpiła awaria.  Podczas uruchamiania hosta ponownie (odtworzenia procesu lub tworzenie nowej fabryki dostawcy trwałości) nowy host próbuje załadować wystąpienia, która nadal jest zablokowany przez stary hosta, ponieważ jeszcze nie wygasła blokady.  
  
-   W scenariuszu jednym węzłem, a wystąpienie danego zostało przerwane w pewnym momencie i tworzone jest nowe wystąpienie dostawcy stanów trwałych, która zawiera identyfikator innego hosta.  
  
 Wartość limitu czasu blokady ma wartość domyślną w ciągu 5 minut, można określić wartość limitu czasu różnych podczas wywoływania <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Instrukcje: Tworzenie niestandardowego uczestnika stanów trwałych](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzalność magazynu](store-extensibility.md)
