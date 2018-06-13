---
title: 'Porady: tworzenie uczestnika trwałości niestandardowych'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: fcd96e41d8fc7b36f9dff5f10e9bc2d9034d79b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517244"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Porady: tworzenie uczestnika trwałości niestandardowych
Poniższa procedura zawiera kroki, aby utworzyć uczestnika trwałości. Zobacz [uczestniczących w trwałości](http://go.microsoft.com/fwlink/?LinkID=177735) próbki i [rozszerzalności magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) temat implementacji próbki uczestników trwałości.  
  
1.  Tworzenie klasy wywodzące się z <xref:System.Activities.Persistence.PersistenceParticipant> lub <xref:System.Activities.Persistence.PersistenceIOParticipant> klasy. Klasa PersistenceIOParticipant zapewnia tych samych punktów rozszerzalności jako klasa PersistenceParticipant oprócz możliwości uczestniczyć w operacji We/Wy. Wykonaj jedną lub więcej z następujących czynności.  
  
2.  Implementowanie <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> metody. **Obiektu CollectValues** metoda ma słownika dwa parametry: jeden do przechowywania wartości odczytu/zapisu, a drugi do przechowywania wartości tylko do zapisu (używane w dalszej części zapytania). W przypadku tej metody należy wypełnić słowników z danymi, które są specyficzne dla uczestnika trwałości. Każdy słownik zawiera nazwę wartości jako klucz i samą wartość jak <xref:System.Runtime.DurableInstancing.InstanceValue> obiektu.  
  
     Wartości w słowniku readWriteValues są dostarczane w **InstanceValue** obiektów. Wartości w słowniku tylko do zapisu są dostarczane w **InstanceValue** obiekty o InstanceValueOptions.Optional i InstanceValueOption.WriteOnly zestawu. Każdy **InstanceValue** dostarczonych przez **obiektu CollectValues** implementacje we wszystkich uczestników trwałości musi mieć unikatową nazwę.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementowanie <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> metody. **Obiektu MapValues** metoda przyjmuje dwa parametry, które są podobne do parametrów który **obiektu CollectValues** metoda. Wszystkie wartości są zbierane w **obiektu CollectValues** etap są przekazywane za pośrednictwem tych parametrów słownika. Nowe wartości dodane przez **obiektu MapValues** etapie zostaną dodane do wartości tylko do zapisu.  Słownik tylko do zapisu jest używany do dostarczania danych do źródła zewnętrznego nie są bezpośrednio związane z wartości wystąpienia. Wartości dostarczone przez implementacje **obiektu MapValues** metoda we wszystkich uczestników trwałości musi mieć unikatową nazwę.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Metoda zapewnia funkcje który <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> nie jest dostępne, w tym umożliwia zależność na innej wartości dostarczonej przez innego uczestnika trwałości, które nie zostały przetworzone przez <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> jeszcze.  
  
4.  Implementowanie **PublishValues** metody. **PublishValues** metody odbiera słownik zawierający wszystkie wartości załadowany z magazynu.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implementowanie **BeginOnSave** metodę, jeśli uczestnik jest uczestnika trwałości we/wy. Ta metoda jest wywoływana podczas operacji zapisu. W przypadku tej metody należy wykonać adjunct we/wy na przechowywanie (wystąpień przepływu pracy zapisanie).  Jeśli host używa transakcji do odpowiedniego polecenia trwałości, w operacji Transaction.Current znajduje się tej samej transakcji.  Ponadto PersistenceIOParticipants może anonsować wymaganie spójności transakcyjnej, w którym przypadku hosta tworzy transakcji dla epizodu trwałości, jeśli jeden czy nie w przeciwnym razie można użyć.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implementowanie **BeginOnLoad** metodę, jeśli uczestnik jest uczestnika trwałości we/wy. Ta metoda jest wywoływana podczas operacji ładowania. W przypadku tej metody należy wykonać we/wy adjunct ładowanie wystąpienia przepływu pracy. Jeśli host używa transakcji do odpowiedniego polecenia trwałości, w operacji Transaction.Current znajduje się tej samej transakcji. Ponadto uczestników trwałości we/wy może anonsować wymaganie spójności transakcyjnej, w którym przypadku hosta tworzy transakcji dla epizodu trwałości, jeśli jeden czy nie w przeciwnym razie można użyć.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
