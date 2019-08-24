---
title: Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016018"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch

Ten przykład pokazuje, <xref:System.Activities.Statements.TryCatch> jak działanie może być używane w ramach działania przepływu sterowania złożonego.

W tym przykładzie kod promocyjny i liczba elementów podrzędnych są przesyłane jako zmienne do <xref:System.Activities.Statements.Flowchart> działania, które oblicza rabat na podstawie formuły odpowiadającej kodowi promocji. Przykład obejmuje bezwzględny kod i wersje projektanta przepływu pracy dla przykładu.

W poniższej tabeli przedstawiono zmienne dla `CreateFlowchartWithFaults` działania.

|Parametry|Opis|
|----------------|-----------------|
|promoCode|Kod promocyjny. Wpisz: String<br /><br /> Możliwe wartości z opisem w nawiasach:<br /><br /> -Pojedyncza (pojedyncza)<br />-MNK (ślub bez dzieci)<br />-MWK (ślub z dziecięcymi).|
|numKids|Liczba elementów podrzędnych. Typ: int|

`CreateFlowchartWithFaults` Działanie używa`promoCode` działania, które przełącza argument i oblicza rabat przy użyciu następującej formuły. <xref:System.Activities.Statements.FlowSwitch%601>

|Wartość`promoCode`|Rabat (%)|
|--------------------------|--------------------|
|Single|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Uwaga:**  Może to spowodować wygenerowanie <xref:System.DivideByZeroException>. W związku z tym obliczanie rabatu jest opakowane w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje <xref:System.DivideByZeroException> wyjątek i ustawia rabat na zero.|

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania FlowchartWithFaultHandling. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Zobacz także

- [Przepływy pracy schematów blokowych](../flowchart-workflows.md)
- [Wyjątki](../exceptions.md)
