---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cc13696cfd8eb2dcdf22fdc067518c8bd55ca32d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004929"
---
# <a name="linq-message-query-correlation"></a>Korelacja zapytania komunikatów LINQ
W tym przykładzie pokazano, jak zrobić korelacja oparta na zawartości, przy użyciu niestandardowego <xref:System.ServiceModel.Dispatcher.MessageQuery> wdrożenia, a nie dostarczane przez system <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Demonstracje  
 Niestandardowe <xref:System.ServiceModel.Dispatcher.MessageQuery>, na podstawie zawartości korelacji.  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie pokazano, jak rozszerzyć <xref:System.ServiceModel.Dispatcher.MessageQuery> klasy bazowej na potrzeby korelacji. Implementacja niestandardowa `LinqMessageQuery`, umożliwia użytkownikom podanie XName można znaleźć w wiadomości przy użyciu XLinq. Dane pobrane przez zapytanie jest używany w celu utworzenia klucza korelacji wysyłać komunikaty do wystąpienia przepływu pracy odpowiednie.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Ten przykład przedstawia usługi przepływu pracy za pomocą punktów końcowych HTTP. Można dodać do uruchomienia tego przykładowego, odpowiednie listy ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) szczegóły), albo przez uruchomienie programu Visual Studio jako Administrator, wykonując następujące polecenie w wierszu podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, Twoja domena i nazwa użytkownika są zastępowane.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Ustawianie wielu projektów uruchamiania, kliknij prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**. Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów uruchamiania.  
  
    3. Uruchom aplikację. W konsoli klienta zawiera przepływu pracy, wysyłanie zamówienie i odbieranie identyfikator zamówienia zakupu oraz później potwierdzania zamówienia. Przedział czasu usługi pokaże przetwarzanych żądań.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
