---
title: StrongNameSignatureVerificationEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3f9dbbdf7ff560f292fed327a2ca1dd26c29a19
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491896"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx — Funkcja
Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamesignatureverificationex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego w zestawie, który ma zostać zweryfikowany.  
  
 `fForceVerification`  
 [in] `true` przeprowadzić weryfikację, nawet jeśli jest to konieczne zastąpić ustawienia rejestru; w przeciwnym razie `false`.  
  
 `pfWasVerified`  
 [out] `true` Jeśli podpisu silnej nazwy został zweryfikowany; w przeciwnym razie `false`. `pfWasVerified` jest również ustawiona na `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli weryfikacja się powiodła. w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `StrongNameSignatureVerificationEx` zapewnia możliwości podobne do [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) funkcji. Jednak drugi dane wejściowe i parametru wyjściowego dla `StrongNameSignatureVerificationEx` typu `BOOLEAN` zamiast `DWORD`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w mscoree.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
