---
title: ICorPublishEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: f54bb99df60d7b3fb7bb98de75fbae210597e45c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790626"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum — Interfejs
Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane w publikowaniu informacji o procesach i domenach aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](icorpublishenum-clone-method.md)|Tworzy kopię tego obiektu `ICorPublishEnum`.|  
|[GetCount, metoda](icorpublishenum-getcount-method.md)|Pobiera liczbę elementów w wyliczeniu.|  
|[Reset, metoda](icorpublishenum-reset-method.md)|Przenosi kursor do początku wyliczenia.|  
|[Skip, metoda](icorpublishenum-skip-method.md)|Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące moduły wyliczające pochodzą z `ICorPublishEnum`:  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorpubPublish, klasa coclass](corpubpublish-coclass.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
