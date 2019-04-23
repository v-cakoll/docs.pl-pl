---
title: _EFN_StackTrace — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119993"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace — Funkcja
Zawiera tekst reprezentujący śledzenia stosu z zarządzanego i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzane, a kod zarządzany.  
  
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
  
## <a name="parameters"></a>Parametry  
 `Client`  
 [in] Klient debugowane.  
  
 `wszTextOut`  
 [out] Tekstowa reprezentacja ślad stosu.  
  
 `puiTextLength`  
 [out] Wskaźnik do liczby znaków `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Tablica kontekstów przejścia.  
  
 `puiTransitionContextCount`  
 [out] Wskaźnik do liczby kontekstów przejścia w tablicy.  
  
 `uiSizeOfContext`  
 [in] Rozmiar struktury kontekstu.  
  
 `Flags`  
 [in] Ustaw na wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01) aby wyświetlić rejestr EBP i wskaźnik stosu enter (ESP) przed każdym `module!functionname` wiersza.  
  
## <a name="remarks"></a>Uwagi  
 `_EFN_StackTrace` Struktury mogą być wywoływane z interfejsu programowego WinDbg. Parametry są używane w następujący sposób:  
  
-   Jeśli `wszTextOut` ma wartość null i `puiTextLength` jest inna niż null, funkcja zwraca długość ciągu w `puiTextLength`.  
  
-   Jeśli `wszTextOut` jest inna niż null, funkcja przechowuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`. Zwraca ona pomyślnie, jeśli było wystarczająco dużo miejsca w buforze lub zwraca E_OUTOFMEMORY Jeśli bufor nie jest wystarczająco długie.  
  
-   Przejście część funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` mają obie wartość null. W takim przypadku funkcja zapewnia wywołań przy użyciu tekstu wyjściowego tylko nazwy funkcji.  
  
-   Jeśli `pTransitionContexts` ma wartość null i `puiTransitionContextCount` jest inna niż null, funkcja zwraca niezbędne liczba wpisów kontekstu w `puiTransitionContextCount`.  
  
-   Jeśli `pTransitionContexts` jest inna niż null, funkcja traktuje je jako tablicę struktury o długości `puiTransitionContextCount`. Rozmiar struktury jest nadawana przez `uiSizeOfContext`, a musi być rozmiar [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.  
  
-   `wszTextOut` są zapisywane w następującym formacie:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Jeśli Przesunięcie szesnastkowo 0x0, przesunięcie nie są zapisywane.  
  
-   Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.  
  
-   `Flags` Parametr jest równa 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym `module!functionname` wiersza. Domyślnie to 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
