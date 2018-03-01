---
title: "CorpubPublish — Klasa coclass"
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
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a>CorpubPublish — Klasa coclass
Udostępnia interfejsy do publikowania informacji o domenach aplikacji i procesów.  
  
## <a name="syntax"></a>Składnia  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|[ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Udostępnia metody do publikowania informacji o procesach i domen aplikacji w tych procesów.|  
|[ICorPublishAppDomain, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Reprezentuje i informacje dotyczące domeny aplikacji w ramach procesu.|  
|[ICorPublishAppDomainEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Udostępnia metody przechodzących przez kolekcję domen aplikacji, które obecnie istnieją w ramach procesu.|  
|[ICorPublishProcess, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[ICorPublishProcessEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Udostępnia metody przechodzących przez kolekcję procesów, które są uruchomione na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Typowy scenariusz publikowania obejmuje deweloperów, którzy chcą do debugowania kodu zarządzanego, który działa na komputerze w domenie aplikacji. Środowisko macierzyste mogą działać więcej niż jednej domeny aplikacji w ramach procesu. Deweloper chce użyć graficznego interfejsu użytkownika lub inne środki, aby wyświetlić listę wszystkich procesów, które są uruchomione na komputerze i pobrania określonego procesu. Listę powinna zawierać wszystkie domeny aplikacji w ramach procesów uruchomionych kodu zarządzanego. Deweloper można zidentyfikować domeny określonej aplikacji i dołączyć do tej domeny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
