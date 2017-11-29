---
title: "Działanie RangeEnumeration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 024cdc9ae082171fb33a63493ac0fbfdd45d3c72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`  
  
## <a name="see-also"></a>Zobacz też
