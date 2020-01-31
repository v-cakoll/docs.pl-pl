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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789216"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish — Klasa coclass
Udostępnia interfejsy umożliwiające publikowanie informacji o domenach i procesach aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|[ICorPublish, interfejs](icorpublish-interface.md)|Zapewnia metody publikowania informacji o procesach i domenach aplikacji w tych procesach.|  
|[ICorPublishAppDomain, interfejs](icorpublishappdomain-interface.md)|Reprezentuje i zawiera informacje dotyczące domeny aplikacji w procesie.|  
|[ICorPublishAppDomainEnum, interfejs](icorpublishappdomainenum-interface.md)|Dostarcza metody, które przechodzą przez kolekcję domen aplikacji, które aktualnie istnieją w ramach procesu.|  
|[ICorPublishProcess, interfejs](icorpublishprocess-interface.md)|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[ICorPublishProcessEnum, interfejs](icorpublishprocessenum-interface.md)|Dostarcza metody, które przechodzą przez kolekcję procesów uruchomionych na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Typowy scenariusz publikowania obejmuje dewelopera, który chce debugować kod zarządzany uruchomiony na komputerze w domenie aplikacji. W środowisku hostingu może być uruchomiona więcej niż jedna domena aplikacji w ramach procesu. Deweloper chce użyć graficznego interfejsu użytkownika lub innych metod, aby wyświetlić listę wszystkich procesów uruchomionych na komputerze i wybrać konkretny proces. Lista powinna zawierać wszystkie domeny aplikacji w ramach procesów, które są uruchomione w kodzie zarządzanym. Deweloper może następnie zidentyfikować konkretną domenę aplikacji i dołączyć debuger do tej domeny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
