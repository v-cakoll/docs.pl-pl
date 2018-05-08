---
title: 'Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: d26e3b127328a3de4df6bd58fb6015bee045f3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+
Po wybraniu odpowiednich trybu hostingu umożliwia skonfigurowanie interfejsów aplikacji, które mają być widoczne jako usługi sieci Web narzędzie wiersza polecenia konfiguracji modelu usług COM + (ComSvcConfig.exe).  
  
> [!NOTE]
>  Musi być administratorowi wykonaj jedną z następujących zadań na komputerze.  
  
 Za pomocą ComSvcConfig.exe na komputerze z systemem Windows 7 Konfiguruj usługę sieci web, aby używać najnowszej wersji modelu usług (obecnie 4.5), wykonaj następujące czynności:  
  
1.  Ustaw klucz rejestru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na wartość DWORD 0x00000001  
  
2.  Uruchom comsvcconfig.exe  
  
3.  Przywróć klucz rejestru dodanej w kroku 1 do oryginalnej wartości lub usuń go, jeśli nie istnieje.  
  
> [!IMPORTANT]
>  Ważne jest przywrócenie tego klucza rejestru. Jest to klucz zgodności. Przywracanie nie ta zmiana może spowodować problemy z innych aplikacji .NET uruchomionych na komputerze).  
  
> [!WARNING]
>  Podczas używania ComSvcConfig.exe/install na komputerze z systemem Windows 8 okno dialogowe jest wyświetlane, podając "aplikacji na komputerze wymaga następujących funkcji systemu Windows: .NET Framework 3.5 (obejmuje .NET 2.0 i .NET 3.0" Jeśli nie jest zainstalowany program .NET Framework 3.5. Można zignorować to okno dialogowe. Alternatywnie możesz mniejszyć OnlyUseLatestCLR klucza rejestru na wartość DWORD 0x00000001  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +  
  
-   Uruchom przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje `IFinances` interfejsu `ItemOrders.IFinancial` składnik (z OnlineStore aplikacji COM +), aby zestaw interfejsów, które mają być widoczne jako usługi sieci Web. Usługa korzysta z trybu obsługi modelu COM + i dlatego wymaga aktywację jawnym aplikacji.  
  
     Gdy znaku wieloznacznego gwiazdki (*) może służyć do działania składnika i interfejsie, unikać używania go, ponieważ można udostępniać tylko wybrane funkcje jako usługę sieci Web. Jeśli są uruchomione przy przyszłych wersjach tego składnika, przy użyciu symbolu wieloznacznego przypadkowo może narazić interfejsów, które mogły nie być wyświetlany, jeśli określono składni konfiguracji.  
  
     / Verbose — opcja powoduje, że narzędzie do wyświetlania ostrzeżeń oprócz wszelkie błędy.  
  
     Kontrakt usługi narażonych będzie zawierać wszystkie metody z `IFinances` interfejsu.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać tylko konkretnych metod z interfejsem do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +  
  
-   Uruchom przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje za pomocą nazw jawnych metod wymaganych, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje tylko `Credit` i `Debit` metody `IFinances` interfejsu jako operacje narażonych serwisowej. Wszystkie inne metody w interfejsie zostanie pominięta kontrakt i nie będzie można wywołać z klientami usługi sieci Web.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu sieci Web  
  
-   Uruchom przy użyciu ComSvcConfig `/install` opcji i `/hosting:was` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Polecenie dodaje `IStockLevels` interfejs w `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które mają być widoczne jako usługi sieci Web. Usługa jest hostowana w OnlineWarehouse katalog wirtualny usług IIS, a nie w modelu COM + w sieci Web i w związku z tym aplikacja jest aktywowana automatycznie zgodnie z wymaganiami.  
  
     Do korzystania z sieci Web hostowanych w procesie konfiguracji, aplikacja COM + musi być skonfigurowana do uruchamiania jako aplikacja biblioteki, a nie aplikacji serwera za pomocą konsoli administracyjnej usług składowych. Aplikacje skonfigurowane jako aplikacji serwerowych Tryb standardowy hostowanych w sieci Web i pociągnąć za sobą przeskoku procesu przetwarzania każdego żądania.  
  
     `/mex` Opcja dodaje dodatkowe punktu końcowego usługi wymiany metadanych (MEX), który używa tego samego transportu jako punkt końcowy usługi aplikacji do obsługi klientów, które ma zostać pobrane definicję kontraktu usługi.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Aby usunąć usługi sieci Web dla określonego interfejsu  
  
-   Uruchom przy użyciu ComSvcConfig `/uninstall` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Usuwa polecenie `IFinances` interfejs w `ItemOrders.Financial` części (z OnlineStore aplikacji COM +).  
  
### <a name="to-list-currently-exposed-interfaces"></a>Aby wyświetlić listę aktualnie interfejsów  
  
-   Uruchom przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Polecenie wyświetla listę aktualnie interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, zakres na komputerze lokalnym.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Aby wyświetlić listę aktualnie określonego widoczne interfejsów  
  
-   Uruchom przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     List poleceń aktualnie widoczne COM +-hostowanej interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, na podstawie OnlineStore COM + na komputerze lokalnym.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Aby wyświetlić Pomoc na temat opcji, które mogą służyć za pomocą narzędzia  
  
-   Uruchom przy użyciu ComSvcConfig /? opcja, jak pokazano w poniższym przykładzie.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd integrowania z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
