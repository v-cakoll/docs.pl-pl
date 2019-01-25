---
title: Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 7c536c9420e94e9b8f8bc2656df284d95a9744c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568195"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
Narzędzie wiersza polecenia w konfiguracji modelu usług COM + (ComSvcConfig.exe) umożliwia skonfigurowanie interfejsów modelu COM + być udostępniane jako usługi sieci Web.  
  
## <a name="syntax"></a>Składnia  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Musisz być administratorem na komputerze lokalnym do użycia ComSvcConfig.exe.  
  
 Narzędzie można znaleźć w następującej lokalizacji  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Aby uzyskać więcej informacji na temat ComSvcConfig.exe zobacz [jak: Używanie narzędzia konfiguracji modelu usług COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 W poniższej tabeli opisano tryby, które mogą być używane z ComSvcConfig.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`install`|Instaluje konfiguracji interfejsu COM + Service Model integration.<br /><br /> Skrócona forma `/i`.|  
|`uninstall`|Odinstalowuje konfigurację interfejsu COM + z modelu usług integracji.<br /><br /> Skrócona forma `/u`.|  
|`list`|Wyświetla informacje na temat składników mających interfejsy, które są skonfigurowane do integracji modelu usług i aplikacji COM +.<br /><br /> Skrócona forma `/l`.|  
  
 W poniższej tabeli opisano flagi, które mogą być używane z ComSvcConfig.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName*\>|Określa aplikacji COM +, aby skonfigurować.<br /><br /> Skrócona forma `/a`.|  
|`/contract:` \<*Identyfikator klasy* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName*    &#124; \*\>|Określa składnik COM + i interfejs, który zostanie skonfigurowany jako kontraktu usługi.<br /><br /> Skrócona forma `/c`.<br /><br /> Podczas gdy znak symbolu wieloznacznego (\*) mogą być używane podczas określenia nazwy składnika i interfejs zaleca się nie korzystać, ponieważ może uwidaczniać interfejsy, które nie ma do.|  
|`/hosting:` \<*complus*  &#124; *was*\>|Określa, czy używać modelu COM + hosting trybu lub trybie hostingu w sieci Web.<br /><br /> Skrócona forma `/h`.<br /><br /> Za pomocą modelu COM + hosting trybu wymaga jawnego aktywacji aplikacji COM +. Korzystanie z sieci Web w trybie hostingu umożliwia aplikacji COM + automatycznie aktywowane jako wymagane. Jeśli aplikacja COM + jest aplikacja biblioteki, działa w procesie Internet Information Services (IIS). Aplikacja modelu COM + w przypadku aplikacji serwera, jest uruchamiany w procesie Dllhost.exe.|  
|`/webSite:` \<*WebsiteName*\>|Określa witryny sieci Web do hostowania, gdy tryb hostingu w sieci Web jest używana (zobacz `/hosting` flagi).<br /><br /> Skrócona forma `/w`.<br /><br /> Jeśli ma witryny sieci Web jest określony, domyślna witryna sieci Web jest używana.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Określa katalog wirtualny dla hostingu stosowania hosting sieci Web (zobacz `/hosting` flagi).<br /><br /> Skrócona forma `/d`.|  
|`/mex`|W domyślnej konfiguracji Usługa do obsługi klientów, które mają zostać pobrane definicję kontraktu usługi, dodaje punkt końcowy usługi wymiany metadanych (MEX).<br /><br /> Skrócona forma `/x`.|  
|`/id`|Wyświetla aplikacji, składników i informacje o interfejsie jako identyfikatorów.<br /><br /> Skrócona forma `/k`.|  
|`/nologo`|ComSvcConfig.exe uniemożliwia wyświetlanie logo jej.<br /><br /> Skrócona forma `/n`.|  
|`/verbose`|Wyświetla wszystkie ostrzeżenia i tekst informacyjny, oprócz wszystkich wykrytych błędów.<br /><br /> Skrócona forma `/v`.|  
|`/help`|Wyświetla komunikat o sposobie użycia.<br /><br /> Skrócona forma `/?`.|  
|`/partial`|Generuje konfiguracji usługi, gdy określony interfejs zawiera podpisy metod, które mogą być udostępniane. Podczas inicjowania usługi zgodne metody są wyświetlane jako operacje na kontrakt usługi i metod niezgodnych są ignorowane i znajduje się poza kontraktu usługi.<br /><br /> Jeśli brakuje tej flagi, narzędzie nie wygeneruje konfiguracji usługi, gdy określony interfejs zawiera jedną lub więcej metod niezgodnych.|  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie dodano `IFinances` interfejsu `ItemOrders.IFinancial` składnika (z OnlineStore aplikacji COM +) do zestawu interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu macierzystego modelu COM +. Wszystkie ostrzeżenia będą dane wyjściowe, oprócz wszystkich wykrytych błędów.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie dodano `IStockLevels` interfejsu `ItemInventory.Warehouse` składnika (z OnlineWarehouse aplikacji COM +) do zestawu interfejsów, które są dostępne jako usługi sieci Web w trybie hostingu w sieci Web. Usługa sieci Web jest sieci Web hostowanych w katalogu wirtualnym OnlineWarehouse usług IIS.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Opis  
 Poniższy przykład usuwa `IFinances` interfejsu `ItemOrders.Financial` składnika (z OnlineStore aplikacji COM +) z zestawu interfejsów, które są dostępne jako usługi sieci Web.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Opis  
 Na poniższych listach przykład aktualnie widoczne interfejsów modelu COM + hostowane, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, dla aplikacji OnlineStore COM +, na komputerze lokalnym.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Używanie narzędzia konfiguracji modelu usług COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
