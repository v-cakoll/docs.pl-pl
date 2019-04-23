---
title: CorpubPublish — Klasa coclass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130536"
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
|[ICorPublishAppDomain, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Reprezentuje i zawiera informacje dotyczące domeny aplikacji w ramach procesu.|  
|[ICorPublishAppDomainEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Udostępnia metody, które przemierzają kolekcję domen aplikacji, które obecnie istnieją w ramach procesu.|  
|[ICorPublishProcess, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[ICorPublishProcessEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Udostępnia metody, które przemierzają kolekcję procesów, które są uruchomione na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Typowy scenariusz publikowania obejmuje deweloperem i potrzebujesz do debugowania kodu zarządzanego, który jest uruchomiony na komputerze w domenie aplikacji. Środowisko hostingu może działać więcej niż jedną domenę aplikacji w ramach procesu. Deweloper chce użyć graficznego interfejsu użytkownika lub inne metody, aby wyświetlić listę wszystkich procesów, które są uruchomione na komputerze, a następnie wybierz określony proces. Listę powinien zawierać wszystkie domeny aplikacji wewnątrz procesów uruchomionych w kodzie zarządzanym. Deweloper można zidentyfikować określonej domenie aplikacji i dołączyć debuger do tej domeny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
