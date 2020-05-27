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
ms.openlocfilehash: 7318a7ea3eb1ddb047a799e58ebdfd9ce6cd76d1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007588"
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`ofRead`|Wskazuje, że plik powinien być otwarty tylko do odczytu.|  
|`ofWrite`|Wskazuje, że plik powinien być otwarty do zapisu.<br /><br /> Jeśli używasz `ofWrite` flagi podczas otwierania pliku winmd, należy również przekazać `ofNoTransform` flagę.|  
|`ofReadWriteMask`|Maska do odczytu i zapisu.|  
|`ofCopyMemory`|Wskazuje, że plik powinien być odczytywany do pamięci. Metadane powinny zachować własną kopię.|  
|`ofCacheImage`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofManifestMetadata`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofReadOnly`|Wskazuje, że plik powinien być otwarty do odczytu i że wywołanie `QueryInterface` dla elementu [IMetaDataEmit](imetadataemit-interface.md) nie może zostać wykonane.|  
|`ofTakeOwnership`|Wskazuje, że pamięć została przypisana przy użyciu wywołania do [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona z metadanych.|  
|`ofNoTypeLib`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofNoTransform`|Wskazuje, że należy wyłączyć automatyczne transformacje plików WinMD. Innymi słowy, projekcja typu środowisko wykonawcze systemu Windows do typu .NET Framework powinna być wyłączona. Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze systemu Windows i środowisko CLR poniżej wystawcy z platformą .NET i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|Zarezerwowane do użytku wewnętrznego.|  
|`ofReserved2`|Zarezerwowane do użytku wewnętrznego.|  
|`ofReserved`|Zarezerwowane do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
