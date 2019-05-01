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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fb081c48abf899b44da1c1351efa3f6036f1c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050210"
---
# <a name="iceegen-interface"></a>ICeeGen — Interfejs
Udostępnia metody dla kompilacji dynamicznej kodu.  
  
 Ten interfejs jest przestarzała i nie powinna być używana.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddSectionReloc, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Nieaktualne. Dodaje instrukcję .reloc do bazy kodu.|  
|[AllocateMethodBuffer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Nieaktualne. Tworzy buforu rozmiaru określonego dla metody, a następnie pobiera adres względny wirtualnej metody.|  
|[ComputePointer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Nieaktualne. Określa bufor dla sekcji określonego kodu.|  
|[EmitString, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Nieaktualne. Emituje określonego ciągu w kodzie podstawowym.|  
|[GenerateCeeFile, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Nieaktualne. Generuje plik bazy kodu, który zawiera kod podstawowy obecnie załadowane w tym `ICeeGen`.|  
|[GenerateCeeMemoryImage, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Nieaktualne. Generuje obrazu w pamięci dla bazy kodu.|  
|[GetIlSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Nieaktualne. Pobiera części bazy kodu języka pośredniego przywoływane przez określone dojście.|  
|[GetIMapTokenIface, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Nieaktualne. Pobiera interfejs odwołuje się określony token.|  
|[GetMethodBuffer, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Nieaktualne. Pobiera odpowiedni rozmiar buforu dla metody o określonym względny adres wirtualny.|  
|[GetSectionBlock, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Nieaktualne. Pobiera blok części bazy kodu.|  
|[GetSectionCreate, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Nieaktualne. Generuje i pobiera sekcję kodu przy użyciu określonej nazwy i wartości flag.|  
|[GetSectionDataLen, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Nieaktualne. Pobiera długość określona sekcja.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Nieaktualne. Pobiera ciąg przechowywaną w określonej względny adres wirtualny.|  
|[GetStringSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Nieaktualne. Pobiera reprezentację ciągu sekcję kodu przywoływane przez określone dojście.|  
|[TruncateSection, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Nieaktualne. Obcina sekcję kodu określonego przez określony czas.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
