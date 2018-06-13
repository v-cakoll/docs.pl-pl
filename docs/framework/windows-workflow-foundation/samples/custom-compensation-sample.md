---
title: Przykładowe kompensacji niestandardowych
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: 55161a46bebca2cce41803ca405cb2b1df57b3fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514327"
---
# <a name="custom-compensation-sample"></a>Przykładowe kompensacji niestandardowych
Ten przykład przedstawia sposób użycia <xref:System.Activities.Statements.CompensableActivity> i jego kompensacji, aby zdefiniować kompensacji niestandardowej logiki. Scenariusz uformowana w tym przykładzie jest agencji wynajem ciężarówka.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Kroki symulowane są:  
  
1.  Użytkownik żąda ciężarówki cudzysłowy dzierżawy dla określonej daty.  
  
2.  Kontaktuje się z trzech firm ciężarówka i trzy cudzysłowy są udostępniane.  
  
3.  Użytkownik wybiera jeden oferty ciężarówka i przechodzi do kolejności za pomocą karty kredytowej.  
  
4.  Aplikacja anuluje innych cudzysłowy ciężarówka dwa.  
  
5.  Aplikacja pobiera opłaty za usługę, z systemem innym niż zwrotowi dla inne niż premium konta w przypadku anulowania 10 dni lub mniej wcześniejsza od daty rezerwacji.  
  
6.  Aplikacja pobiera opłata wynajem ciężarówka.  
  
7.  Aplikacja oczekuje, aż Data rezerwacji lub do momentu klient postanowiła anulowania rezerwacji, zależnie od zostanie osiągnięty jako pierwszy.  
  
8.  Jeśli klient anuluje rezerwacji, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> kompensacji niestandardowej logiki działa zgodnie z następującą logiką:  
  
    1.  Jeśli klient ma inne niż premium konta i jest krótszy niż 10 dni przed datą rezerwacji, a następnie nadal są naliczane opłaty za usługę; w przeciwnym razie aplikacja zwrotów opłaty za usługę.  
  
    2.  Pozostałe działania compensable (kolejność ciężarówka + opłata kolejności ciężarówka) są uruchamiane zgodnie z logiką kompensacji domyślne, czyli odpowiednio w odwrotnej kolejności wykonywania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz rozwiązanie CustomCompensation.sln. Znajduje się w katalogu \WF\Basic\Compensation\CustomCompensation.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`