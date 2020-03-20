---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142618"
---
# <a name="using-the-pick-activity"></a>Używanie działania Pick
W tym przykładzie pokazano, jak używać <xref:System.Activities.Statements.Pick> działania.

 Działanie <xref:System.Activities.Statements.Pick> zapewnia modelowanie kontroli oparte na zdarzeniach. Zachowuje się podobnie do `switch` instrukcji C#, która wykonuje tylko jedną `switch` z gałęzi w instrukcji. W `switch` przeciwieństwie do instrukcji, w której gałąź jest wykonywana na podstawie wartości, <xref:System.Activities.Statements.Pick> działanie wykonuje gałąź na podstawie sposobu zakończenia działania.

 Ten przykład monituje użytkownika o wpisanie jego nazwy na konsoli w danym okresie czasu. Działanie <xref:System.Activities.Statements.Pick> w próbce ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik typów w ich nazwie w ciągu 5 sekund, czy nie. Jeśli użytkownik wpisuje w ich nazwie w ciągu 5 sekund, `ReadLine` pierwsza gałąź jest wykonywana, która zawiera działanie niestandardowe; w przeciwnym razie wykonywana jest <xref:System.Activities.Statements.Delay> inna gałąź, która zawiera działanie. Po wpisaniu nazwy użytkownika na konsoli, nazwa użytkownika jest drukowana na konsoli. Jeśli dane wejściowe nie zostanie wprowadzone w ciągu 5 sekund, upłynie limit czasu operacji.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.Activities.Statements.Pick>Działania.

## <a name="discussion"></a>Dyskusji
 Przykład zawiera przepływ pracy projektanta i kodowany przepływ pracy.

 Projekt projektanta Przepływ pracy Wersja projektanta przykładu pokazuje, jak utworzyć przepływ pracy w projektancie. Następujące pliki są zawarte:

- Program.cs : Zawiera `Main` funkcję, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: działanie niestandardowe, które odczytuje niektóre dane wejściowe z konsoli.

- Sequence1.xaml: Przepływ pracy utworzony przy użyciu projektanta, który używa pobrania.

 Kodowany przepływ pracy Zakodowana wersja przykładu pokazuje, jak utworzyć przepływ pracy w projektancie. Następujące pliki są zawarte:

- Program.cs : Zawiera `Main` funkcję, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: działanie niestandardowe, które odczytuje niektóre dane wejściowe z konsoli.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania Pick.sln.

2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
