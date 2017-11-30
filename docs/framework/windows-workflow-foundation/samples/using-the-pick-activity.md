---
title: "Przy użyciu działaniu wybierz"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a95567afd955848b81bc343109acfe3fd138c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-pick-activity"></a>Przy użyciu działaniu wybierz
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Pick> działania.  
  
 <xref:System.Activities.Statements.Pick> Działania zawiera kontrolki oparte na zdarzeniu modelowania. Działa podobnie do języka C# `switch` instrukcji, która jest wykonywana tylko jednej z gałęzi w `switch` instrukcji. W odróżnieniu od `switch` na podstawie instrukcji, w którym jest wykonywane gałęzi przy użyciu wartości <xref:System.Activities.Statements.Pick> gałąź ustalane na podstawie sposobu kończy działanie wykonuje działania.  
  
 W tym przykładzie monituje użytkownika o wpisanie nazwy na konsoli w danym okresie. <xref:System.Activities.Statements.Pick> Działanie w próbce ma dwie gałęzie, które są ustalane na podstawie tego, czy użytkownik wpisze w ich imieniu w ciągu 5 sekund, czy nie. Jeśli użytkownik wpisze w ich imieniu w ciągu 5 sekund, jest wykonywane pierwszej gałęzi, który zawiera niestandardowy `ReadLine` działanie; w przeciwnym razie innej gałęzi jest wykonywane, który zawiera <xref:System.Activities.Statements.Delay> działania. Gdy nazwa użytkownika jest wpisany w konsoli, nazwa użytkownika jest drukowane na konsoli. Jeśli dane wejściowe nie została wprowadzona w ciągu 5 sekund, jest upłynął limit czasu operacji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.Pick>działanie.  
  
## <a name="discussion"></a>Omówienie  
 Przykład zawiera projektanta przepływów pracy i kodowanego przepływu pracy.  
  
 Projektant przepływu pracy  
 Wersja projektanta przykładowych pokazano, jak utworzyć przepływ pracy w projektancie. Zawarte są następujące pliki:  
  
-   Plik program.CS: Zawiera `Main` funkcji, która wykonuje przykładowego przepływu pracy.  
  
-   ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.  
  
-   Sequence1.XAML: Przepływ pracy utworzony za pomocą projektanta, który używa pobrania.  
  
 Kodowane przepływu pracy  
 Kodowane wersją przykładu przedstawia sposób tworzenia przepływu pracy w projektancie. Zawarte są następujące pliki:  
  
-   Plik program.CS: Zawiera `Main` funkcji, która wykonuje przykładowego przepływu pracy.  
  
-   ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Pick.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`  
  
## <a name="see-also"></a>Zobacz też
