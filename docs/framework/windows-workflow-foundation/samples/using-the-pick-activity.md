---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037881"
---
# <a name="using-the-pick-activity"></a>Używanie działania Pick
Ten przykład pokazuje, <xref:System.Activities.Statements.Pick> jak używać działania.

 <xref:System.Activities.Statements.Pick> Działanie zapewnia modelowania kontroli opartej na zdarzeniach. Zachowuje się podobnie do C# `switch` instrukcji, która wykonuje tylko jedną z gałęzi w `switch` instrukcji. W przeciwieństwie `switch` do instrukcji <xref:System.Activities.Statements.Pick> , w której rozgałęzienie jest wykonywane na podstawie wartości, działanie wykonuje gałąź w oparciu o zakończenie działania.

 Ten przykład poprosi użytkownika o wpisanie nazwy w konsoli w danym okresie czasu. <xref:System.Activities.Statements.Pick> Działanie w przykładzie ma dwie gałęzie, które są wykonywane w zależności od tego, czy użytkownik wpisze swoją nazwę w ciągu 5 sekund. Jeśli użytkownik wpisze swoją nazwę w ciągu 5 sekund, wykonywana jest pierwsza gałąź, która zawiera działanie niestandardowe `ReadLine` ; w przeciwnym razie inna gałąź jest wykonywana, która <xref:System.Activities.Statements.Delay> zawiera działanie. Po wpisaniu nazwy użytkownika w konsoli programu nazwa użytkownika jest drukowana w konsoli programu. Jeśli dane wejściowe nie zostaną wprowadzone w ciągu 5 sekund, Operacja przekroczyła limit czasu.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.Activities.Statements.Pick>interakcyjn.

## <a name="discussion"></a>Dyskusji
 Przykład zawiera przepływ pracy projektanta i kodowany przepływ pracy.

 Przepływ pracy projektanta wersja projektanta przykład pokazuje, jak utworzyć przepływ pracy w projektancie. Dostępne są następujące pliki:

- Program.cs: `Main` Zawiera funkcję, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.

- Sequence1. XAML: Przepływ pracy utworzony przy użyciu projektanta, który używa funkcji pobrania.

 Kodowany przepływ pracy zakodowana wersja przykładu pokazuje, jak utworzyć przepływ pracy w projektancie. Dostępne są następujące pliki:

- Program.cs: `Main` Zawiera funkcję, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania do pobrania. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
