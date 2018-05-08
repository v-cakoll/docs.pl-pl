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
ms.openlocfilehash: 8f144426996583d5058f70daed99d8a37cfb6bfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr — Wyliczenie
Zawiera wartości, które opisano funkcje metody.  
  
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
|`mdPrivateScope`|Określa, że element członkowski nie może być przywoływany.|  
|`mdPrivate`|Określa, że element członkowski jest dostępna tylko dla typu nadrzędnego.|  
|`mdFamANDAssem`|Określa, że element członkowski jest dostępna dla podtypów tylko w tym zestawie.|  
|`mdAssem`|Określa, że element członkowski accessibly wszystkim osobom w zestawie.|  
|`mdFamily`|Określa, czy element członkowski jest dostępny tylko według typu i podtypów.|  
|`mdFamORAssem`|Określa, że element członkowski jest dostępny za pomocą klasy pochodne i innych typów w zestawie jej.|  
|`mdPublic`|Określa, że element członkowski jest dostępna dla wszystkich typów z dostępem do zakresu.|  
|`mdStatic`|Określa, że element członkowski jest zdefiniowany w ramach tego typu, a nie jako element członkowski wystąpienia.|  
|`mdFinal`|Określa, że nie można zastąpić metody.|  
|`mdVirtual`|Określa, czy metoda może zostać zastąpiona.|  
|`mdHideBySig`|Określa, że metoda ukrywa według nazwy i podpisu, a nie tylko według nazwy.|  
|`mdVtableLayoutMask`|Określa układ tabeli wirtualnej.|  
|`mdReuseSlot`|Określa, że można ponownie użyć tej metody w tabeli wirtualnej gniazda. Domyślnie włączone.|  
|`mdNewSlot`|Określa, że metoda zawsze pobiera nowe gniazdo w tabeli wirtualnej.|  
|`mdCheckAccessOnOverride`|Określa, że metoda może zostać przesłonięta przez ten sam typ, do których jest widoczna.|  
|`mdAbstract`|Określa, że metoda nie jest zaimplementowana.|  
|`mdSpecialName`|Określa, czy metoda jest szczególna i że jego nazwa zawiera opis sposobu.|  
|`mdPinvokeImpl`|Określa, że implementacja metody jest przekazywany za pomocą funkcji PInvoke.|  
|`mdUnmanagedExport`|Określa, że metoda jest zarządzana metoda wyeksportowane do kodu niezarządzanego.|  
|`mdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`mdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego powinien sprawdzać kodowanie nazwę metody.|  
|`mdHasSecurity`|Określa, czy metoda ma zabezpieczeń skojarzonych z nim.|  
|`mdRequireSecObject`|Określa, że metoda wymaga innej metody zawierająca kod zabezpieczeń.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
