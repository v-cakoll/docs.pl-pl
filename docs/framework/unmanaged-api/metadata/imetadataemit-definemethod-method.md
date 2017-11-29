---
title: "IMetaDataEmit::DefineMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de55ee714dcba512befae3d2311a9880a08ba29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod — Metoda
Tworzy definicję metody lub funkcji globalnej z określoną sygnaturą i zwraca token do tej definicji metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypedef` Token nadrzędnej klasy lub interfejsu nadrzędnego metody. Ustaw `td` do `mdTokenNil`, jeśli definiujesz funkcją globalną.  
  
 `szName`  
 [in] Nazwa elementu członkowskiego w standardzie Unicode.  
  
 `dwMethodFlags`  
 [in] Wartość [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenia, który określa atrybuty metody lub funkcji globalnej.  
  
 `pvSigBlob`  
 [in] Podpis metody. Podpis jest trwały dostarczony. Aby określić dodatkowe informacje dla wszystkich parametrów, należy użyć [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.  
  
 `cbSigBlob`  
 [in] Liczba bajtów w `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] Adres kodu.  
  
 `dwImplFlags`  
 [in] Wartość [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenie określający funkcji w implementacji metody.  
  
 `pmd`  
 [out] Token elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Gwarantuje metadanych interfejsu API utrwalić metod w tej samej kolejności jak wywołującego emituje je dla danego otaczającej klasy lub interfejsu, która została określona w `td` parametru.  
  
 Dodatkowe informacje na temat stosowania `DefineMethod` i poniżej podano ustawienia określonego parametru.  
  
## <a name="slots-in-the-v-table"></a>Gniazda w tabeli V  
 Środowisko uruchomieniowe używa definicjami metod, aby skonfigurować miejsc v-table. W przypadku, gdy co najmniej jednego gniazda muszą być zostało pominięte, na przykład aby zachować parzystości z układem interfejsu COM fikcyjny — metoda zdefiniowano do podjęcia miejsca lub miejsc, w tabeli v; Ustaw `dwMethodFlags` do `mdRTSpecialName` wartość [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie i określ nazwę jako:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 gdzie *SequenceNumber* to numer sekwencji metody i *CountOfSlots* jest numer gniazda, aby pominąć tabeli v. Jeśli *CountOfSlots* jest pominięty, przyjmowana jest wartość 1. Te metody fikcyjny nie są z kodu zarządzanego lub niezarządzanego i wszelkie próby połączeń telefonicznych z nimi, z kodu zarządzane lub niezarządzane, generuje wyjątek. Ich jedynym celem jest miejsce w tabeli v generujący środowiska uruchomieniowego integracji COM.  
  
## <a name="duplicate-methods"></a>Zduplikowana metody  
 Nie powinna definiować metody zduplikowane. Oznacza to, że nie należy wywołania `DefineMethod` z zestawem zduplikowanych wartości w `td`, `wzName`, i `pvSig` parametrów. (Te trzy parametry razem jednoznacznie określić metodę.). Jednak można użyć zduplikowanych triple pod warunkiem, że w przypadku jednego z definicjami metod, można ustawić `mdPrivateScope` bitu w `dwMethodFlags` parametru. ( `mdPrivateScope` Bit oznacza, że kompilator będzie Emituj odwołania do tej definicji — metoda.)  
  
## <a name="method-implementation-information"></a>Informacje dotyczące implementacji metody  
 Informacje o implementacji metody często nie jest znany w czasie zadeklarowano metody. W związku z tym nie trzeba przekazać wartości w `ulCodeRVA` i `dwImplFlags` parametrów podczas wywoływania metody `DefineMethod`. Wartości, które mogą być dostarczane później za pomocą [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), gdzie to właściwe.  
  
 W niektórych sytuacjach, takich jak wywołania platformy (PInvoke) lub COM interop scenariuszy, treści metody nie zostanie podany, i `ulCodeRVA` powinna być równa zero. W takich przypadkach metoda powinna nie oznaczone jako abstract, ponieważ środowisko uruchomieniowe zlokalizuje implementacji.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definiowanie metody dla funkcji PInvoke  
 Dla każdej funkcji niezarządzanej ma być wywoływana za pomocą funkcji PInvoke musi definiować zarządzanego metodę, która reprezentuje funkcję docelowy niezarządzanych. Aby określić metodę zarządzanych, użyj `DefineMethod` niektóre z parametrów niektórych wartości w zależności od sposobu, w którym jest używana PInvoke:  
  
-   Wartość true, PInvoke — wymaga wywołania metody niezarządzane zewnętrznych znajduje się w bibliotece DLL niezarządzane.  
  
-   Lokalne PInvoke - obejmuje wywołanie metody niezarządzane natywnego osadzonym w bieżącym modułu zarządzanego.  
  
 Ustawienia parametru podano w poniższej tabeli.  
  
|Parametr|Wartości true funkcji PInvoke|Wartości dla lokalnych funkcji PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ustaw `mdStatic`; wyczyść `mdSynchronized` i `mdAbstract`.|  
|`pvSigBlob`|Typy zarządzane wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) metoda podpisu z parametrami, które są prawidłowe.|Typy zarządzane prawidłowy podpis metody CLR z parametrami, które są prawidłowe.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ustaw `miCil` i `miManaged`.|Ustaw `miNative` i `miUnmanaged`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
