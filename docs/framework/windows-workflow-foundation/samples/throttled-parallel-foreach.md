---
title: Działanie ThrottledParallelForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715921"
---
# <a name="throttled-parallel-foreach"></a>Działanie ThrottledParallelForEach

Działanie `ThrottleParallelForEach` jest podobne do działania <xref:System.Activities.Statements.ParallelForEach%601> z jedynym wyjątkiem, że umożliwia ustawienie współczynnika współbieżności, aby ograniczyć liczbę równoczesnych gałęzi do wykonania. Działanie `ThrottleParallelForEach` pochodzi od <xref:System.Activities.NativeActivity>, ponieważ wymaga zaplanowania innych działań (działania podrzędne) i jest dostępne tylko za pośrednictwem klasy <xref:System.Activities.NativeActivityContext>.

## <a name="projects"></a>Projekty

|**ProjectName**|**Opis**|**Pliki główne**|
|-|-|-|
|ThrottledParallelForEach|Zawiera `ThrottledParallelForEach` działanie i jego projektanta.|ThrottledParallelForEach.cs<br /><br /> Definicja działania `ThrottledParallelForEach`.|
|CodeTestClient|Przykładowa aplikacja kliencka, która konfiguruje i uruchamia przepływ pracy z `ThrottledParallelForEach` przy użyciu kodu bezwzględnego.|Program.cs<br /><br /> Definiuje i uruchamia wystąpienie przykładowego przepływu pracy.|

## <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik ThrottledParallelForEach. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
