---
title: 'Instrukcje: używanie narzędzia konfiguracji modelu usług COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 67bacade0435f1c63bc79b3282f6bded55b67304
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991584"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Instrukcje: używanie narzędzia konfiguracji modelu usług COM+
Po wybraniu odpowiedniego trybu hostingu Użyj narzędzia wiersza polecenia konfiguracji modelu usług COM+ (ComSvcConfig. exe), aby skonfigurować interfejsy aplikacji, które będą udostępniane jako usługi sieci Web.  
  
> [!NOTE]
> Aby wykonać dowolne z następujących zadań, musisz być administratorem na komputerze.  
  
 W przypadku korzystania z programu ComSvcConfig. exe na komputerze z systemem Windows 7 w celu skonfigurowania usługi sieci Web do korzystania z najnowszej wersji modelu usług (obecnie 4.5) wykonaj następujące czynności:  
  
1. Ustaw klucz `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` rejestru na wartość typu DWORD 0x00000001  
  
2. Uruchom ComSvcConfig. exe  
  
3. Przywróć pierwotną wartość klucza rejestru, który został dodany w kroku 1, lub usuń go, jeśli nie istnieje.  
  
> [!IMPORTANT]
> Przywrócenie tego klucza rejestru jest ważne. Jest to klucz zgodności. Przywrócenie tej zmiany może spowodować problemy z innymi aplikacjami .NET uruchomionymi na komputerze.  
  
> [!WARNING]
> W przypadku korzystania z ComSvcConfig. exe/install na komputerze z systemem Windows 8 zostanie wyświetlone okno dialogowe informujące o tym, że aplikacja na komputerze wymaga następującej funkcji systemu Windows: .NET Framework 3,5 (w tym .NET 2,0 i .NET 3,0 "Jeśli .NET Framework 3,5 nie jest zainstalowana. To okno dialogowe może być ignorowane. Alternatywnie można przyOnlyUseLatestCLR klucz rejestru do wartości DWORD 0x00000001  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów udostępnianych jako usługi sieci Web, przy użyciu trybu hostingu modelu COM+  
  
- Uruchom ComSvcConfig przy użyciu `/install` opcji `/hosting:complus` i, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje `IFinances` Interfejs `ItemOrders.IFinancial` składnika (z aplikacji OnlineStore com+) do zestawu interfejsów, które będą uwidocznione jako usługi sieci Web. Usługa używa trybu hostingu modelu COM+ i w związku z tym wymaga jawnej aktywacji aplikacji.  
  
     Chociaż symbol wieloznaczny\*gwiazdka () może być używany dla składnika i interfejsu, należy unikać używania go, ponieważ może być konieczne uwidocznienie tylko wybranych funkcji jako usługi sieci Web. Jeśli jest uruchamiany z przyszłą wersją tego składnika, użycie symbolu wieloznacznego może przypadkowo ujawnić interfejsy, które mogą nie być obecne podczas określania składni konfiguracji.  
  
     Opcja/verbose nakazuje narzędziu wyświetlanie ostrzeżeń oprócz błędów.  
  
     Kontrakt dla uwidocznionej usługi będzie zawierać wszystkie metody z `IFinances` interfejsu.  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Aby dodać tylko konkretne metody z interfejsu do zestawu interfejsów uwidocznionych jako usługi sieci Web, przy użyciu trybu hostingu modelu COM+  
  
- Uruchom ComSvcConfig przy użyciu `/install` opcji `/hosting:complus` i z jawnym nazewnictwem wymaganych metod, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Polecenie dodaje tylko `Credit` metody i `Debit` z `IFinances` interfejsu jako operacje do umowy uwidocznionej usługi. Wszystkie inne metody interfejsu zostaną pominięte z kontraktu i nie zostaną wywołane przez klientów usługi sieci Web.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a>Aby dodać interfejs do zestawu interfejsów udostępnianych jako usługi sieci Web, korzystając z trybu hostingu w sieci Web  
  
- Uruchom ComSvcConfig przy użyciu `/install` opcji `/hosting:was` i opcji, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Polecenie dodaje `IStockLevels` Interfejs `ItemInventory.Warehouse` do składnika (z aplikacji OnlineWarehouse com+) do zestawu interfejsów, które będą udostępniane jako usługi sieci Web. Usługa jest w sieci Web hostowana w katalogu wirtualnym usługi IIS OnlineWarehouse, a nie w modelu COM+, a więc aplikacja jest automatycznie uaktywniana zgodnie z potrzebami.  
  
     Aby można było korzystać z konfiguracji w procesie hostowanym w sieci Web, aplikacja COM+ musi być skonfigurowana do uruchamiania jako aplikacja biblioteki, a nie aplikacja serwera przy użyciu konsoli administracyjnej usług składowych. Aplikacje skonfigurowane jako aplikacje serwera używają standardowego trybu hostowanego w sieci Web i ponoszą przeskok procesu, aby przetwarzać każde żądanie.  
  
     `/mex` Opcja dodaje dodatkowy punkt końcowy usługi wymiany metadanych (Mex), który używa tego samego transportu co punkt końcowy usługi aplikacji do obsługi klientów, którzy chcą pobrać definicję kontraktu z usługi.  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a>Aby usunąć usługę sieci Web dla określonego interfejsu  
  
- Uruchom ComSvcConfig przy użyciu `/uninstall` opcji, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Polecenie usuwa `IFinances` Interfejs `ItemOrders.Financial` na składniku programu (z aplikacji OnlineStore com+).  
  
## <a name="to-list-currently-exposed-interfaces"></a>Aby wyświetlić listę aktualnie uwidocznionych interfejsów  
  
- Uruchom ComSvcConfig przy użyciu `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     Polecenie wyświetla listę aktualnie uwidocznionych interfejsów wraz z odpowiednim adresem i szczegółami powiązania, które należą do zakresu komputera lokalnego.  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a>Aby wyświetlić listę konkretnych interfejsów, które są obecnie uwidocznione  
  
- Uruchom ComSvcConfig przy użyciu `/list` opcji, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Polecenie wyświetla aktualnie uwidocznione interfejsy obsługiwane przez model COM+ oraz odpowiednie adresy i szczegóły dotyczące powiązań dla aplikacji OnlineStore COM+ na komputerze lokalnym.  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Aby wyświetlić pomoc dotyczącą opcji, które mogą być używane z narzędziem  
  
- Uruchom ComSvcConfig przy użyciu/? opcja, jak pokazano w poniższym przykładzie.  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd integrowania z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
