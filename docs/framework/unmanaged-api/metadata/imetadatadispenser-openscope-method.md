---
title: "IMetaDataDispenser::OpenScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope — Metoda
Otwiera istniejący plik na dysku, a następnie mapuje metadanych do pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szScope`  
 [in] Nazwa pliku, który ma zostać otwarty. Plik musi zawierać wspólnych języka wspólnego (CLR) metadanych.  
  
 `dwOpenFlags`  
 [in] Wartość [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić otwierania trybu (do odczytu, zapisu i tak dalej).  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID interfejsu odpowiednie metadane zwrócone; obiekt wywołujący będą używać interfejsu do zaimportowania (odczyt) albo Emituj metadanych (Zapisz).  
  
 Wartość `riid` należy określić jeden z interfejsów "import" lub "Emituj". Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Wskaźnik do interfejsu zwrócony.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu metod z jednego z interfejsów "import", lub dodać do przy użyciu metod z jednego z interfejsów "Emituj" można tworzyć zapytania w pamięci kopie metadanych.  
  
 Jeśli plik docelowy nie zawiera metadanych CLR `OpenScope` metoda zakończy się niepowodzeniem.  
  
 W programie .NET Framework w wersji 1.0 i 1.1, jeśli zakres wersji jest otwarty z `dwOpenFlags` wartość ofRead, jest uprawniona do udostępniania. Oznacza to, że jeśli kolejnych wywołań `OpenScope` przebiegu nazwy pliku, który został uprzednio otwarty zostanie ponownie użyty istniejący zakres i nie jest tworzony nowy zestaw struktur danych. Jednak problemy mogą wystąpić z powodu tego udostępniania.  
  
 W programie .NET Framework w wersji 2.0, zakresy otwarta z `dwOpenFlags` ustawioną ofRead nie będą udostępniane. Użyj wartości ofReadOnly umożliwia zakresu do udostępnienia. Po udostępnieniu zakres kwerendy używające "odczytu/zapisu" interfejsy metadanych nie powiedzie się.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
