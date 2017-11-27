---
title: "_EFN_StackTrace — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_StackTrace
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_StackTrace
helpviewer_keywords: _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 031812b2c286c5647afb9c88882f22e2c7c3addf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace — Funkcja
Udostępnia reprezentację tekst ślad stosu zarządzanych i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzanych i kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [in] Klient debugowany.  
  
 `wszTextOut`  
 [out] Reprezentacja tekstowa typu ślad stosu.  
  
 `puiTextLength`  
 [out] Wskaźnik do liczba znaków w `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Tablica kontekstów przejścia.  
  
 `puiTransitionContextCount`  
 [out] Wskaźnik do różnych kontekstach przejścia w tablicy.  
  
 `uiSizeOfContext`  
 [in] Rozmiar struktury kontekstu.  
  
 `Flags`  
 [in] Wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01) do wyświetlenia rejestru EBP i wprowadź wskaźnik stosu (ESP) przed każdym `module!functionname` wiersza.  
  
## <a name="remarks"></a>Uwagi  
 `_EFN_StackTrace` Struktury może zostać wywołana z interfejsu programowego WinDbg. Parametry są używane w następujący sposób:  
  
-   Jeśli `wszTextOut` ma wartość null i `puiTextLength` jest niezerowa, funkcja zwraca długość ciągu w `puiTextLength`.  
  
-   Jeśli `wszTextOut` jest niezerowa, funkcja przechowuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`. Zwraca go pomyślnie, jeśli było wystarczająco dużo miejsca w buforze lub zwraca E_OUTOFMEMORY Jeśli bufor nie był wystarczająco długi.  
  
-   Przejście część funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` są obie wartości null. W takim przypadku funkcja udostępnia wywołań z tekst wyjściowy tylko nazwy funkcji.  
  
-   Jeśli `pTransitionContexts` ma wartość null i `puiTransitionContextCount` jest niezerowa, funkcja zwraca niezbędne liczbę wpisów kontekstu w `puiTransitionContextCount`.  
  
-   Jeśli `pTransitionContexts` jest niezerowa, funkcja traktuje ją jako tablica struktury o długości `puiTransitionContextCount`. Rozmiar struktury jest określany przez `uiSizeOfContext`, a musi być rozmiar [simplecontext —](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.  
  
-   `wszTextOut`są zapisywane w następującym formacie:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Jeśli Przesunięcie szesnastkowo 0x0, przesunięcie nie są zapisywane.  
  
-   Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.  
  
-   `Flags` Parametr ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby wyświetlić EBP i ESP przed każdym `module!functionname` wiersza. Domyślnie jest 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
