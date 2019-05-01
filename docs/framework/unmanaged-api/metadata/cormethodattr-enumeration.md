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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045529"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr — Wyliczenie
Zawiera wartości, które opisano funkcje, które metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`mdMemberAccessMask`|Określa dostęp do elementu członkowskiego.|  
|`mdPrivateScope`|Określa, czy element członkowski nie może być przywoływany.|  
|`mdPrivate`|Określa, że składowa jest dostępne tylko dla typu nadrzędnego.|  
|`mdFamANDAssem`|Określa, czy element członkowski jest dostępny przez podtypy tylko w tym zestawie.|  
|`mdAssem`|Określa, że element członkowski accessibly przez dowolną osobę w zestawie.|  
|`mdFamily`|Określa, czy element członkowski jest dostępny tylko według typu i podtypy.|  
|`mdFamORAssem`|Określa, czy element członkowski jest dostępna, przez klasy pochodne, jak również inne typy w jego zestawie.|  
|`mdPublic`|Określa, że składowa jest dostępny dla wszystkich typów z dostępem do zakresu.|  
|`mdStatic`|Określa, że składowa jest zdefiniowana w ramach tego typu, a nie jako członek wystąpienia.|  
|`mdFinal`|Określa, że nie można zastąpić metody.|  
|`mdVirtual`|Określa, czy metoda może zostać zastąpiona.|  
|`mdHideBySig`|Określa, że metoda ukrywa według nazwy i podpisu, a nie tylko według nazwy.|  
|`mdVtableLayoutMask`|Określa układ tabeli wirtualnej.|  
|`mdReuseSlot`|Określa, miejsca, użyć tej metody w tabeli wirtualnej można użyć ponownie. Domyślnie włączone.|  
|`mdNewSlot`|Określa, że metoda zawsze pobiera nowe gniazdo w tabeli wirtualnej.|  
|`mdCheckAccessOnOverride`|Określa, czy metoda może być zastąpiona przez te same typy, do których jest widoczna.|  
|`mdAbstract`|Określa, że metoda nie jest zaimplementowana.|  
|`mdSpecialName`|Określa, że metoda jest specjalne i czy jego nazwę w tym artykule opisano sposób.|  
|`mdPinvokeImpl`|Określa, że implementacja metody jest przekazywany za pomocą funkcji PInvoke.|  
|`mdUnmanagedExport`|Określa, że metoda jest metodą zarządzanych wyeksportowane do kodu niezarządzanego.|  
|`mdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`mdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego powinien sprawdzać, kodowanie nazwy metody.|  
|`mdHasSecurity`|Określa, że metoda ma zabezpieczeń skojarzonych z nim.|  
|`mdRequireSecObject`|Określa, że metoda wywołuje inną metodę zawierająca kod zabezpieczeń.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
