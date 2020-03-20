---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182807"
---
# <a name="linq-message-query-correlation"></a>Korelacja zapytania komunikatów LINQ
W tym przykładzie pokazano, jak wykonać korelację <xref:System.ServiceModel.Dispatcher.MessageQuery> opartą na zawartości przy <xref:System.ServiceModel.XPathMessageQuery>użyciu implementacji niestandardowej, w przeciwieństwie do dostarczonych przez system.  
  
## <a name="demonstrates"></a>Demonstracje  
 Niestandardowa <xref:System.ServiceModel.Dispatcher.MessageQuery>korelacja oparta na zawartości.  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie pokazano, jak rozszerzyć z klasy podstawowej <xref:System.ServiceModel.Dispatcher.MessageQuery> na potrzeby korelacji. Implementacja niestandardowa, `LinqMessageQuery`umożliwia użytkownikom zapewnienie XName znaleźć w wiadomości przy użyciu XLinq. Dane pobrane przez kwerendę jest używany do tworzenia klucza korelacji do wysyłania komunikatów do wystąpienia przepływu pracy odpowiednie.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. W tym przykładzie udostępnia usługę przepływu pracy przy użyciu punktów końcowych HTTP. Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i HTTPS](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, że twoja domena i nazwa użytkownika są podstawione.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu list ACL url należy wykonać następujące czynności.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Ustaw wiele projektów start-upów, klikając prawym przyciskiem myszy rozwiązanie i wybierając **pozycję Ustaw projekty startowe**. Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów startowych.  
  
    3. Uruchom aplikację. Konsola klienta pokazuje przepływ pracy wysyłający zamówienie i odbierający identyfikator zamówienia zakupu, a następnie potwierdzający zamówienie. Okno Usługa wyświetli przetwarzane żądania.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
