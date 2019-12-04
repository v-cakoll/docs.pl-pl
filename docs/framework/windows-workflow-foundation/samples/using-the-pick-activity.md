---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: b0997254615ca962fd386dea70c67a8edb36c90a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715525"
---
# <a name="using-the-pick-activity"></a>Używanie działania Pick
Ten przykład ilustruje sposób użycia działania <xref:System.Activities.Statements.Pick>.

 Działanie <xref:System.Activities.Statements.Pick> zapewnia modelowania kontroli opartej na zdarzeniach. Zachowuje się podobnie do instrukcji C# `switch`, która wykonuje tylko jedną z gałęzi w instrukcji `switch`. W przeciwieństwie do instrukcji `switch`, w której gałąź jest wykonywana na podstawie wartości, działanie <xref:System.Activities.Statements.Pick> wykonuje gałąź na podstawie sposobu ukończenia działania.

 Ten przykład poprosi użytkownika o wpisanie nazwy w konsoli w danym okresie czasu. Działanie <xref:System.Activities.Statements.Pick> w przykładzie ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik wpisze swoją nazwę w ciągu 5 sekund. Jeśli użytkownik wpisze swoją nazwę w ciągu 5 sekund, wykonywana jest pierwsza gałąź, która zawiera niestandardowe działanie `ReadLine`; w przeciwnym razie inna gałąź jest wykonywana, która zawiera <xref:System.Activities.Statements.Delay> działanie. Po wpisaniu nazwy użytkownika w konsoli programu nazwa użytkownika jest drukowana w konsoli programu. Jeśli dane wejściowe nie zostaną wprowadzone w ciągu 5 sekund, Operacja przekroczyła limit czasu.

## <a name="demonstrates"></a>Przedstawia
 działanie <xref:System.Activities.Statements.Pick>.

## <a name="discussion"></a>Dyskusji
 Przykład zawiera przepływ pracy projektanta i kodowany przepływ pracy.

 Przepływ pracy projektanta wersja projektanta przykład pokazuje, jak utworzyć przepływ pracy w projektancie. Dostępne są następujące pliki:

- Program.cs: zawiera funkcję `Main`, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.

- Sequence1. XAML: przepływ pracy utworzony przy użyciu projektanta, który używa funkcji pobrania.

 Kodowany przepływ pracy zakodowana wersja przykładu pokazuje, jak utworzyć przepływ pracy w projektancie. Dostępne są następujące pliki:

- Program.cs: zawiera funkcję `Main`, która wykonuje przykładowy przepływ pracy.

- ReadString.cs: niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania do pobrania. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
