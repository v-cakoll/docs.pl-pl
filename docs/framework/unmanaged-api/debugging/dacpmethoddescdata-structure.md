---
title: DacpMethodDescData, struktura
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793844"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData, struktura

Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski                       | Opis                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Wskazuje, czy środowisko uruchomieniowe ma kod natywny dla danego wystąpienia metody. |
| `bIsDynamic`                 | Wskazuje, czy metoda jest generowana dynamicznie przy użyciu uproszczonego generowania kodu.           |
| `wSlotNumber`                | Numer gniazda metody w tabeli metod.                                                   |
| `NativeCodeAddr`             | Początkowy adres macierzysty metody.                                                            |
| `data`                       | Wskaźnik do bufora używanego wewnętrznie przez środowisko uruchomieniowe.                                             |
| `MethodDescPtr`              | Wskaźnik do `MethodDesc` w środowisku uruchomieniowym.                                                     |
| `nativeCodeInfo`             | Wskaźnik do buforu używany wewnętrznie przez środowisko uruchomieniowe do śledzenia metod.                            |
| `moduleInfo`                 | Wskaźnik do buforu używany wewnętrznie przez środowisko uruchomieniowe w celu uzyskania informacji o modułach.                      |
| `MDToken`                    | Token skojarzony z daną metodą.                                                         |
| `payloadGC`                  | Wskaźnik do buforu wyrzucania elementów bezużytecznych używanego wewnętrznie przez środowisko uruchomieniowe.                          |
| `payloadGC2`                 | Wskaźnik do buforu wyrzucania elementów bezużytecznych używanego wewnętrznie przez środowisko uruchomieniowe.                          |
| `managedDynamicMethodObject` | Jeśli metoda jest dynamiczna, środowisko uruchomieniowe używa tego buforu wewnętrznie do śledzenia informacji.     |
| `requestedIP`                | Służy do wypełniania struktury na żądanie, gdy zostanie udzielony adres kodu natywnego.                    |
| `rejitDataCurrent`           | Informacje o najnowszej wersji Instrumentacji metody.                                   |
| `rejitDataRequested`         | ReJIT informacje o żądanym adresie macierzystym.                                             |
| `cJittedRejitVersions`       | Liczba przypadków, gdy metoda została rejitted przez instrumentację.                           |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę zgodnie z powyższym opisem.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
- [Standardowe typy danych](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
