---
title: CorMethodAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 779a8f88b7521aa4b0a75594552981b41714ee3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007679"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr — Wyliczenie
Zawiera wartości opisujące funkcje metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`mdMemberAccessMask`|Określa dostęp do elementu członkowskiego.|  
|`mdPrivateScope`|Określa, że nie można odwołać się do elementu członkowskiego.|  
|`mdPrivate`|Określa, że element członkowski jest dostępny tylko dla typu nadrzędnego.|  
|`mdFamANDAssem`|Określa, że element członkowski jest dostępny tylko dla podtypów w tym zestawie.|  
|`mdAssem`|Określa, że element członkowski jest Accessibly przez każdą z nich w zestawie.|  
|`mdFamily`|Określa, że element członkowski jest dostępny tylko dla typów i podtypów.|  
|`mdFamORAssem`|Określa, że element członkowski jest dostępny dla klas pochodnych i innych typów w zestawie.|  
|`mdPublic`|Określa, że element członkowski jest dostępny dla wszystkich typów z dostępem do zakresu.|  
|`mdStatic`|Określa, że element członkowski jest zdefiniowany jako część typu, a nie jako element członkowski wystąpienia.|  
|`mdFinal`|Określa, że nie można zastąpić metody.|  
|`mdVirtual`|Określa, że metoda może zostać przesłonięta.|  
|`mdHideBySig`|Określa, że Metoda ukrywa przez nazwę i podpis, a nie tylko według nazwy.|  
|`mdVtableLayoutMask`|Określa układ tabeli wirtualnej.|  
|`mdReuseSlot`|Określa, że gniazdo używane dla tej metody w tabeli wirtualnej ma być ponownie używane. Domyślnie włączone.|  
|`mdNewSlot`|Określa, że metoda zawsze pobiera nowe miejsce w tabeli wirtualnej.|  
|`mdCheckAccessOnOverride`|Określa, że metoda może być zastąpiona przez te same typy, do których jest widoczna.|  
|`mdAbstract`|Określa, że metoda nie jest zaimplementowana.|  
|`mdSpecialName`|Określa, że metoda jest specjalna i że jej nazwa opisuje sposób.|  
|`mdPinvokeImpl`|Określa, że implementacja metody jest przekazywana za pomocą funkcji PInvoke.|  
|`mdUnmanagedExport`|Określa, że metoda jest metodą zarządzaną eksportowaną do kodu niezarządzanego.|  
|`mdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`mdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego powinno sprawdzać kodowanie nazwy metody.|  
|`mdHasSecurity`|Określa, że do metody są skojarzone zabezpieczenia.|  
|`mdRequireSecObject`|Określa, że metoda wywołuje inną metodę zawierającą kod zabezpieczeń.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
