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
ms.openlocfilehash: a85dc586b0c08fabdd34c018e82314c9003eeded
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171018"
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

- [IMapToken — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
