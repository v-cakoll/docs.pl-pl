---
title: Przykładowe Kompensacja niestandardowa
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475871"
---
# <a name="custom-compensation-sample"></a>Przykładowe Kompensacja niestandardowa
Ten przykład ilustruje sposób używania <xref:System.Activities.Statements.CompensableActivity> i jego procedurę obsługi do definiowania logiki Kompensacja niestandardowa. Scenariusz, w tym przykładzie w modelu jest agencji wypożyczeń Truck.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Procedura symulowane jest następująca:  
  
1.  Użytkownik żąda ciężarówki oferty dzierżawy dla określonej daty.  
  
2.  Kontaktować się z trzech firm truck i znajdują się trzy cudzysłowów.  
  
3.  Użytkownik wybiera jeden truck oferty i przechodzi do kolejności przy użyciu karty kredytowej.  
  
4.  Aplikacja anuluje inne oferty truck dwa.  
  
5.  Aplikacja pobiera opłaty za usługę, czyli niepodlegającego zwrotowi środków dla kont innych niż premium w przypadku anulowania się stanie w ciągu 10 dni lub mniej przed datą rezerwacji.  
  
6.  Aplikacja opłaty za opłatą wypożyczeń truck.  
  
7.  Aplikacja czeka, aż Data rezerwacji lub do momentu klient zdecydowała się anulowania rezerwacji, osiągnięta jako pierwsza.  
  
8.  Jeśli klient anuluje rezerwację, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Kompensacja niestandardowa logiki jest uruchamiany zgodnie z następującą logiką:  
  
    1.  Jeśli klient ma konto inne niż premium i jest mniej niż 10 dni przed datą rezerwacji, a następnie nadal są naliczane opłaty za usługę; w przeciwnym razie aplikacja zwroty opłata za usługę.  
  
    2.  Pozostałe kompensacyjne działań (kolejność truck + opłata kolejności truck) są uruchamiane zgodnie z domyślnej logiki wynagrodzenie, która jest wyrównanie w odwrotnej kolejności wykonywania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz rozwiązanie CustomCompensation.sln. Znajduje się on w katalogu \WF\Basic\Compensation\CustomCompensation.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`