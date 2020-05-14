---
title: ICorPublishAppDomainEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: a48e20413f466e25a9145e9dbf1ba93d90155770
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397032"
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum — Interfejs
Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , które aktualnie istnieją w ramach procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next — Metoda](icorpublishappdomainenum-next-method.md)|Pobiera określoną liczbę `ICorPublishAppDomain` wystąpień z kolekcji, rozpoczynając od bieżącego położenia.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorPublishAppDomainEnum`Interfejs implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [CorpubPublish — Klasa coclass](corpubpublish-coclass.md)
