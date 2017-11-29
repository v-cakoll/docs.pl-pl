---
title: "ICeeGen — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8342c79dd8b7452599af8d9782b0fbec5f83e964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegen-interface"></a>ICeeGen — Interfejs
Udostępnia metody dla kompilacji dynamicznej kodu.  
  
 Ten interfejs jest przestarzały i nie powinna być używana.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddSectionReloc — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Nieaktualne. Dodaje instrukcję .reloc do ścieżki bazowej kodu.|  
|[AllocateMethodBuffer — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Nieaktualne. Tworzy buforu o określonym rozmiarze metody i pobiera adres względny wirtualnej metody.|  
|[ComputePointer — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Nieaktualne. Określa bufor dla określonego kodu sekcji.|  
|[EmitString — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Nieaktualne. Emituje określonego ciągu w bazie kodu.|  
|[GenerateCeeFile — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Nieaktualne. Generuje plik bazowej kodu, który zawiera kod podstawowy załadowanych obecnie do tego `ICeeGen`.|  
|[GenerateCeeMemoryImage — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Nieaktualne. Generuje obrazu w pamięci dla ścieżki bazowej kodu.|  
|[GetIlSection — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Nieaktualne. Pobiera część bazy kodu języka pośredniego odwołuje się określony uchwyt.|  
|[GetIMapTokenIface — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Nieaktualne. Pobiera interfejs odwołuje się określony token.|  
|[GetMethodBuffer — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Nieaktualne. Pobiera odpowiedni rozmiar buforu dla metody pod określonym adresem wirtualnego względną.|  
|[GetSectionBlock — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Nieaktualne. Pobiera blok sekcji ścieżki bazowej kodu.|  
|[GetSectionCreate — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Nieaktualne. Generuje i pobiera sekcji kodu przy użyciu określonej nazwy i wartości flag.|  
|[GetSectionDataLen — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Nieaktualne. Pobiera długość określonej sekcji.|  
|[GetString — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Nieaktualne. Pobiera ciąg przechowywanych na określony wirtualny adres względny.|  
|[GetStringSection — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Nieaktualne. Pobiera reprezentację ciągu sekcji kod odwołuje się określony uchwyt.|  
|[TruncateSection — metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Nieaktualne. Obcina sekcji określonego kodu przez określony czas.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
