---
title: "Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40e7644ade32f245772a8971cf0693683b980952
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
Narzędzie wiersza polecenia konfiguracji modelu usług COM + (ComSvcConfig.exe) umożliwia skonfigurowanie interfejsów modelu COM + mają być uwidaczniane jako usługi sieci Web.  
  
## <a name="syntax"></a>Składnia  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Musi być administratorem na komputerze lokalnym do użycia ComSvcConfig.exe.  
  
 Narzędzie można znaleźć w następującej lokalizacji  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ komunikacji  
  
 Aby uzyskać więcej informacji o ComSvcConfig.exe, zobacz [porady: Użyj modelu COM + narzędzia konfiguracji modelu usług](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 W poniższej tabeli opisano tryby, które mogą być używane z ComSvcConfig.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`install`|Instaluje konfiguracji interfejsu COM + integracji modelu usług.<br /><br /> Skrócona forma `/i`.|  
|`uninstall`|Odinstalowuje konfiguracji dla interfejsu COM + z integracji modelu usług.<br /><br /> Skrócona forma `/u`.|  
|`list`|Wyświetla informacje o aplikacji COM + i składników, które interfejsy, które są skonfigurowane dla integracji modelu usług.<br /><br /> Skrócona forma `/l`.|  
  
 W poniższej tabeli opisano flagi, które mogą być używane z ComSvcConfig.exe.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/application:`\< *ApplicationID* &#124; *ApplicationName*\>|Określa konfigurowania aplikacji COM +.<br /><br /> Skrócona forma `/a`.|  
|`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*Identyfikator interfejsu* &#124; *InterfaceName* &#124;\*\>|Określa interfejs, który zostanie skonfigurowany jako kontraktu usługi i składnik modelu COM +.<br /><br /> Skrócona forma `/c`.<br /><br /> Podczas symbol wieloznaczny (\*) można używać podczas określania nazwy składników i interfejsów, zalecamy, aby używać go, ponieważ może narazić interfejsów, które nie ma do.|  
|`/hosting:`\< *complus* &#124; *został*\>|Określa, czy ma być używany tryb lub trybu hostingu sieci Web COM +.<br /><br /> Skrócona forma `/h`.<br /><br /> Za pomocą modelu COM + można zastosować trybu hostingu wymaga jawnego aktywacji aplikacji COM +. Korzystanie z sieci Web trybu hostingu umożliwia aplikacji COM + automatycznie aktywowane jako wymagane. Aplikacja COM + w przypadku aplikacji biblioteki, jest uruchamiana w procesie Internet Information Services (IIS). Aplikacja COM + w przypadku aplikacji serwera, jest uruchamiana w procesie Dllhost.exe.|  
|`/webSite:`\< *Podaną*\>|Określa witrynę sieci Web do obsługi, gdy trybu hostingu w sieci Web jest używana (zobacz `/hosting` flagi).<br /><br /> Skrócona forma `/w`.<br /><br /> Jeśli zostanie określona żadna witryna sieci Web, jest używana domyślna witryna sieci Web.|  
|`/webDirectory:`\< *WebDirectoryName*\>|Określa katalog wirtualny dla hostingu, gdy jest używana usługa hostingu sieci Web (zobacz `/hosting` flagi).<br /><br /> Skrócona forma `/d`.|  
|`/mex`|Dodaje punkt końcowy usługi wymiany metadanych (MEX) w domyślnej konfiguracji usługi do obsługi klientów, które ma zostać pobrane z usługi definicję kontraktu.<br /><br /> Skrócona forma `/x`.|  
|`/id`|Wyświetla aplikacji, składników i informacje o interfejsie jako identyfikatorów.<br /><br /> Skrócona forma `/k`.|  
|`/nologo`|Uniemożliwia wyświetlanie logo jego ComSvcConfig.exe.<br /><br /> Skrócona forma `/n`.|  
|`/verbose`|Wyświetla wszystkie ostrzeżenia i tekst informacyjny oprócz wszystkich wykrytych błędów.<br /><br /> Skrócona forma `/v`.|  
|`/help`|Wyświetla komunikat o sposobie użycia.<br /><br /> Skrócona forma `/?`.|  
|`/partial`|Generuje konfiguracji usługi, jeśli określony interfejs zawiera podpisy metod, które można uwidocznić. Podczas inicjowania usługi zgodne metody są wyświetlane jako operacje na kontrakt usługi i metody niezgodnymi są ignorowane i znajduje się poza kontraktu usługi.<br /><br /> W przypadku braku tej flagi narzędzie nie będą generowane konfiguracji usługi, jeśli określony interfejs zawiera co najmniej jedną metodę niezgodne.|  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie dodano `IFinances` interfejsu `ItemOrders.IFinancial` składnik (z OnlineStore aplikacji COM +), aby zestaw interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +. Wszystkie ostrzeżenia będą dane wyjściowe, oprócz wszystkich wykrytych błędów.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie dodano `IStockLevels` interfejsu `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu hostingu. Usługi sieci Web jest sieci Web hostowanych w OnlineWarehouse katalog wirtualny usług IIS.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Opis  
 Poniższy przykład umożliwia usunięcie `IFinances` interfejsu `ItemOrders.Financial` składnik (z OnlineStore aplikacji COM +) z zestawu interfejsów, które są dostępne jako usługi sieci Web.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Opis  
 Na poniższych listach przykład widoczne obecnie interfejsów modelu COM + hostowanych, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, na podstawie OnlineStore COM + na komputerze lokalnym.  
  
### <a name="code"></a>Kod  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: używanie narzędzia konfiguracji modelu usług COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
