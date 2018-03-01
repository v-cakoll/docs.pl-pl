---
title: "ICorRuntimeHost — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1280c49c2eea6a06eca10ebd8896b0722e321547
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost — Interfejs
Udostępnia metody umożliwiające hosta go uruchamiać i zatrzymywać środowisko uruchomieniowe języka wspólnego (CLR) jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkie domeny uruchomionych w procesie.  
  
 W programie .NET Framework w wersji 2.0, ten interfejs jest zastąpiona [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Resetuje wyliczający domeny na początku listy domen.|  
|[CreateDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Tworzy domeny aplikacji. Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Tworzy domeny aplikacji. Ta metoda umożliwia obiekt wywołujący, aby przekazać wystąpienia IAppDomainSetup Konfigurowanie dodatkowych funkcji zwracana <xref:System._AppDomain> wystąpienia.|  
|[CreateDomainSetup, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Pobiera wskaźnika interfejsu typu `IAppDomainSetup` do <xref:System.AppDomainSetup> wystąpienia. `IAppDomainSetup`udostępnia metody, aby skonfigurować aspektów domeny aplikacji, zanim zostanie on utworzony.|  
|[CreateEvidence, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Pobiera wskaźnika interfejsu typu <xref:System.Security.Principal.IIdentity>, dzięki czemu hosta utworzyć dowodów zabezpieczeń do przekazania do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nie używać.|  
|[CurrentDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Pobiera wskaźnika interfejsu typu <xref:System._AppDomain> reprezentujący domeny załadowany w bieżącym wątku.|  
|[DeleteLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nie używać.|  
|[EnumDomains, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Pobiera moduł wyliczający dla domen w bieżącym procesie.|  
|[GetConfiguration, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Pobiera obiekt, który umożliwia hosta do określenia konfiguracji wywołanie zwrotne środowiska CLR.|  
|[GetDefaultDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Pobiera wskaźnika interfejsu typu <xref:System._AppDomain> reprezentujący domenę domyślną dla bieżącego procesu.|  
|[LocksHeldByLogicalThread, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nie używać.|  
|[MapFile, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapuje określony plik do pamięci. Ta metoda jest przestarzała.|  
|[NextDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Pobiera wskaźnika interfejsu do następnej domeny w wyliczeniu.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Uruchamia środowisko CLR.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.|  
|[SwitchInLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nie używać.|  
|[SwitchOutLogicalThreadState, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nie używać.|  
|[UnloadDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Zwalnia domeny określonej aplikacji w bieżącym procesie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomain>  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [Hosty w czasie wykonywania](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
