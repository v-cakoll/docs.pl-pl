---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cd91a171f3242cfd7e8ac0404e24ac065919bcce
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094621"
---
# <a name="linq-message-query-correlation"></a>Korelacja zapytania komunikatów LINQ
Ten przykład pokazuje, jak przeprowadzić korelację opartą na zawartości przy użyciu niestandardowej implementacji <xref:System.ServiceModel.Dispatcher.MessageQuery>, w przeciwieństwie do <xref:System.ServiceModel.XPathMessageQuery>dostarczonych przez system.  
  
## <a name="demonstrates"></a>Przedstawia  
 <xref:System.ServiceModel.Dispatcher.MessageQuery>niestandardowe, korelacja oparta na zawartości.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak rozłożyć z klasy bazowej <xref:System.ServiceModel.Dispatcher.MessageQuery> na potrzeby korelacji. Implementacja niestandardowa, `LinqMessageQuery`, umożliwia użytkownikom podawanie XName do znajdowania w komunikacie przy użyciu XLinq. Dane pobierane przez zapytanie są używane do tworzenia klucza korelacji do wysyłania komunikatów do odpowiedniego wystąpienia przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Ten przykład uwidacznia usługę przepływu pracy za pomocą punktów końcowych HTTP. Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i https](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, że Twoja domena i nazwa użytkownika zostały zastąpione.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu list ACL adresów URL wykonaj następujące czynności.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Aby ustawić wiele projektów uruchomieniowych, kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Ustaw projekty startowe**. Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów początkowych.  
  
    3. Uruchom aplikację. W konsoli klienta programu jest wyświetlany przepływ pracy, który wysyła zamówienie i pobiera identyfikator zamówienia zakupu, a następnie potwierdza zamówienie. W oknie usługi zostaną wyświetlone żądania przetwarzane.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
