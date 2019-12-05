---
title: 'Instrukcje: Tworzenie niestandardowego uczestnika trwałości'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 0e61395cb59a7d162668445d23241e3ff562d67b
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802547"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Instrukcje: Tworzenie niestandardowego uczestnika trwałości
Poniższa procedura zawiera kroki umożliwiające utworzenie uczestnika trwałości. Zapoznaj się z tematem [udział w](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100)) przykładowej trwałości i [rozszerzalności magazynu](store-extensibility.md) dla przykładowych implementacji uczestników trwałości.  
  
1. Utwórz klasę pochodną <xref:System.Activities.Persistence.PersistenceParticipant> lub klasy <xref:System.Activities.Persistence.PersistenceIOParticipant>. Klasa PersistenceIOParticipant oferuje te same punkty rozszerzalności, jak Klasa PersistenceParticipant, oprócz możliwości uczestniczenia w operacjach we/wy. Wykonaj co najmniej jeden z poniższych kroków.  
  
2. Zaimplementuj metodę <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>. Metoda **CollectValues** ma dwa parametry słownika: jeden do przechowywania wartości odczytu/zapisu i drugi do przechowywania wartości tylko do zapisu (używanych później w zapytaniach). W tej metodzie należy wypełnić te słowniki danymi, które są specyficzne dla uczestnika trwałości. Każdy słownik zawiera nazwę wartości jako klucz i wartość jako obiekt <xref:System.Runtime.DurableInstancing.InstanceValue>.  
  
    Wartości w słowniku readWriteValues są spakowane jako obiekty **InstanceValue** . Wartości w słowniku tylko do zapisu są pakowane jako obiekty **InstanceValue** z zestawem InstanceValueOptions. Optional i InstanceValueOption. WriteOnly. Każdy **InstanceValue** zapewniany przez implementacje **CollectValues** we wszystkich uczestnikach trwałości musi mieć unikatową nazwę.
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. Zaimplementuj metodę <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>. Metoda **MapValues** przyjmuje dwa parametry, które są podobne do parametrów, które odbiera Metoda **CollectValues** . Wszystkie wartości zebrane na etapie **CollectValues** są przesyłane za pomocą tych parametrów słownika. Nowe wartości dodawane przez etap **MapValues** są dodawane do wartości tylko do zapisu.  Słownik tylko do zapisu służy do dostarczania danych do zewnętrznego źródła, które nie jest bezpośrednio skojarzone z wartościami wystąpień. Każda wartość dostarczona przez implementacje metody **MapValues** we wszystkich uczestnikach trwałości musi mieć unikatową nazwę.  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     Metoda <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> zapewnia funkcję, która nie <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>, w tym, że umożliwia zależność od innej wartości dostarczonej przez innego uczestnika trwałości, który nie został jeszcze przetworzony przez <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>.  
  
4. Zaimplementuj metodę **PublishValues** . Metoda **PublishValues** odbiera słownik zawierający wszystkie wartości załadowane z magazynu trwałości.  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. Zaimplementuj metodę **BeginOnSave** , jeśli uczestnik jest uczestnikiem operacji we/wy o trwałości. Ta metoda jest wywoływana podczas operacji zapisywania. W tej metodzie należy wykonać adjunct we/wy do trwałych (oszczędności) wystąpień przepływu pracy.  Jeśli host używa transakcji dla odpowiedniego polecenia trwałości, ta sama transakcja jest podana w Transaction. Current.  Ponadto PersistenceIOParticipants może ogłaszać wymaganie spójności transakcyjnej, w takim przypadku host tworzy transakcję dla odcinka trwałości, jeśli nie będzie można jej użyć.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. Zaimplementuj metodę **BeginOnLoad** , jeśli uczestnik jest uczestnikiem operacji we/wy o trwałości. Ta metoda jest wywoływana podczas operacji ładowania. W tej metodzie należy wykonać adjunct we/wy, aby załadować wystąpienia przepływu pracy. Jeśli host używa transakcji dla odpowiedniego polecenia trwałości, ta sama transakcja jest podana w Transaction. Current. Ponadto w przypadku uczestników operacji we/wy może być ogłaszany wymóg spójności transakcyjnej, w takim przypadku host tworzy transakcję dla odcinka trwałości, jeśli nie będzie można jej użyć.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
