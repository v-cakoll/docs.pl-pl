---
title: ICLRRuntimeInfo::IsLoadable — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: a1cd169fc4be5b1dd3ab1a83f4ad143ba2e2442b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007367"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable — Metoda
Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do bieżącego procesu, biorąc pod uwagę inne środowiska uruchomieniowe, które mogły już zostać załadowane do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbLoadable`  
 [out] `true` Jeśli to środowisko uruchomieniowe może zostać załadowane do bieżącego procesu; w przeciwnym razie `false` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pbLoadable`ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli inne środowisko uruchomieniowe jest już załadowane do procesu, a środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do wykonywania równoczesnego, `pbLoadable` zwraca wartość `true` . Jeśli dwa środowiska uruchomieniowe nie mogą być uruchamiane równolegle, `pbLoadable` Funkcja zwraca wartość `false` . Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4 może działać obok siebie w tym samym procesie, przy użyciu środowiska CLR w wersji 2,0 lub CLR w wersji 1,1. Jednak środowisko CLR w wersji 1,1 i środowisko CLR w wersji 2,0 nie mogą być uruchamiane równolegle.  
  
 Jeśli żadne środowisko uruchomieniowe nie zostanie załadowane do procesu, ta metoda zawsze zwraca wartość `true` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
