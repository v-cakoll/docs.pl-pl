---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177117"
---
# <a name="operationscope"></a>OperationScope
W tym przykładzie przedstawiono sposób, w jaki wiadomości działania, <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> może służyć do udostępnienia istniejących niestandardowe działanie jako operacji w usłudze przepływu pracy. W tym przykładzie zawiera nowe niestandardowe działanie o nazwie `OperationScope`. Jest ona przeznaczona do jej obsługi ułatwiają realizację Tworzenie usługi przepływu pracy, pozwalając użytkownikom na tworzenie treści swojej działalności oddzielnie jako działania niestandardowe, a następnie łatwe udostępnianie ich jako operacje usługi przy użyciu `OperationScope` działania. Na przykład niestandardowy `Add` działań, która przyjmuje dwa `in` argumenty i zwraca jedną `out` argument może być udostępniany jako `Add` działanie usługi przepływu pracy przeciągając go do `OperationScope`.  
  
 Zakres działa, sprawdzając działania w jej treści. Dowolny niepowiązanych `in` argumenty są zakłada się, że dane wejściowe z przychodzących wiadomości. Wszystkie `out` argumentów, niezależnie od tego, czy są one związane, to zakłada się, że dane wyjściowe w kolejnych odpowiedzi. Nazwa operacji narażonych pochodzi z nazwy wyświetlanej `OperationScope` działania. Efekt jest, że działanie treści jest opakowana w <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> z parametrami, od wiadomości powiązany z argumentami działania.  
  
 Ten przykład przedstawia usługi przepływu pracy za pomocą punktów końcowych HTTP. Aby uruchomić, należy dodać odpowiednie listy ACL adresu URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień Wykonywanie dodaje odpowiednie listy ACL (Upewnij się, że Twoja domena i nazwa użytkownika są zastępowane dla domeny %\\% UserName %).  
  
 **netsh http Dodaj adres url urlacl =http://+:8000/ użytkownika domeny % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie OperationScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Ustawianie wielu projektów uruchamiania, kliknij prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierając **Ustaw projekty startowe**. Dodaj scenariusz i Scenario_Client (w tej kolejności) jako wiele projektów uruchamiania.  
  
3.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
    > [!WARNING]
    >  Ten krok jest wymagany, aby wyświetlić przepływ pracy BankService.xaml ze względu na to niestandardowe działanie `OperationScope`.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację. Konsola Scenario_Client wyświetli monit o podanie danych wejściowych i odpowiednie dane wyjściowe są widoczne w konsoli scenariusza.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`