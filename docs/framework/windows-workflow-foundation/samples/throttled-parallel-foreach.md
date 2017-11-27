---
title: "Ograniczeniem przepustowości ForEach równoległych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c8336060be48f55b974960e67ca1ebc57e76c63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="throttled-parallel-foreach"></a>Ograniczeniem przepustowości ForEach równoległych
`ThrottleParallelForEach` Działanie przypomina <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` działania z jednym wyjątkiem jego umożliwia ustawienie współczynnika współbieżności do ograniczenia liczby równoczesnych gałęzi do wykonania. `ThrottleParallelForEach` Działania jest pochodną <xref:System.Activities.NativeActivity>, ponieważ należy ją zaplanować inne działania (działań podrzędnych) i ten jest dostępny tylko za pośrednictwem <xref:System.Activities.NativeActivityContext> klasy.  
  
## <a name="projects"></a>Projekty  
  
|**ProjectName**|**Opis**|**Główne pliki**|  
|-|-|-|  
|ThrottledParallelForEach|Zawiera `ThrottledParallelForEach` działanie i jego projektanta.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` Definicji działania.|  
|CodeTestClient|Przykładowa aplikacja klienta, który konfiguruje i uruchamia przepływ pracy o `ThrottledParallelForEach` przy użyciu kodu nadrzędnych.|Plik program.CS<br /><br /> Definiuje i uruchomione jest wystąpienie przykładowy przepływ pracy.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ThrottledParallelForEach.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`  
  
## <a name="see-also"></a>Zobacz też
