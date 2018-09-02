---
title: Skorelowany Kalkulator
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384674"
---
# <a name="correlated-calculator"></a>Skorelowany Kalkulator
W tym przykładzie przedstawiono sposób użycia działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>) w Projektancie z korelacją opartego na zawartości, na podstawie parametru w komunikacie. W tym scenariuszu operacje Kalkulator znajdują się w konwoju równoległych. Zarówno w przypadku wystąpienia, jak i korelacja (na podstawie `CalculatorId`) są tworzone, gdy pierwszy komunikat jest wysyłany do przepływu pracy, a kolejne komunikaty z taką samą `CalculatorId` są wysyłane do tego wystąpienia, dopóki nie jest wywoływana przez operację resetowania. Klient jest implementowany jako aplikację WPF, która używa serwer proxy oparty na kodzie klienta do komunikowania się z usługą.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Rozpocznij [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] w podwyższonym poziomem uprawnień, otwórz plik rozwiązania For.sln.  
  
    1.  Przejdź do folderu, który zawiera [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Kliknij prawym przyciskiem myszy Devenv.exe, a następnie wybierz pozycję **Uruchom jako administrator**.  
  
2.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CorrelatedCalculator.sln.  
  
3.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
4.  Aby uruchomić projekt usługi, naciśnij kombinację klawiszy CTRL + F5.  
  
5.  Gdy usługa jest gotowy i nasłuchuje komunikatów w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta, a następnie uruchom go.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`