---
title: CoInitializeEE — Funkcja
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131941"
---
# <a name="coinitializeee-function"></a>CoInitializeEE — Funkcja
Zapewnia, że aparat wykonywania środowiska uruchomieniowego języka wspólnego jest ładowany do procesu. Ta funkcja jest przestarzała w .NET Framework 4. Zamiast tego użyj metody [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFlags`  
 podczas Jedna ze stałych wyliczenia [COINITIEE —](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM zdefiniowane w Winerror. h i wartości w poniższej tabeli.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Aparat wykonywania został załadowany pomyślnie.|  
|S_FALSE|Aparat wykonywania został już załadowany.|  
|E_FAIL|Nie można załadować aparatu wykonywania.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ładuje aparat wykonywania, jeśli nie został wcześniej załadowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
