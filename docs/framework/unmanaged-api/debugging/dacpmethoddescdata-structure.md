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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860818"
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

| Członek                       | Opis                                                                                     |
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
**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
- [Standardowe typy danych](../common-data-types-unmanaged-api-reference.md)
