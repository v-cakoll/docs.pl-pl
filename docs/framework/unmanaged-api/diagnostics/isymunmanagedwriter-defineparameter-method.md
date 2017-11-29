---
title: "ISymUnmanagedWriter::DefineParameter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineParameter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 166087a27d0aa7b100da563c25f7e5a52612ce50
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter — Metoda
Określa pojedynczy parametr w bieżącej metodzie. Typ parametru jest pobierana z parametru pozycji (sekwencji) w podpisie metody.  
  
 Parametry są definiowane w metadanych dla danej metody, nie trzeba definiować ich ponownie za pomocą tej metody. Czytniki symbol musi sprawdzić normalne metadane parametrów przed zaewidencjonowaniem magazynu symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Nazwa parametru.  
  
 `attributes`  
 [in] Atrybuty parametrów.  
  
 `sequence`  
 [in] Sygnatura parametru.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres Specyfikacja parametru.  
  
 `addr2`  
 [in] Drugi adres Specyfikacja parametru.  
  
 `addr3`  
 [in] Trzeci adres Specyfikacja parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
