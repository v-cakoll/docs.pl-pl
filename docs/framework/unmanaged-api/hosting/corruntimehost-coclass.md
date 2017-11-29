---
title: "CorRuntimeHost — Klasa coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3d7a272aff3a3c7d32042b76d37fdb15c9dcad4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost — Klasa coclass
Udostępnia interfejsy związanych z zarządzaniem aplikacjami, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.  
  
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
|[ICorConfiguration — interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).|  
|[ICorRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Udostępnia metody umożliwiające hosta go uruchamiać i zatrzymywać środowisko uruchomieniowe języka wspólnego jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkie domeny uruchomionych w procesie.|  
|[IDebuggerInfo — interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.|  
|[IGCHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.|  
|"IValidator"|Udostępnia metody do weryfikacji przenośnych obrazy wykonywalne i szczegółowe raportowanie błędów sprawdzania poprawności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współklasy hostingu](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
