---
title: Obsługa błędów w schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: e89c80ecfa8ec93fdde82b5638c504ded681a4fc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487026"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Obsługa błędów w schematu blokowego przy użyciu działania TryCatch
W tym przykładzie pokazano sposób, w jaki <xref:System.Activities.Statements.TryCatch> działanie może być używane w ramach działania przepływu sterowania złożonego.  
  
 W tym przykładzie kodu promocyjnego, a liczba elementów podrzędnych są przekazywane jako zmienne <xref:System.Activities.Statements.Flowchart> działania, który oblicza rabat w wysokości oparte na formuł, które odpowiadają kodu promocyjnego. Przykład obejmuje imperatywne wersje projektanta kodu i przepływ pracy próbki.  
  
 W poniższej tabeli przedstawiono zmienne `CreateFlowchartWithFaults` działania.  
  
|Parametry|Opis|  
|----------------|-----------------|  
|promoCode|Kod promocyjny. Typ: ciąg<br /><br /> Możliwe wartości z opisem w nawiasach:<br /><br /> -Pojedynczy (pojedynczo)<br />-MNK (małżeństwa z nie dzieci).<br />-MWK (małżeństwa dla dzieci.)|  
|numKids|Liczba elementów podrzędnych. Typ: int|  
  
 `CreateFlowchartWithFaults` Używa działania <xref:System.Activities.Statements.FlowSwitch%601> działanie, które zmienia się na `promoCode` argumentu i oblicza rabat, korzystając z następującego wzoru.  
  
|Wartość `promoCode`|Rabat na wersję (%)|  
|--------------------------|--------------------|  
|Single|10|  
|MNK|15|  
|MWK|15 + (1 – 1 /`numberOfKids`)\*10 **Uwaga:** potencjalnie może zgłosić to obliczenie <xref:System.DivideByZeroException>. Dlatego obliczeń rabatu jest opakowana w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje <xref:System.DivideByZeroException> wyjątek i ustawia rabat na zero.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania FlowchartWithFaultHandling.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływy pracy schematów blokowych](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [Wyjątki](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
