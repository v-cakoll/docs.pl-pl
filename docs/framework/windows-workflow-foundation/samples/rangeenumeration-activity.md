---
title: Działanie RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: 9aa04c80f20e2d410fb49e2d07d836c8c5ab1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516581"
---
# <a name="rangeenumeration-activity"></a>Działanie RangeEnumeration
Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przechodzi przez kolekcję liczb. W poniższej tabeli przedstawiono główne pliki uwzględnione w próbce.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|RangeEnumeration.cs|Definiuje niestandardowe działanie o nazwie `RangeEnumeration` który zastępuje <xref:System.Activities.NativeActivity> klasy i pętlę seria liczb.|  
|RangeEnumerationSample.cs|Aplikacji klienckiej, która używa `RangeEnumeration` działanie Iterowanie przez kolekcję liczb.|  
  
 W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|Uruchamianie|Liczba całkowita, można uruchomić z pętli.|  
|Zatrzymywanie|Liczba całkowita, można zatrzymać w pętli.|  
|Krok|Określa, ile dotyczące iteracji po każdym.|  
|Treści|Określa kod do wykonania podczas każdej iteracji.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`