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
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860912"
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
  
|Interface|Opis|  
|---------------|-----------------|  
|[ICorPublish — Interfejs](icorpublish-interface.md)|Zapewnia metody publikowania informacji o procesach i domenach aplikacji w tych procesach.|  
|[ICorPublishAppDomain — Interfejs](icorpublishappdomain-interface.md)|Reprezentuje i zawiera informacje dotyczące domeny aplikacji w procesie.|  
|[ICorPublishAppDomainEnum — Interfejs](icorpublishappdomainenum-interface.md)|Dostarcza metody, które przechodzą przez kolekcję domen aplikacji, które aktualnie istnieją w ramach procesu.|  
|[ICorPublishProcess — Interfejs](icorpublishprocess-interface.md)|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[ICorPublishProcessEnum — Interfejs](icorpublishprocessenum-interface.md)|Dostarcza metody, które przechodzą przez kolekcję procesów uruchomionych na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Typowy scenariusz publikowania obejmuje dewelopera, który chce debugować kod zarządzany uruchomiony na komputerze w domenie aplikacji. W środowisku hostingu może być uruchomiona więcej niż jedna domena aplikacji w ramach procesu. Deweloper chce użyć graficznego interfejsu użytkownika lub innych metod, aby wyświetlić listę wszystkich procesów uruchomionych na komputerze i wybrać konkretny proces. Lista powinna zawierać wszystkie domeny aplikacji w ramach procesów, które są uruchomione w kodzie zarządzanym. Deweloper może następnie zidentyfikować konkretną domenę aplikacji i dołączyć debuger do tej domeny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie](index.md)
