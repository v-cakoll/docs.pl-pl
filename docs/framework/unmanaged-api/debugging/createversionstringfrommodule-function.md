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
ms.openlocfilehash: 0988b2c4471cb5449f7c7fac82c6e94bcd537b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409283"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule — Funkcja
Tworzy ciąg wersji ze wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) ścieżki w procesie docelowym.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pidDebuggee`  
 [in] Identyfikator procesu, w którym element docelowy CLR został załadowany.  
  
 `szModuleName`  
 [in] Pełną lub względną ścieżkę do obiektu docelowego CLR, który jest ładowany w procesie.  
  
 `pBuffer`  
 [out] Zwróć buforu do przechowywania ciąg wersji dla elementu docelowego CLR.  
  
 `cchBuffer`  
 [in] Rozmiar `pBuffer`.  
  
 `pdwLength`  
 [out] Długość ciągu wersji zwrócony przez `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie zwrócono ciąg wersji dla elementu docelowego CLR w `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` jest równa null, lub element `pBuffer` lub `cchBuffer` ma wartość null. `pBuffer` i `cchBuffer` muszą być wartość null lub inną niż null.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` jest większa niż `cchBuffer`. Może to być oczekiwany wynik, jeśli przekazanego wartości null zarówno dla `pBuffer` i `cchBuffer`i rozmiar buforu niezbędne przy użyciu `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` zawiera ścieżkę do prawidłowy CLR w procesie docelowym.  
  
 E_FAIL (lub inne kody powrotu E_)  
 `pidDebuggee` nie odwołuje się nieprawidłowy procesu lub innych awarii.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja akceptuje proces CLR, który jest identyfikowany przez `pidDebuggee` i ciąg ścieżki, która jest określona przez `szModuleName`. Ciąg wersji jest zwracany w buforze który `pBuffer` wskazuje. Ten ciąg jest nieprzezroczysta dla użytkownika funkcji; oznacza to, że jest wewnętrzna znaczenia w sam ciąg wersji. Jest on używany wyłącznie w kontekście tej funkcji i [createdebugginginterfacefromversion — funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Ta funkcja powinna być wywoływana dwukrotnie. Podczas wywoływania po raz pierwszy go przekazać wartości null zarówno dla `pBuffer` i `cchBuffer`. Gdy to zrobisz, rozmiar buforu niezbędne do `pBuffer` zostaną zwrócone w `pdwLength`. Można następnie wywołaj funkcję po raz drugi i przekaż bufor w `pBuffer` i jego rozmiar w `cchBuffer`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** biblioteki dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
