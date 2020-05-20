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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616525"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost — Klasa coclass
Udostępnia interfejsy do zarządzania aplikacjami, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|[ICorConfiguration, interfejs](icorconfiguration-interface.md)|Zapewnia metody konfigurowania środowiska uruchomieniowego języka wspólnego (CLR).|  
|[ICorRuntimeHost, interfejs](icorruntimehost-interface.md)|Zapewnia metody umożliwiające uruchamianie hosta i zatrzymywanie jawnie środowiska uruchomieniowego języka wspólnego, tworzenie i Konfigurowanie domen aplikacji, dostęp do domeny domyślnej oraz wyliczanie wszystkich domen uruchomionych w procesie.|  
|[IDebuggerInfo, interfejs](idebuggerinfo-interface.md)|Zapewnia metody uzyskiwania informacji o stanie usług debugowania.|  
|[IGCHost, interfejs](igchost-interface.md)|Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.|  
|IValidator|Zapewnia metody weryfikacji przenośnych obrazów wykonywalnych i szczegółowe raportowanie błędów walidacji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Współklasy hostingu](hosting-coclasses.md)
