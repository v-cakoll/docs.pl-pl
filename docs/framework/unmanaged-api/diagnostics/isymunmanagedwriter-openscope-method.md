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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6a862f0861416ebc80c7b6107267bcbb5ec51f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657366"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope — Metoda
Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie. Zakres staje się nowy zakres bieżący i są wypychane na stosie zakresów. Zakresy należy tworzą hierarchię. Elementy równorzędne są niedozwolone nakładają się na siebie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startOffset`  
 [in] Przesunięcie pierwsza instrukcja w zakresie leksykalnym, w bajtach od początku metody.  
  
 `pRetVal`  
 [out] Wskaźnik do `ULONG32` , która otrzymuje identyfikator zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="remarks"></a>Uwagi  
 `ISymUnmanagedWriter::OpenScope` Zwraca identyfikator nieprzezroczysty zakres, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) Aby zdefiniować zakres użytkownika początkowe i końcowe przesunięcie w późniejszym czasie. W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane. Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
