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
ms.openlocfilehash: cc5093a5ba0afcccaf960e9b8776f93a061cc2f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785670"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_funkcja ślad stosu
Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, po jednym dla każdego przejścia między niezarządzanym i zarządzanym kodem.  
  
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
 podczas Ustaw wartość na 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01), aby pokazać rejestr EBP oraz wskaźnik wprowadzania stosu (ESP) przed każdą `module!functionname` wierszem.  
  
## <a name="remarks"></a>Uwagi  
 Strukturę `_EFN_StackTrace` można wywołać z interfejsu programistycznego WinDbg. Parametry są używane w następujący sposób:  
  
- Jeśli `wszTextOut` ma wartość null, a `puiTextLength` nie ma wartości null, funkcja zwraca długość ciągu w `puiTextLength`.  
  
- Jeśli `wszTextOut` nie ma wartości null, funkcja zapisuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`. Pomyślnie zwraca wartość, jeśli w buforze było wystarczająco dużo miejsca E_OUTOFMEMORY lub jeśli bufor nie był wystarczająco długi.  
  
- Część przejścia funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` mają wartość null. W takim przypadku funkcja udostępnia obiekty wywołujące z tekstem wyjściowym tylko nazw funkcji.  
  
- Jeśli `pTransitionContexts` ma wartość null, a `puiTransitionContextCount` nie ma wartości null, funkcja zwraca wymaganą liczbę wpisów kontekstu w `puiTransitionContextCount`.  
  
- Jeśli `pTransitionContexts` nie ma wartości null, funkcja traktuje ją jako tablicę struktur o długości `puiTransitionContextCount`. Rozmiar struktury jest określony przez `uiSizeOfContext`i musi być rozmiarem [SimpleContext](stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.  
  
- `wszTextOut` jest zapisywana w następującym formacie:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Jeśli przesunięcie w postaci szesnastkowej jest 0x0, przesunięcie nie jest zapisywane.  
  
- W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.  
  
- Parametr `Flags` ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym wierszem `module!functionname`. Domyślnie jest to 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
