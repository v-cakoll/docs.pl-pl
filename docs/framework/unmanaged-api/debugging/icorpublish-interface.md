---
title: ICorPublish — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 1bd2f537cfa6a27c24ba91ea7caa29dc9e71a74e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396322"
---
# <a name="icorpublish-interface"></a>ICorPublish — Interfejs
Służy jako ogólny interfejs publikowania informacji o procesach i informacjach o domenach aplikacji w tych procesach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumProcesses, metoda](icorpublish-enumprocesses-method.md)|Pobiera wystąpienie [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , które zawiera zarządzane procesy uruchomione na tym komputerze.|  
|[GetProcess — Metoda](icorpublish-getprocess-method.md)|Pobiera wystąpienie [ICorPublishProcess](icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [CorpubPublish — Klasa coclass](corpubpublish-coclass.md)
