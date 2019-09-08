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
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798914"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx — Funkcja
Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureVerificationEx —](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.  
  
 `fForceVerification`  
 podczas Aby przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; `false`w przeciwnym razie. `true`  
  
 `pfWasVerified`  
 określoną Jeśli podpis silnej nazwy został zweryfikowany; w przeciwnym razie, `false`. `true` `pfWasVerified`jest również ustawiony na `false` , Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 `StrongNameSignatureVerificationEx`zapewnia możliwość podobną do funkcji [StrongNameSignatureVerification —](strongnamesignatureverification-function.md) . Jednak drugi parametr wejściowy i parametr wyjściowy dla `StrongNameSignatureVerificationEx` są typu `BOOLEAN` zamiast `DWORD`.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureVerificationEx, metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification, metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
