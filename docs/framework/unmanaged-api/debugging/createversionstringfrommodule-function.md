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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492026"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule — Funkcja
Tworzy ciąg wersji ze ścieżki środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego w procesie docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Identyfikator procesu, w którym celem CLR jest załadowany.  
  
 `szModuleName`  
 [in] Pełną lub względną ścieżkę do obiektu docelowego CLR, który jest załadowany do procesu.  
  
 `pBuffer`  
 [out] Zwraca bufor do przechowywania ciągu wersji dla elementu docelowego CLR.  
  
 `cchBuffer`  
 [in] Rozmiar `pBuffer`.  
  
 `pdwLength`  
 [out] Długość ciągu wersji zwracanego przez `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Ciąg wersji dla elementu docelowego CLR została pomyślnie zwrócona w `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` jest wartością null, lub element `pBuffer` lub `cchBuffer` ma wartość null. `pBuffer` i `cchBuffer` muszą być wartość null lub jest inna niż null.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` jest większa niż `cchBuffer`. Może to być oczekiwany wynik, jeśli przekazana wartość null dla obu `pBuffer` i `cchBuffer`i sprawdzać rozmiar buforu niezbędne za pomocą `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` nie zawiera ścieżki do prawidłowe CLR w procesie docelowym.  
  
 E_FAIL (lub inne kody powrotne e_)  
 `pidDebuggee` Nie można znaleźć prawidłowy proces, lub inna awaria.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja akceptuje procesu CLR, która jest identyfikowana przez `pidDebuggee` i ścieżki ciąg, który jest określony przez `szModuleName`. Ciąg wersji jest zwracany w buforze, `pBuffer` wskazuje. Ten ciąg jest nieprzezroczysta dla użytkownika funkcji; oznacza to nie ma znaczenia wewnętrzne w ciąg wersji. Jest używana wyłącznie w kontekście tej funkcji i [createdebugginginterfacefromversion — funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Ta funkcja powinna być wywoływana dwa razy. Gdy wywołujesz ją po raz pierwszy, przekazać wartości null dla obu `pBuffer` i `cchBuffer`. Gdy to zrobisz, rozmiar buforu, które są niezbędne do `pBuffer` zostaną zwrócone w `pdwLength`. Można następnie wywołać funkcję po raz drugi i przekaż bufor w `pBuffer` i jej rozmiar w `cchBuffer`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
