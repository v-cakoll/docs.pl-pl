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
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503903"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost — Interfejs
Zapewnia metody, które umożliwiają hostowi uruchamianie i zatrzymywanie jawnie środowiska uruchomieniowego języka wspólnego (CLR), w celu utworzenia i skonfigurowania domen aplikacji, uzyskania dostępu do domeny domyślnej i wyliczenia wszystkich domen uruchomionych w procesie.  
  
 W .NET Framework w wersji 2,0 ten interfejs został zastąpiony przez [ICLRRuntimeHost](iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](icorruntimehost-closeenum-method.md)|Resetuje moduł wyliczający domeny z powrotem do początku listy domen.|  
|[CreateDomain, metoda](icorruntimehost-createdomain-method.md)|Tworzy domenę aplikacji. Obiekt wywołujący otrzymuje wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType> .|  
|[CreateDomainEx, metoda](icorruntimehost-createdomainex-method.md)|Tworzy domenę aplikacji. Ta metoda umożliwia obiektowi wywołującemu przekazanie wystąpienia IAppDomainSetup — w celu skonfigurowania dodatkowych funkcji zwracanego <xref:System._AppDomain> wystąpienia.|  
|[CreateDomainSetup, metoda](icorruntimehost-createdomainsetup-method.md)|Pobiera wskaźnik interfejsu typu `IAppDomainSetup` do <xref:System.AppDomainSetup> wystąpienia. `IAppDomainSetup`zapewnia metody konfigurowania aspektów domeny aplikacji przed jej utworzeniem.|  
|[CreateEvidence, metoda](icorruntimehost-createevidence-method.md)|Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity> , który umożliwia hostowi tworzenie dowodu bezpieczeństwa do przekazania do elementu [ondomain](icorruntimehost-createdomain-method.md) lub [CreateDomainEx —](icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, metoda](icorruntimehost-createlogicalthreadstate-method.md)|Nie używaj.|  
|[CurrentDomain, metoda](icorruntimehost-currentdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain> , który reprezentuje domenę załadowana w bieżącym wątku.|  
|[DeleteLogicalThreadState, metoda](icorruntimehost-deletelogicalthreadstate-method.md)|Nie używaj.|  
|[EnumDomains, metoda](icorruntimehost-enumdomains-method.md)|Pobiera moduł wyliczający dla domen w bieżącym procesie.|  
|[GetConfiguration — Metoda](icorruntimehost-getconfiguration-method.md)|Pobiera obiekt, który umożliwia hostowi określenie konfiguracji wywołania zwrotnego środowiska CLR.|  
|[GetDefaultDomain, metoda](icorruntimehost-getdefaultdomain-method.md)|Pobiera wskaźnik interfejsu typu <xref:System._AppDomain> , który reprezentuje domenę domyślną dla bieżącego procesu.|  
|[LocksHeldByLogicalThread, metoda](icorruntimehost-locksheldbylogicalthread-method.md)|Nie używaj.|  
|[MapFile, metoda](icorruntimehost-mapfile-method.md)|Mapuje określony plik do pamięci. Ta metoda jest przestarzała.|  
|[NextDomain, metoda](icorruntimehost-nextdomain-method.md)|Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.|  
|[Start — Metoda](icorruntimehost-start-method.md)|Uruchamia środowisko CLR.|  
|[Stop, metoda](icorruntimehost-stop-method.md)|Kończy wykonywanie kodu w środowisku uruchomieniowym dla bieżącego procesu.|  
|[SwitchInLogicalThreadState, metoda](icorruntimehost-switchinlogicalthreadstate-method.md)|Nie używaj.|  
|[SwitchOutLogicalThreadState, metoda](icorruntimehost-switchoutlogicalthreadstate-method.md)|Nie używaj.|  
|[UnloadDomain, metoda](icorruntimehost-unloaddomain-method.md)|Zwalnia określoną domenę aplikacji z bieżącego procesu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- [Hosting](index.md)
- [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)
- [Hosty środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Hosting, interfejsy](hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](corruntimehost-coclass.md)
