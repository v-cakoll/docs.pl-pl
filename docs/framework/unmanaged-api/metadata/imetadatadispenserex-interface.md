---
title: IMetaDataDispenserEx — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008056"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx — Interfejs
Rozszerza interfejs [interfejsu IMetaDataDispenser](imetadatadispenser-interface.md) , aby zapewnić możliwość sterowania sposobem działania interfejsów API metadanych w bieżącym zakresie metadanych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindAssembly — Metoda](imetadatadispenserex-findassembly-method.md)|Ta metoda nie jest zaimplementowana. Jeśli zostanie wywołana, zwraca E_NOTIMPL.|  
|[FindAssemblyModule — Metoda](imetadatadispenserex-findassemblymodule-method.md)|Ta metoda nie jest zaimplementowana. Jeśli zostanie wywołana, zwraca E_NOTIMPL.|  
|[GetCORSystemDirectory — Metoda](imetadatadispenserex-getcorsystemdirectory-method.md)|Pobiera katalog, który przechowuje bieżące środowisko uruchomieniowe języka wspólnego (CLR). Ta metoda jest obsługiwana tylko dla debugerów out-of-process. Jeśli wywoływana z innego składnika, zwróci E_NOTIMPL.|  
|[GetOption — Metoda](imetadatadispenserex-getoption-method.md)|Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.|  
|[OpenScopeOnITypeInfo — Metoda](imetadatadispenserex-openscopeonitypeinfo-method.md)|Ta metoda nie jest zaimplementowana. Jeśli zostanie wywołana, zwraca E_NOTIMPL.|  
|[SetOption — Metoda](imetadatadispenserex-setoption-method.md)|Ustawia określoną opcję na daną wartość dla bieżącego zakresu metadanych. Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataDispenser — Interfejs](imetadatadispenser-interface.md)
- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
