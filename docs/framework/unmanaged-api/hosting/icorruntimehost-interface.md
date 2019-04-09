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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec893c898a6cd4abffd525056ed0d0169fcbb288
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184785"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost — Interfejs
Udostępnia metody umożliwiające hosta do uruchamiania i zatrzymywania środowisko uruchomieniowe języka wspólnego (CLR) jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkich domen, uruchomiony w procesie.  
  
 W programie .NET Framework 2.0, ten interfejs jest zastąpione przez [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum — Metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Resetuje wyliczający domeny do początku listy domen.|  
|[CreateDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Tworzy domenę aplikacji. Obiekt wywołujący otrzymuje wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Tworzy domenę aplikacji. Ta metoda umożliwia obiektowi wywołującemu Przekaż wystąpienie iappdomainsetup — Aby skonfigurować dodatkowe funkcje zwracanego <xref:System._AppDomain> wystąpienia.|  
|[CreateDomainSetup, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Pobiera wskaźnik interfejsu typu `IAppDomainSetup` do <xref:System.AppDomainSetup> wystąpienia. `IAppDomainSetup` udostępnia metody umożliwiające konfigurowanie aspektów domeny aplikacji, zanim zostanie on utworzony.|  
|[CreateEvidence, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity>, co pozwala hosta utworzyć dowodów zabezpieczeń do przekazania do [createdomain —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nie używać.|  
|[CurrentDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain> reprezentujący domeny załadowany w bieżącym wątku.|  
|[DeleteLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nie używać.|  
|[EnumDomains, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Pobiera moduł wyliczający dla domen w bieżącym procesie.|  
|[GetConfiguration, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Pobiera obiekt, który zezwala hostów do określenia konfiguracji wywołania zwrotnego środowiska CLR.|  
|[GetDefaultDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain> reprezentujący domyślnej domeny dla bieżącego procesu.|  
|[LocksHeldByLogicalThread, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nie używać.|  
|[MapFile, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapuje określony plik do pamięci. Ta metoda jest przestarzała.|  
|[NextDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Uruchamia środowisko CLR.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.|  
|[SwitchInLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nie używać.|  
|[SwitchOutLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nie używać.|  
|[UnloadDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Zwalnia domeny określonej aplikacji w bieżącym procesie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Hosty środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost — Klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
