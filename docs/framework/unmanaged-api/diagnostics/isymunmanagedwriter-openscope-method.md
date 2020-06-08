---
title: ISymUnmanagedWriter::OpenScope — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 2808606be24399c9a4fe03df4c53202d31cbbe91
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501719"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope — Metoda
Otwiera nowy zakres leksykalny w bieżącej metodzie. Zakres będzie nowym bieżącym zakresem i jest wypychany do stosu zakresów. Zakresy muszą tworzyć hierarchię. Elementy równorzędne nie mogą nakładać się na siebie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `startOffset`  
 podczas Przesunięcie pierwszej instrukcji w zakresie leksykalnym (w bajtach) od początku metody.  
  
 `pRetVal`  
 określoną Wskaźnik do elementu `ULONG32` , który odbiera identyfikator zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `ISymUnmanagedWriter::OpenScope`zwraca nieprzezroczysty identyfikator zakresu, który może być używany z [ISymUnmanagedWriter:: SetScopeRange —](isymunmanagedwriter-setscoperange-method.md) w celu zdefiniowania początkowego i końcowego przesunięcia zakresu w późniejszym czasie. W takim przypadku przesunięcia przesłane do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter:: CloseScope —](isymunmanagedwriter-closescope-method.md) są ignorowane. Identyfikatory zakresów są prawidłowe tylko w bieżącej metodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)
