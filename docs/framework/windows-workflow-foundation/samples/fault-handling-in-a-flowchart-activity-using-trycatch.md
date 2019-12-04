---
title: Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710837"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch

Ten przykład pokazuje, jak aktywność <xref:System.Activities.Statements.TryCatch> może być używana w działaniu przepływu sterowania złożonego.

W tym przykładzie kod promocyjny i liczba elementów podrzędnych są przesyłane jako zmienne do działania <xref:System.Activities.Statements.Flowchart>, które oblicza rabat na podstawie formuły odpowiadającej kodowi promocji. Przykład obejmuje bezwzględny kod i wersje projektanta przepływu pracy dla przykładu.

W poniższej tabeli przedstawiono zmienne działania `CreateFlowchartWithFaults`.

|Parametry|Opis|
|----------------|-----------------|
|promoCode|Kod promocyjny. Typ: ciąg<br /><br /> Możliwe wartości z opisem w nawiasach:<br /><br /> -Pojedyncza (pojedyncza)<br />-MNK (ślub bez dzieci)<br />-MWK (ślub z dziecięcymi).|
|numKids|Liczba elementów podrzędnych. Typ: int|

Działanie `CreateFlowchartWithFaults` używa działania <xref:System.Activities.Statements.FlowSwitch%601>, które przełącza `promoCode` argument i oblicza rabat przy użyciu następującej formuły.

|Wartość `promoCode`|Rabat (%)|
|--------------------------|--------------------|
|Single|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Uwaga:** potencjalnie to obliczenie może zgłosić <xref:System.DivideByZeroException>. W związku z tym obliczanie rabatu jest opakowane w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje wyjątek <xref:System.DivideByZeroException> i ustawia rabat na zero.|

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania FlowchartWithFaultHandling. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Zobacz także

- [Przepływy pracy schematów blokowych](../flowchart-workflows.md)
- [Wyjątki](../exceptions.md)
