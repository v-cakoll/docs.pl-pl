---
title: "StrongNameTokenFromAssemblyEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssemblyEx
helpviewer_keywords: StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef530595d92995124c590e70ac5ffc32a228c67a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx — Funkcja
Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do pliku wykonywalnego przenośnego (PE) dla zestawu.  
  
 `ppbStrongNameToken`  
 [out] Token zwrócony silnej nazwy.  
  
 `pcbStrongNameToken`  
 [out] Rozmiar w bajtach tokenu silnej nazwy.  
  
 `ppbPublicKeyBlob`  
 [out] Zwrócony klucz publiczny.  
  
 `pcbPublicKeyBlob`  
 [out] Rozmiar w bajtach klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy jest skrócona forma klucza publicznego. Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.  
  
 Po klucz jest pobierana i jest tworzony token, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.  
  
 Jeśli `StrongNameTokenFromAssemblyEx` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w mscoree.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameTokenFromAssemblyEx — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [StrongNameTokenFromAssembly — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
