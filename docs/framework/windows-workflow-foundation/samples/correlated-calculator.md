---
title: Kalkulator skorelowane
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6296ecb5c708d344624cac6e24247d2163fd66b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="correlated-calculator"></a>Kalkulator skorelowane
W tym przykładzie przedstawiono sposób użycia działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>) w Projektancie z korelacją na podstawie zawartości na podstawie parametru w komunikacie. W tym scenariuszu operacje Kalkulator znajdują się w który równoległych. Zarówno wystąpienia, jak i korelacja (na podstawie `CalculatorId`) są tworzone, gdy pierwszy komunikat jest wysyłany do przepływu pracy i kolejnych komunikatów o takim samym `CalculatorId` są wysyłane do tego wystąpienia, dopóki nosi nazwę operację resetowania. Klient jest implementowany jako aplikacji WPF, która używa serwera proxy klienta oparte na kodzie do komunikowania się z usługą.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] w podwyższonym poziomem uprawnień, otwórz plik rozwiązania For.sln.  
  
    1.  Przejdź do folderu, który zawiera [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Kliknij prawym przyciskiem myszy Devenv.exe i wybierz **Uruchom jako administrator**.  
  
2.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CorrelatedCalculator.sln.  
  
3.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
4.  Aby uruchomić projekt usługi, naciśnij kombinację klawiszy CTRL + F5.  
  
5.  Gdy usługa jest gotowa i nasłuchiwania dla wiadomości w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta i uruchom go.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`