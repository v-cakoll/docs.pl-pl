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
ms.openlocfilehash: a725aa2c0f1fdea523bbf7cba880bc805f855782
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860733"
---
# <a name="_efn_stacktrace-function"></a>\_Funkcja\_EFN ślad stosu
Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, jeden dla każdego przejścia między niezarządzanym i zarządzanym kodem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Debugowany klient.  
  
 `wszTextOut`  
 określoną Tekstowa reprezentacja śladu stosu.  
  
 `puiTextLength`  
 określoną Wskaźnik do liczby znaków w `wszTextOut`.  
  
 `pTransitionContexts`  
 określoną Tablica kontekstów przejścia.  
  
 `puiTransitionContextCount`  
 określoną Wskaźnik do liczby kontekstów przejścia w tablicy.  
  
 `uiSizeOfContext`  
 podczas Rozmiar struktury kontekstu.  
  
 `Flags`  
 podczas Ustaw wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01), aby pokazać rejestr EBP i wskaźnik wprowadzania stosu (ESP) przed każdym `module!functionname` wierszem.  
  
## <a name="remarks"></a>Uwagi  
 `_EFN_StackTrace` Strukturę można wywołać z interfejsu programistycznego WinDbg. Parametry są używane w następujący sposób:  
  
- Jeśli `wszTextOut` ma wartość null `puiTextLength` i nie ma wartości null, funkcja zwraca długość ciągu w `puiTextLength`.  
  
- Jeśli `wszTextOut` wartość nie jest równa null, funkcja przechowuje `wszTextOut` tekst w do lokalizacji wskazanej `puiTextLength`przez. Pomyślnie zwraca wartość, jeśli w buforze było wystarczająco dużo miejsca E_OUTOFMEMORY lub jeśli bufor nie był wystarczająco długi.  
  
- Część przejścia funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` ma wartość null. W takim przypadku funkcja udostępnia obiekty wywołujące z tekstem wyjściowym tylko nazw funkcji.  
  
- Jeśli `pTransitionContexts` ma wartość null `puiTransitionContextCount` i nie ma wartości null, funkcja zwraca wymaganą liczbę wpisów kontekstu w `puiTransitionContextCount`.  
  
- Jeśli `pTransitionContexts` wartość nie jest równa null, funkcja traktuje ją jako tablicę struktur `puiTransitionContextCount`długości. Rozmiar struktury jest określony przez `uiSizeOfContext`i musi być rozmiarem [SimpleContext](stacktrace-simplecontext-structure.md) lub `CONTEXT` architekturą.  
  
- `wszTextOut`jest zapisywana w następującym formacie:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Jeśli przesunięcie w postaci szesnastkowej jest 0x0, przesunięcie nie jest zapisywane.  
  
- W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.  
  
- `Flags` Parametr ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym `module!functionname` wierszem. Domyślnie jest to 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
