---
title: IMapToken::Map — Metoda
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece12247e48a0a005fd542bf76a32a1c6eeaa7cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478405"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map — Metoda
Mapuje relacji między zestawami, przy użyciu sygnatur metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkImp`  
 [in] Token metadanych, który reprezentuje obiekt importowany kodu.  
  
 `tkEmit`  
 [in] Token metadanych, który reprezentuje obiekt emitowany kod.  
  
## <a name="remarks"></a>Uwagi  
 Sytuacji tokenu mapowane ponownie podczas scalania, pierwotny token jest zakresem w zakresie metadanych importowanych (źródło) i obejmuje nowy token w zakresie metadanych emitowany (docelowy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
