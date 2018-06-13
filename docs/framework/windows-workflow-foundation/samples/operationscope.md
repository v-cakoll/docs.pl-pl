---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: bca5a32e25537aea8c8fad7b80eb296d66fadf77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515788"
---
# <a name="operationscope"></a>OperationScope
W przykładzie pokazano sposób działania, do obsługi komunikatów <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> można użyć do udostępnienia istniejących działań niestandardowych jako operacji w usłudze przepływu pracy. Ten przykład zawiera nowe niestandardowe działanie o nazwie `OperationScope`. Jest on przeznaczony do jej obsługi ułatwiają tworzenie usługi przepływu pracy zezwolenie użytkownikom na tworzenie treści prace oddzielnie jako działań niestandardowych, a następnie łatwe udostępnianie je jako operacje usługi przy użyciu `OperationScope` działania. Na przykład niestandardowy `Add` działania, która przyjmuje dwa `in` argumentów i zwraca jedną `out` argument może być udostępniany jako `Add` operacji w usłudze przepływu pracy, przeciągając go do `OperationScope`.  
  
 Zakres działa sprawdzając działania w jego treści. Wszelkie niepowiązane `in` argumenty są uważane za dane wejściowe z komunikatu przychodzącego. Wszystkie `out` argumentów, niezależnie od tego, czy są powiązane są uważane za dane wyjściowe w kolejnych odpowiedzi. Nazwa operacji narażonych jest pobierana z nazwę wyświetlaną `OperationScope` działania. W rezultacie jest, że działanie treści jest ujęte w <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> z parametrami z wiadomości powiązany z argumentów działania.  
  
 Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP. Do uruchomienia, muszą zostać dodane odpowiednie listy ACL adresu URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień dodaje odpowiednich list ACL (Upewnij się, że Twoje domena i nazwa użytkownika są zastępowane dla domeny %\\% UserName %).  
  
 **netsh http Dodaj adres url urlacl =http://+:8000/ użytkownika domeny % =\\% UserName %**  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`