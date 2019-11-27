---
title: CorOpenFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436506"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags — Wyliczenie
Zawiera wartości flag kontrolujące zachowanie metadanych podczas otwierania plików manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ofRead`|Wskazuje, że plik powinien być otwarty tylko do odczytu.|  
|`ofWrite`|Wskazuje, że plik powinien być otwarty do zapisu.<br /><br /> Jeśli używasz flagi `ofWrite` podczas otwierania pliku winmd, należy również przekazać flagę `ofNoTransform`.|  
|`ofReadWriteMask`|Maska do odczytu i zapisu.|  
|`ofCopyMemory`|Wskazuje, że plik powinien być odczytywany do pamięci. Metadane powinny zachować własną kopię.|  
|`ofCacheImage`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofManifestMetadata`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofReadOnly`|Wskazuje, że plik powinien być otwarty do odczytu i że nie można wykonać wywołania `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) .|  
|`ofTakeOwnership`|Wskazuje, że pamięć została przypisana przy użyciu wywołania do [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona z metadanych.|  
|`ofNoTypeLib`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofNoTransform`|Wskazuje, że należy wyłączyć automatyczne transformacje plików WinMD. Innymi słowy, projekcja typu środowisko wykonawcze systemu Windows do typu .NET Framework powinna być wyłączona. Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze systemu Windows i środowisko CLR poniżej wystawcy z platformą .NET i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|Przeznaczone do użytku wewnętrznego.|  
|`ofReserved2`|Przeznaczone do użytku wewnętrznego.|  
|`ofReserved`|Przeznaczone do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
