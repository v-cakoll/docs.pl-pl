---
title: ICorRuntimeHost — Interfejs
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139547"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost — Interfejs
Zapewnia metody, które umożliwiają hostowi uruchamianie i zatrzymywanie jawnie środowiska uruchomieniowego języka wspólnego (CLR), w celu utworzenia i skonfigurowania domen aplikacji, uzyskania dostępu do domeny domyślnej i wyliczenia wszystkich domen uruchomionych w procesie.  
  
 W .NET Framework w wersji 2,0 ten interfejs został zastąpiony przez [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Resetuje moduł wyliczający domeny z powrotem do początku listy domen.|  
|[CreateDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Tworzy domenę aplikacji. Obiekt wywołujący otrzymuje wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Tworzy domenę aplikacji. Ta metoda umożliwia obiektowi wywołującemu przekazanie wystąpienia IAppDomainSetup — w celu skonfigurowania dodatkowych funkcji zwracanego wystąpienia <xref:System._AppDomain>.|  
|[CreateDomainSetup, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Pobiera wskaźnik interfejsu typu `IAppDomainSetup` do wystąpienia <xref:System.AppDomainSetup>. `IAppDomainSetup` udostępnia metody konfigurowania aspektów domeny aplikacji przed jej utworzeniem.|  
|[CreateEvidence, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity>, co umożliwia hostowi tworzenie dowodu bezpieczeństwa do przekazania do elementu [ondomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nie używać.|  
|[CurrentDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain> reprezentujący domenę załadowana w bieżącym wątku.|  
|[DeleteLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nie używać.|  
|[EnumDomains, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Pobiera moduł wyliczający dla domen w bieżącym procesie.|  
|[GetConfiguration, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Pobiera obiekt, który umożliwia hostowi określenie konfiguracji wywołania zwrotnego środowiska CLR.|  
|[GetDefaultDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain>, który reprezentuje domenę domyślną dla bieżącego procesu.|  
|[LocksHeldByLogicalThread, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nie używać.|  
|[MapFile, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapuje określony plik do pamięci. Ta metoda jest przestarzała.|  
|[NextDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Uruchamia środowisko CLR.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Kończy wykonywanie kodu w środowisku uruchomieniowym dla bieżącego procesu.|  
|[SwitchInLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nie używać.|  
|[SwitchOutLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nie używać.|  
|[UnloadDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Zwalnia określoną domenę aplikacji z bieżącego procesu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Hosty środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
