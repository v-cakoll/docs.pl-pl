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
ms.openlocfilehash: fd362beb9f8fd7a1f2076eb6490a96c0358520e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432150"
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
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
