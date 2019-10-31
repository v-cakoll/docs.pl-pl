---
title: FUSION_INSTALL_REFERENCE — Struktura
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: 3859752fd92a76f3fef1ceced0e792109b65106a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108280"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE — Struktura
Reprezentuje odwołanie do zestawu, który aplikacja została zainstalowana w globalnej pamięci podręcznej zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`cbSize`|Rozmiar struktury w bajtach.|  
|`dwFlags`|Zarezerwowane do użytku w przyszłości. Ta wartość musi być równa 0 (zero).|  
|`guidScheme`|Jednostka, która dodaje odwołanie. To pole może mieć jedną z następujących wartości:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: zestaw odwołuje się do aplikacji, która została zainstalowana przy użyciu Instalator Windows Microsoft. Pole `szIdentifier` jest ustawione na `MSI`, a pole `szNonCanonicalData` jest ustawione na `Windows Installer`. Ten schemat jest używany dla zestawów równoległych systemu Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: zestaw odwołuje się do aplikacji, która pojawia się w interfejsie **Dodaj/Usuń programy** . Pole `szIdentifier` zawiera token, który rejestruje aplikację przy użyciu interfejsu **Dodaj/Usuń programy** .<br />-FUSION_REFCOUNT_FILEPATH_GUID: zestaw odwołuje się do aplikacji reprezentowanej przez plik w systemie plików. Pole `szIdentifier` zawiera ścieżkę do tego pliku.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: zestaw odwołuje się do aplikacji reprezentowanej tylko przez nieprzezroczysty ciąg. Pole `szIdentifier` zawiera ten ciąg nieprzezroczysty. Globalna pamięć podręczna zestawów nie sprawdza istnienia nieprzezroczystych odwołań po usunięciu tej wartości.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zarezerwowana.|  
|`szIdentifier`|Unikatowy ciąg identyfikujący aplikację, która zainstalowała zestaw w globalnej pamięci podręcznej zestawów. Jego wartość zależy od wartości pola `guidScheme`.|  
|`szNonCanonicalData`|Ciąg, który jest zrozumiały tylko dla jednostki, która dodaje odwołanie. Globalna pamięć podręczna zestawów przechowuje ten ciąg, ale nie używa go.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie — struktury](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
