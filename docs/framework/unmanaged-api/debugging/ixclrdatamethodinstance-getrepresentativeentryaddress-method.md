---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 6f204e2ed9cb1409d53432355467bb11946f8809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775535"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method

Pobiera najbardziej reprezentatywnej adres punktu wejścia dla natywnej kompilacji wszystkie możliwe punkty wejścia dla metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>Parametry

`addr`\
[out] Adres najbardziej reprezentatywnej natywnego punktu wejścia dla metody.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią [ `IXCLRDataMethodInstance` interfejsu](ixclrdatamethodinstance-interface.md) i odpowiada 19 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Interfejs IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
