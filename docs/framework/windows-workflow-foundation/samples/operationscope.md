---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d1e2738e8cdb546a1dcbb00689e5b4c360ddd04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operationscope"></a>OperationScope
W przykładzie pokazano sposób działania, do obsługi komunikatów <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> można użyć do udostępnienia istniejących działań niestandardowych jako operacji w usłudze przepływu pracy. Ten przykład zawiera nowe niestandardowe działanie o nazwie `OperationScope`. Jest on przeznaczony do jej obsługi ułatwiają tworzenie usługi przepływu pracy zezwolenie użytkownikom na tworzenie treści prace oddzielnie jako działań niestandardowych, a następnie łatwe udostępnianie je jako operacje usługi przy użyciu `OperationScope` działania. Na przykład niestandardowy `Add` działania, która przyjmuje dwa `in` argumentów i zwraca jedną `out` argument może być udostępniany jako `Add` operacji w usłudze przepływu pracy, przeciągając go do `OperationScope`.  
  
 Zakres działa sprawdzając działania w jego treści. Wszelkie niepowiązane `in` argumenty są uważane za dane wejściowe z komunikatu przychodzącego. Wszystkie `out` argumentów, niezależnie od tego, czy są powiązane są uważane za dane wyjściowe w kolejnych odpowiedzi. Nazwa operacji narażonych jest pobierana z nazwę wyświetlaną `OperationScope` działania. W rezultacie jest, że działanie treści jest ujęte w <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> z parametrami z wiadomości powiązany z argumentów działania.  
  
 Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP. Do uruchomienia, muszą zostać dodane odpowiednie listy ACL adresu URL. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień dodaje odpowiednich list ACL (Upewnij się, że Twoje domena i nazwa użytkownika są zastępowane dla domeny %\\% UserName %).  
  
 **netsh http Dodaj adres url urlacl = http: / / +: 8000 / użytkownika domeny % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie OperationScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierając **Ustaw projekty startowe**. Dodawanie scenariuszy i Scenario_Client (w tej kolejności) jako wiele projektów rozruchu.  
  
3.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
    > [!WARNING]
    >  Ten krok jest wymagany do wyświetlania BankService.xaml przepływu pracy z powodu działań niestandardowych `OperationScope`.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację. Konsoli Scenario_Client wyświetla monit o podanie danych wejściowych i odpowiednie dane wyjściowe jest widoczne w konsoli scenariusza.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`  
  
## <a name="see-also"></a>Zobacz też
