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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936503"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE — Struktura
Reprezentuje odwołanie, który sprawia, że aplikacja do zestawu, który aplikacja została zainstalowana w globalnej pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`dwFlags`|Zarezerwowane dla przyszłej rozszerzalności. Ta wartość musi być 0 (zero).|  
|`guidScheme`|Jednostka, która dodaje odwołanie. To pole może mieć jedną z następujących wartości:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: Zestaw odwołuje się aplikacja, która została zainstalowana za pomocą Instalatora Windows firmy Microsoft. `szIdentifier` Pole jest ustawione na `MSI`i `szNonCanonicalData` pole jest ustawione na `Windows Installer`. Ten schemat jest używany dla zestawów side-by-side Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Zestaw odwołuje się do aplikacji, która jest wyświetlana w **Dodaj/Usuń programy** interfejsu. `szIdentifier` Pole zawiera token, który rejestruje aplikację za pomocą **Dodaj/Usuń programy** interfejsu.<br />-FUSION_REFCOUNT_FILEPATH_GUID: Zestaw odwołuje się aplikacja, która jest reprezentowana przez plik w systemie plików. `szIdentifier` Pole zawiera ścieżkę do tego pliku.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Zestaw odwołuje się aplikacja, która jest reprezentowana tylko przez nieprzezroczysty ciąg. `szIdentifier` Pole zawiera to nieprzezroczysty ciąg. Global assembly cache nie sprawdza istnienie odwołania nieprzezroczyste po usunięciu tej wartości.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zastrzeżona.|  
|`szIdentifier`|Unikatowy ciąg, który identyfikuje aplikację, którą zainstalowano zestaw w globalnej pamięci podręcznej. Wartość zależy od wartości `guidScheme` pola.|  
|`szNonCanonicalData`|Ciąg, który jest zrozumiałe dla jednostki, która dodaje odwołanie. Global assembly cache przechowuje te parametry, ale nie jest używana.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie — struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
