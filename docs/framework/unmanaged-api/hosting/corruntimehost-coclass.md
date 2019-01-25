---
title: CorRuntimeHost — Klasa coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c81a39acee31986421c810e2814a4f7e6c4d970
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597531"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost — Klasa coclass
Zawiera interfejsy zarządzania aplikacji, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|[ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Udostępnia metody do konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).|  
|[ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Udostępnia metody umożliwiające hosta do uruchamiania i zatrzymywania środowiska uruchomieniowego języka wspólnego jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkich domen, uruchomiony w procesie.|  
|[IDebuggerInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.|  
|[IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.|  
|Ivalidator "—"|Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów i szczegółowe raporty błędów sprawdzania poprawności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Współklasy hostingu](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
