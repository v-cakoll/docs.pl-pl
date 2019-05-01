---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004734"
---
# <a name="using-the-pick-activity"></a>Używanie działania Pick
W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Pick> działania.

 <xref:System.Activities.Statements.Pick> Działania zawiera kontrolki oparte na zdarzeniach modelowania. Zachowuje się podobnie jak C# `switch` instrukcję, która wykonuje tylko jeden z gałęzi, skorzystaj z `switch` instrukcji. W odróżnieniu od `switch` na podstawie instrukcji, w którym jest wykonywana gałąź na podstawie wartości <xref:System.Activities.Statements.Pick> działanie wykonuje gałęzi, w zależności od sposobu zakończy działanie.

 W tym przykładzie monituje użytkownika o wpisanie nazwy w konsoli w danym okresie czasu. <xref:System.Activities.Statements.Pick> Działanie w próbce ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik wpisze w ich imieniu w ciągu 5 sekund, czy nie. Jeśli użytkownik wpisze w ich imieniu w ciągu 5 sekund, zostanie wykonany pierwszej gałęzi, który zawiera niestandardowy `ReadLine` działanie; w przeciwnym razie innej gałęzi jest wykonywane, który zawiera <xref:System.Activities.Statements.Delay> działania. Po wpisaniu nazwy użytkownika w konsoli nazwy użytkownika jest drukowany w konsoli. Jeśli dane wejściowe nie zostanie wprowadzona w ciągu 5 sekund, operacja przekroczyła limit czasu.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.Activities.Statements.Pick> działanie.

## <a name="discussion"></a>Dyskusja
 Przykład obejmuje projektanta przepływu pracy i kodowany przepływu pracy.

 Projektanta Workflow Designer wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie. Uwzględnione są następujące pliki:

- Program.cs : Obejmuje `Main` funkcja, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.

- Sequence1.XAML: Przepływ pracy utworzony za pomocą projektanta, który używa wybierz.

 Kodowane przepływu pracy kodowane wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie. Uwzględnione są następujące pliki:

- Program.cs : Obejmuje `Main` funkcja, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania Pick.sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`