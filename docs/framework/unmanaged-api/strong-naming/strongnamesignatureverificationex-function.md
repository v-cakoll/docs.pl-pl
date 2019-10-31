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
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121148"
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
 [in] `true` przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false`.  
  
 `pfWasVerified`  
 [out] `true`, jeśli zweryfikowano podpis silnej nazwy; w przeciwnym razie `false`. `pfWasVerified` jest również ustawiony na `false`, Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `StrongNameSignatureVerificationEx` zapewnia możliwość podobną do funkcji [StrongNameSignatureVerification —](strongnamesignatureverification-function.md) . Jednak drugi parametr wejściowy i parametr wyjściowy dla `StrongNameSignatureVerificationEx` są typu `BOOLEAN` zamiast `DWORD`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureVerificationEx, metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification, metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
