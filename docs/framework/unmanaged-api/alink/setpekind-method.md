---
title: SetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179390"
---
# <a name="setpekind-method"></a>SetPEKind — Metoda
Określa typ pliku wykonywalnego przenośnego, specyficznego dla komputera lub niezależnego od komputera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu.  
  
 `FileToken`  
 Token pliku, dla którego ma być ustawiony typ PE. Może mieć `AssemblyID` wartość NULL, jeśli nie oznacza niezwiązanego trybu sieciowego.  
  
 `dwPEKind`  
 Typ PE, wskazany przez [wyliczenie CorPEKind](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 Architektura komputera docelowego, jak wskazano w nagłówku NT.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda powiedzie się.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz też

- [GetPEKind — Metoda](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
