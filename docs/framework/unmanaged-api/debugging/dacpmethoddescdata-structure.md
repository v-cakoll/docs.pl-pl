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
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203200"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData, struktura

Definiuje bufora transportu dla metody środowiska uruchomieniowego informacje.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
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
