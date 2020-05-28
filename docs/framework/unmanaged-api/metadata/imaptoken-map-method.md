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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008199"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map — Metoda
Mapuje relacje między zestawami przy użyciu podpisów metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkImp`  
 podczas Token metadanych reprezentujący zaimportowany obiekt kodu.  
  
 `tkEmit`  
 podczas Token metadanych reprezentujący emitowany obiekt kodu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy ponowne mapowanie tokenu odbywa się podczas scalania, oryginalny token jest objęty zakresem zaimportowanego (źródłowego) zakresu metadanych, a nowy token jest objęty zakresem metadanych emitowanych (docelowych).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMapToken, interfejs](imaptoken-interface.md)
