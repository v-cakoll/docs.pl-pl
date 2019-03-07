---
title: IMetaDataEmit::DefineMethod — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2372aac00473786df9b5deefb969fc02abd8daa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496109"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod — Metoda
Tworzy definicję metody lub funkcja globalna o określonej sygnaturze i zwraca token do tej definicji metody.  
  
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
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypedef` Tokenu w klasie nadrzędnej lub interfejs nadrzędny metody. Ustaw `td` do `mdTokenNil`, jeśli zamierzasz zdefiniować funkcją globalną.  
  
 `szName`  
 [in] Nazwa elementu członkowskiego w formacie Unicode.  
  
 `dwMethodFlags`  
 [in] Wartość [cormethodattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie, które określa atrybuty, metody lub funkcji globalnych.  
  
 `pvSigBlob`  
 [in] Podpis metody. Podpis jest trwały dostarczony. Jeśli musisz określić dodatkowe informacje dotyczące parametrów, należy użyć [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.  
  
 `cbSigBlob`  
 [in] Liczba bajtów w `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] Adres kodu.  
  
 `dwImplFlags`  
 [in] Wartość [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenie, które określa funkcje implementacji metody.  
  
 `pmd`  
 [out] Token składowej.  
  
## <a name="remarks"></a>Uwagi  
 Metadane interfejsu API gwarantuje można utrwalić metod opisanych w tej samej kolejności, jak obiekt wywołujący emituje je dla danego otaczającej klasy lub interfejsu, która została określona w `td` parametru.  
  
 Dodatkowe informacje na temat użytkowania `DefineMethod` i ustawienia określonego parametru są podane poniżej.  
  
## <a name="slots-in-the-v-table"></a>Gniazda w tabeli V  
 Środowisko wykonawcze używa definicji metody, aby skonfigurować miejsc v tabeli. W przypadku, gdy jeden lub więcej miejsc muszą być pominięte, na przykład aby zachować parzystości z układem interfejsu COM, fikcyjnego metoda jest zdefiniowana na podjęcie miejsca lub miejsc, w tabeli v; Ustaw `dwMethodFlags` do `mdRTSpecialName` wartość [cormethodattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie i określ nazwę jako:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 gdzie *SequenceNumber* to numer sekwencji, metody i *CountOfSlots* jest liczba miejsc, aby pominąć w tabeli v. Jeśli *CountOfSlots* jest pominięty, przyjmowana jest wartość 1. Te metody fikcyjnego z rolą nie są wywoływane z poziomu kodu zarządzanego lub niezarządzanego i każda próba ich wywołania w kodzie zarządzanym lub niezarządzanym, generuje wyjątek. Ich służy wyłącznie do zajmują miejsce, w tabeli v generowany przez środowisko uruchomieniowe integracji modelu COM.  
  
## <a name="duplicate-methods"></a>Zduplikowane metody  
 Nie powinna definiować metody zduplikowane. Oznacza to, nie należy wywołać `DefineMethod` z zestawem zduplikowane wartości w `td`, `wzName`, i `pvSig` parametrów. (Te trzy parametry, razem jednoznacznie określić metody.). Jednak można użyć zduplikowanych triple pod warunkiem, że w przypadku jednej z definicji metody, można ustawić `mdPrivateScope` bit w `dwMethodFlags` parametru. ( `mdPrivateScope` Bit oznacza, że kompilator nie zostanie wyemitowany przez odwołanie do tę definicję metody.)  
  
## <a name="method-implementation-information"></a>Informacje o implementacji — metoda  
 Informacje o implementacji metody często nie jest znany w czasie, który jest zadeklarowany metody. W związku z tym, nie trzeba przekazać wartości w `ulCodeRVA` i `dwImplFlags` parametrów podczas wywoływania `DefineMethod`. Wartości, które mogą być dostarczane później za pomocą [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), odpowiednio.  
  
 W niektórych sytuacjach, takich jak wywołania platformy (funkcja PInvoke) lub scenariuszach międzyoperacyjnego modelu COM, treści metody nie zostanie podany, i `ulCodeRVA` powinna być równa zero. W takich sytuacjach metody powinna nie być oznaczane jako abstrakcyjny, ponieważ środowisko uruchomieniowe lokalizuje wdrożenia.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definiowanie metody dla funkcji PInvoke  
 Dla każdego z niezarządzanej funkcji można wywołać za pomocą usług PInvoke należy zdefiniować zarządzanych metodę, która reprezentuje funkcję docelowej niezarządzanych. Aby zdefiniować zarządzaną metodą, należy użyć `DefineMethod` niektórych parametrów niektórych wartości w zależności od sposobu, w którym jest używana funkcja PInvoke:  
  
-   Wartość true, PInvoke — obejmuje wywołania metody niezarządzanego zewnętrznej znajdującej się w niezarządzaną biblioteką DLL.  
  
-   Lokalne PInvoke — obejmuje wywołania metody natywnej niezarządzanych, osadzonego w bieżącym modułu zarządzanego.  
  
 Ustawienia parametru są podane w poniższej tabeli.  
  
|Parametr|Wartości true funkcji PInvoke|Wartości dla lokalnych funkcji PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ustaw `mdStatic`; clear `mdSynchronized` i `mdAbstract`.|  
|`pvSigBlob`|Typy zarządzane prawidłowe wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) podpis metody z parametrami, które są prawidłowe.|Typy zarządzane prawidłowego podpisu metody CLR z parametrami, które są prawidłowe.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ustaw `miCil` i `miManaged`.|Ustaw `miNative` i `miUnmanaged`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
