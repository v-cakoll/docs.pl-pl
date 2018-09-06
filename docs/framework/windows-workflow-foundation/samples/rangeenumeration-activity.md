---
title: Działanie RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868721"
---
# <a name="rangeenumeration-activity"></a>Działanie RangeEnumeration
W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, który iteruje po kolekcji liczb. W poniższej tabeli przedstawiono główne pliki zawarte w przykładzie.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|RangeEnumeration.cs|Definiuje niestandardowe działanie o nazwie `RangeEnumeration` , zastępuje <xref:System.Activities.NativeActivity> klasy i pętle w kolejnych seriach liczb.|  
|RangeEnumerationSample.cs|Aplikacja kliencka, która używa `RangeEnumeration` działania do iteracji przez kolekcję liczb.|  
  
 W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|Uruchamianie|Liczba całkowita, aby rozpocząć pętli z.|  
|Zatrzymywanie|Liczba całkowita, aby zatrzymać pętlę w.|  
|Krok|Określa, ile iteracyjne każdorazowo.|  
|Treść|Określa kod, do wykonania podczas każdej iteracji.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`