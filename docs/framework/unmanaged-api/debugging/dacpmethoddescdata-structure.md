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
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739132"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData, struktura

Definiuje bufora transportu dla metody środowiska uruchomieniowego informacje.

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
| `bHasNativeCode`             | Wskazuje, czy środowisko uruchomieniowe jest kodu natywnego, które są dostępne dla danego wystąpienia metody. |
| `bIsDynamic`                 | Wskazuje, jeśli metoda jest generowany dynamicznie za pośrednictwem generowania kodu uproszczone.           |
| `wSlotNumber`                | Numer gniazda metody w tabeli metod.                                                   |
| `NativeCodeAddr`             | Metoda początkowej adresu natywnego.                                                            |
| `data`                       | Wskaźnik do buforu używana wewnętrznie w czasie wykonywania.                                             |
| `MethodDescPtr`              | Wskaźnik do `MethodDesc` w środowisku uruchomieniowym.                                                     |
| `nativeCodeInfo`             | Wskaźnik do buforu używana wewnętrznie przez środowisko uruchomieniowe w celu śledzenia metody.                            |
| `moduleInfo`                 | Wskaźnik do buforu używana wewnętrznie przez środowisko uruchomieniowe, aby uzyskać informacje o module.                      |
| `MDToken`                    | Token skojarzony z danej metody.                                                         |
| `payloadGC`                  | Wskaźnik do buforu kolekcji wyrzucania elementów używana wewnętrznie w czasie wykonywania.                          |
| `payloadGC2`                 | Wskaźnik do buforu kolekcji wyrzucania elementów używana wewnętrznie w czasie wykonywania.                          |
| `managedDynamicMethodObject` | Jeśli metoda jest dynamiczny, środowisko wykonawcze używa tego buforu wewnętrznie informacji śledzenia.     |
| `requestedIP`                | Używany do wypełniania struktury na żądanie, gdy podano adres kodu natywnego.                    |
| `rejitDataCurrent`           | Informacje o najnowszych instrumentowanej wersji metody.                                   |
| `rejitDataRequested`         | Rejit informacji dla żądanego adresu natywnego.                                             |
| `cJittedRejitVersions`       | Liczba przypadków, gdy metoda została rejitted za pomocą Instrumentacji.                           |

## <a name="remarks"></a>Uwagi

Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki. Aby go użyć, definiują strukturę, jak określono powyżej.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Standardowe typy danych](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
