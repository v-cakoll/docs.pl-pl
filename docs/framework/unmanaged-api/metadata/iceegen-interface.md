---
title: ICeeGen — Interfejs
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426153"
---
# <a name="iceegen-interface"></a>ICeeGen — Interfejs
Zapewnia metody dynamicznego kompilowania kodu.  
  
 Ten interfejs jest przestarzały i nie powinien być używany.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddSectionReloc, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Nieaktualne. Dodaje instrukcję. reloc do bazy kodu.|  
|[AllocateMethodBuffer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Nieaktualne. Tworzy bufor o określonym rozmiarze dla metody i pobiera względny adres wirtualny metody.|  
|[ComputePointer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Nieaktualne. Określa bufor dla określonej sekcji kodu.|  
|[EmitString, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Nieaktualne. Emituje określony ciąg do bazy kodu.|  
|[GenerateCeeFile, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Nieaktualne. Generuje plik bazy kodu, który zawiera bazę kodu, która jest aktualnie załadowana do tego `ICeeGen`.|  
|[GenerateCeeMemoryImage, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Nieaktualne. Generuje obraz w pamięci dla bazy kodu.|  
|[GetIlSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Nieaktualne. Pobiera sekcję bazy kodu języka pośredniego, do której odwołuje się określone dojście.|  
|[GetIMapTokenIface, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Nieaktualne. Pobiera interfejs przywoływany przez określony token.|  
|[GetMethodBuffer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Nieaktualne. Pobiera bufor odpowiedniego rozmiaru dla metody pod określonym względnym adresem wirtualnym.|  
|[GetSectionBlock, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Nieaktualne. Pobiera blok sekcji bazy kodu.|  
|[GetSectionCreate, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Nieaktualne. Generuje i pobiera sekcję kodu przy użyciu podanej wartości Name i flag.|  
|[GetSectionDataLen, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Nieaktualne. Pobiera długość określonej sekcji.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Nieaktualne. Pobiera ciąg przechowywany w określonym względnym adresie wirtualnym.|  
|[GetStringSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Nieaktualne. Pobiera ciąg reprezentujący sekcję kodu, do której odwołuje się określone dojście.|  
|[TruncateSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Nieaktualne. Obcina określoną sekcję kodu o określoną długość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
