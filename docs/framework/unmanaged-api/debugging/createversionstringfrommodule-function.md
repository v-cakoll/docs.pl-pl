---
title: CreateVersionStringFromModule — Funkcja
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
ms.openlocfilehash: 1571ff796a10c5ddcd85cc2ce130e62eab2ed8f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132085"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule — Funkcja
Tworzy ciąg wersji ze ścieżki środowiska uruchomieniowego języka wspólnego (CLR) w procesie docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pidDebuggee`  
 podczas Identyfikator procesu, w którym jest ładowany docelowe środowisko CLR.  
  
 `szModuleName`  
 podczas Pełna lub względna ścieżka do docelowego środowiska CLR, który jest ładowany w procesie.  
  
 `pBuffer`  
 określoną Bufor powrotny do przechowywania ciągu wersji dla docelowego środowiska CLR.  
  
 `cchBuffer`  
 podczas Rozmiar `pBuffer`.  
  
 `pdwLength`  
 określoną Długość ciągu wersji zwracanego przez `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Ciąg wersji docelowego środowiska CLR został pomyślnie zwrócony w `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` ma wartość null lub `pBuffer` lub `cchBuffer` ma wartość null. `pBuffer` i `cchBuffer` muszą mieć wartość null lub być wartością null.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` jest większa niż `cchBuffer`. Może to być oczekiwany wynik, jeśli przeszedł wartość null dla obu `pBuffer` i `cchBuffer`i zbadano niezbędny rozmiar buforu przy użyciu `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` nie zawiera ścieżki do prawidłowego środowiska CLR w procesie docelowym.  
  
 E_FAIL (lub inne kody powrotne E_)  
 `pidDebuggee` nie odwołuje się do prawidłowego procesu lub innego błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja akceptuje proces CLR identyfikowany przez `pidDebuggee` i ścieżkę ciągu, która jest określona przez `szModuleName`. Ciąg wersji jest zwracany w buforze, do którego wskazuje `pBuffer`. Ten ciąg jest nieprzezroczysty dla użytkownika funkcji; oznacza to, że nie istnieje żadne wewnętrzne znaczenie w ciągu wersji. Jest używana wyłącznie w kontekście tej funkcji i [funkcji CreateDebuggingInterfaceFromVersion —](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Ta funkcja powinna być wywoływana dwukrotnie. Po pierwszym wywołaniu należy przekazać wartość null dla obu `pBuffer` i `cchBuffer`. Gdy to zrobisz, rozmiar buforu niezbędnego do `pBuffer` zostanie zwrócony w `pdwLength`. Następnie można wywołać funkcję po raz drugi i przekazać bufor w `pBuffer` i jego rozmiar w `cchBuffer`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim. h  
  
 **Biblioteka:** dbgshim. dll  
  
 **.NET Framework wersje:** 3,5 SP1
