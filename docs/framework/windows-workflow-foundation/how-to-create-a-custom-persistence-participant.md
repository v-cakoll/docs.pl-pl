---
title: 'Porady: Tworzenie niestandardowego uczestnika stanów trwałych'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 8daf4924db48c79486e85660357e3b28a2583836
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855845"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Porady: Tworzenie niestandardowego uczestnika stanów trwałych
Poniższa procedura zawiera kroki, aby utworzyć uczestnika stanów trwałych. Zobacz [uczestniczących w trwałości](https://go.microsoft.com/fwlink/?LinkID=177735) próbki i [rozszerzalności Store](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tematu w przykładowej implementacji uczestnicy stanów trwałych.  
  
1.  Utwórz klasę pochodząca od <xref:System.Activities.Persistence.PersistenceParticipant> lub <xref:System.Activities.Persistence.PersistenceIOParticipant> klasy. Klasa PersistenceIOParticipant zapewnia ten sam punkty rozszerzeń jako klasa PersistenceParticipant, oprócz możliwości udziału w operacji We/Wy. Postępuj zgodnie z co najmniej jeden z następujących czynności.  
  
2.  Implementowanie <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metody. **CollectValues** metoda ma słownika dwa parametry: jeden do przechowywania wartości odczytu/zapisu, a druga do przechowywania wartości tylko do zapisu (używane w dalszej części zapytania). W przypadku tej metody należy wypełnić słowników z danymi, które są specyficzne dla uczestnika stanów trwałych. Każdy słownik zawiera nazwę wartości klucza oraz sama wartość jak <xref:System.Runtime.DurableInstancing.InstanceValue> obiektu.  
  
     Wartości w słowniku readWriteValues są dostarczane w **InstanceValue** obiektów. Wartości w słowniku tylko do zapisu jest spakowany jako **InstanceValue** obiektów z InstanceValueOptions.Optional i InstanceValueOption.WriteOnly zestawu. Każdy **InstanceValue** dostarczone przez **CollectValues** implementacje we wszystkich uczestników stanu trwałego musi mieć unikatową nazwę.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementowanie <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metody. **MapValues** metoda przyjmuje dwa parametry, które są podobne do parametrów, **CollectValues** metoda otrzymuje. Wszystkie wartości są zbierane w **CollectValues** etapu są przekazywane za pośrednictwem tych parametrów słownika. Nowe wartości dodanej przez **MapValues** etapu są dodawane do wartości tylko do zapisu.  Słownik tylko do zapisu jest używany do przekazywania danych do zewnętrznego źródła, nie są bezpośrednio związane z wartości wystąpienia. Każdej wartości dostarczone przez implementacje **MapValues** metoda we wszystkich uczestników stanu trwałego musi mieć unikatową nazwę.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Metoda oferuje funkcje, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> nie, w tym, że umożliwia ona zależność od innej wartości, dostarczone przez inną uczestnika stanów trwałych, które nie zostały przetworzone przez <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> jeszcze.  
  
4.  Implementowanie **PublishValues** metody. **PublishValues** metoda otrzymuje słownik zawierający wszystkie wartości, które są ładowane w trwałości sklepie.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implementowanie **BeginOnSave** metodę, jeśli uczestnik jest uczestnika stanów trwałych operacji We/Wy. Ta metoda jest wywoływana podczas operacji zapisu. W przypadku tej metody należy wykonać adjunct operacji We/Wy do utrwalania (wystąpienia przepływu pracy zapisywanie).  Jeśli host używa transakcji do odpowiedniego polecenia trwałości, Transaction.Current jest podawany tej samej transakcji.  Ponadto PersistenceIOParticipants może anonsować wymagane spójności transakcyjnej, w których przypadku hosta tworzy transakcji dla odcinek trwałości, jeśli jeden będzie nie używane.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implementowanie **BeginOnLoad** metodę, jeśli uczestnik jest uczestnika stanów trwałych operacji We/Wy. Ta metoda jest wywoływana podczas operacji ładowania. W przypadku tej metody należy wykonywać operacji We/Wy adjunct ładowanie wystąpienia przepływu pracy. Jeśli host używa transakcji do odpowiedniego polecenia trwałości, Transaction.Current jest podawany tej samej transakcji. Ponadto uczestnicy stanów trwałych operacji We/Wy może anonsować wymagane spójności transakcyjnej, w których przypadku hosta tworzy transakcji dla odcinek trwałości, jeśli jeden będzie nie używane.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
