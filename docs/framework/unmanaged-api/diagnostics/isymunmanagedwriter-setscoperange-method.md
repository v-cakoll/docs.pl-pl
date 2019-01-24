---
title: ISymUnmanagedWriter::SetScopeRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da50542d9f57e008b31ce2e6ed9698df1275d5eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618814"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange — Metoda
Definiuje zakres przesunięcia dla określonego zakresu leksykalne. Zakres staje się nowy zakres bieżący i są wypychane na stosie zakresów. Zakresy należy tworzą hierarchię. Elementy równorzędne są niedozwolone nakładają się na siebie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scopeId`  
 [in] Identyfikator zakresu dla zakresu.  
  
 `startOffset`  
 [in] Przesunięcie w bajtach, pierwsza instrukcja w zakresie leksykalnym od samego początku metody.  
  
 `endOffset`  
 [in] Przesunięcie w bajtach ostatniej instrukcji w zakresie leksykalnym od samego początku metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="remarks"></a>Uwagi  
 [ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator nieprzezroczysty zakres, który może być używany z `ISymUnmanagedWriter::SetScopeRange` Aby zdefiniować zakres użytkownika początkowe i końcowe przesunięcie w późniejszym czasie. W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane. Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
