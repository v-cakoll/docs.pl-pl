---
title: 'Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 528e46a47daa6df865308592eb41658369a74b6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736250"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+
Po wybraniu odpowiedni tryb hostingu skonfiguruj interfejsy aplikacji, które będą dostępne jako usługi sieci Web za pomocą narzędzia wiersza polecenia w konfiguracji modelu usług COM + (ComSvcConfig.exe).  
  
> [!NOTE]
>  Musi być administratorem na komputerze, aby wykonać dowolne z następujących czynności.  
  
 Korzystając z ComSvcConfig.exe na komputerze z Windows 7 można skonfigurować usługę sieci web, aby korzystać z najnowszej wersji modelu usługi (obecnie 4.5), wykonaj następujące czynności:  
  
1.  Ustaw klucz rejestru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` wartość DWORD 0x00000001  
  
2.  Uruchom comsvcconfig.exe  
  
3.  Przywróć klucz rejestru, dodanej w kroku 1 do oryginalnej wartości lub usuń go, jeśli nie istnieje.  
  
> [!IMPORTANT]
>  Ważne jest przywrócenie tego klucza rejestru. Jest to klucz zgodności. Przywracanie nie ta zmiana może spowodować problemy z innymi aplikacjami .NET na maszynie).  
  
> [!WARNING]
>  Korzystając z ComSvcConfig.exe/install na komputerze Windows 8 okno dialogowe jest wyświetlony "aplikacji na komputerze wymaga następującej funkcji Windows: .NET Framework 3.5 (obejmuje .NET 2.0 i .NET 3.0" Jeśli nie zainstalowano programu .NET Framework 3.5. Można zignorować to okno dialogowe. Alternatywnie możesz sed OnlyUseLatestCLR klucza rejestru w celu wartość DWORD 0x00000001  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu obsługi modelu COM +  
  
-   Uruchamianie przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje `IFinances` interfejsu `ItemOrders.IFinancial` składnika (z OnlineStore aplikacji COM +) do zestawu interfejsów, które będą dostępne jako usługi sieci Web. Usługa korzysta z modelu COM + hosting tryb i w związku z tym wymaga składnika Aktywacja jawne aplikacji.  
  
     Chociaż wieloznacznego gwiazdki (*) mogą być używane dla składnika i interfejsu, Unikaj korzystania z niego, ponieważ może uwidaczniać tylko wybrane funkcjonalność w postaci usługi sieci Web. Uruchom z przyszłych wersji tego składnika, z zastosowaniem symbolu wieloznacznego przypadkowo może narazić interfejsów, które nie mogły być obecna, gdy określono składni konfiguracji.  
  
     / Verbose — opcja powoduje, że narzędzie, aby wyświetlić ostrzeżenia, oprócz wszelkie błędy.  
  
     Kontrakt usługi narażonych będzie zawierać wszystkie metody z `IFinances` interfejsu.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać tylko konkretnych metod z interfejsu do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu obsługi modelu COM +  
  
-   Uruchamianie przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje nazewnictwa jawnych metod wymaganych, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje tylko `Credit` i `Debit` metody z `IFinances` interfejs jako operacji kontraktu usługi narażone. Wszystkie inne metody w interfejsie zostanie pominięta kontrakt i nie będzie można wywołać za pomocą klientów usługi sieci Web.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu hostingu w sieci Web  
  
-   Uruchamianie przy użyciu ComSvcConfig `/install` opcji i `/hosting:was` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Polecenie dodaje `IStockLevels` interfejsu na `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które będą dostępne jako usługi sieci Web. Usługa jest hostowana w katalogu wirtualnym OnlineWarehouse usług IIS, a nie w modelu COM + w sieci Web i dlatego automatycznie aktywowano aplikację zgodnie z wymaganiami.  
  
     Do korzystania z konfiguracji w trakcie hostowanych w sieci Web, aplikacji COM +, musi być skonfigurowany do uruchamiania jako aplikacji biblioteki, a nie aplikacji serwera przy użyciu konsoli administracyjnej usługi składowe. Aplikacje, skonfigurowany jako serwer aplikacji używanie standardowego trybu hostowanej w sieci Web bez ponoszenia przeskoku procesu przetwarzania każdego żądania.  
  
     `/mex` Opcja dodaje dodatkowe metadane programu Exchange (MEX) usługi punktu końcowego, który używa tego samego transportu jako punkt końcowy usługi aplikacji do obsługi klientów, które mają zostać pobrane definicję kontraktu usługi.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Aby usunąć usługę sieci Web dla określonego interfejsu  
  
-   Uruchamianie przy użyciu ComSvcConfig `/uninstall` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Polecenie usuwa `IFinances` interfejsu na `ItemOrders.Financial` składnika (z OnlineStore aplikacji COM +).  
  
### <a name="to-list-currently-exposed-interfaces"></a>Aby wyświetlić listę aktualnie interfejsów  
  
-   Uruchamianie przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Polecenie wyświetla listę aktualnie interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, ograniczone do komputera lokalnego.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Aby wyświetlić listę określonych aktualnie widoczne interfejsów  
  
-   Uruchamianie przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Listy poleceń aktualnie widoczne COM + — obsługiwane interfejsy, wraz z odpowiednim adresem i szczegóły powiązania aplikacji OnlineStore COM +, na komputerze lokalnym.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Aby wyświetlić Pomoc na temat opcji, które mogą służyć za pomocą narzędzia  
  
-   Uruchamianie przy użyciu ComSvcConfig /? opcja, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd integrowania z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
