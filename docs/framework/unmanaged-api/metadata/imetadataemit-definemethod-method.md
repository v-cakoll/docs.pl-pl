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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177665"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod — Metoda
Tworzy definicję metody lub funkcji globalnej z określonym podpisem i zwraca token do tej definicji metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] Token `mdTypedef` klasy nadrzędnej lub nadrzędnego interfejsu metody. Ustaw `td` `mdTokenNil`na , jeśli definiujesz funkcję globalną.  
  
 `szName`  
 [w] Nazwa elementu członkowskiego w unicode.  
  
 `dwMethodFlags`  
 [w] Wartość wyliczenia [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) która określa atrybuty metody lub funkcji globalnej.  
  
 `pvSigBlob`  
 [w] Podpis metody. Podpis jest zachowywany zgodnie z podano. Jeśli chcesz określić dodatkowe informacje dla dowolnych parametrów, użyj [metody IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)  
  
 `cbSigBlob`  
 [w] Liczba bajtów `pvSigBlob`w pliku .  
  
 `ulCodeRVA`  
 [w] Adres kodu.  
  
 `dwImplFlags`  
 [w] Wartość wyliczenia [CorMethodImpl,](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) która określa funkcje implementacji metody.  
  
 `pmd`  
 [na zewnątrz] Token elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs API metadanych gwarantuje, że metody utrwalania w tej samej kolejności, w jakiej `td` wywoływany jest, emituje je dla danej klasy lub interfejsu otaczającego, który jest określony w parametrze.  
  
 Dodatkowe informacje dotyczące `DefineMethod` korzystania z poszczególnych ustawień parametrów znajdują się poniżej.  
  
## <a name="slots-in-the-v-table"></a>Szczeliny w tabeli V  
 Środowisko wykonawcze używa definicji metod do konfigurowania gniazd v-table. W przypadku, gdy należy pominąć jedno lub więcej gniazd, na przykład w celu zachowania parytetu z układem interfejsu COM, metoda manekina jest definiowana w celu uwzględnienia gniazda lub gniazd w tabeli v; ustawić `dwMethodFlags` wartość `mdRTSpecialName` wyliczenia [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) i określić nazwę jako:  
  
 \<_VtblGap*SequenceNumber*>\<\_*CountOfSlots*>
  
 gdzie *SequenceNumber* jest numerem sekwencyjnym metody i *CountOfSlots* jest liczba gniazd do pominięcia w tabeli v. Jeśli *CountOfSlots zostanie pominięty,* zakłada się 1. Te metody fikcyjne nie są wywoływane z kodu zarządzanego lub niezarządzanego i każda próba wywołania ich, z kodu zarządzanego lub niezarządzanego, generuje wyjątek. Ich jedynym celem jest zajmie miejsce w tabeli v, który generuje środowisko wykonawcze dla integracji com.  
  
## <a name="duplicate-methods"></a>Zduplikowane metody  
 Nie należy definiować zduplikowanych metod. Oznacza to, że `DefineMethod` nie należy wywoływać z `td` `wzName`duplikatem zestawu wartości w , i `pvSig` parametrów. (Te trzy parametry razem jednoznacznie definiują metodę.). Można jednak użyć zduplikowanej potrójnej, pod warunkiem, że `mdPrivateScope` dla `dwMethodFlags` jednej z definicji metody można ustawić bit w parametrze. (Bit `mdPrivateScope` oznacza, że kompilator nie będzie emitować odwołanie do tej definicji metody.)  
  
## <a name="method-implementation-information"></a>Informacje o implementacji metody  
 Informacje o implementacji metody często nie jest znany w momencie zadeklarowania metody. W związku z tym nie trzeba `ulCodeRVA` przekazywać wartości w i `dwImplFlags` parametry podczas wywoływania `DefineMethod`. Wartości mogą być dostarczane później za pośrednictwem [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), odpowiednio.  
  
 W niektórych sytuacjach, takich jak wywołanie platformy (PInvoke) lub współdziałania COM `ulCodeRVA` scenariusze, treść metody nie zostaną dostarczone i powinny być ustawione na zero. W takich sytuacjach metoda nie powinna być oznaczana jako abstrakcyjna, ponieważ środowisko wykonawcze zlokalizuje implementację.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definiowanie metody pinvoke  
 Dla każdej funkcji niezarządzanej, która ma być wywoływana za pośrednictwem PInvoke, należy zdefiniować metodę zarządzaną, która reprezentuje docelową funkcję niezarządzaną. Aby zdefiniować metodę `DefineMethod` zarządzaną, należy użyć z niektórymi parametrami ustawionymi na określone wartości, w zależności od sposobu, w jaki jest używany PInvoke:  
  
- True PInvoke - obejmuje wywołanie zewnętrznej metody niezarządzanej, która znajduje się w niezarządzanej biblioteki DLL.  
  
- Local PInvoke - obejmuje wywołanie macierzystej metody niezarządzanej, która jest osadzona w bieżącym module zarządzanym.  
  
 Ustawienia parametrów podano w poniższej tabeli.  
  
|Parametr|Wartości dla prawdziwego PInvoke|Wartości dla lokalnego PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Zestaw `mdStatic`; jasne `mdSynchronized` `mdAbstract`i .|  
|`pvSigBlob`|Podpis metody prawidłowego wspólnego środowiska wykonawczego języka (CLR) z parametrami, które są prawidłowymi typami zarządzanymi.|Prawidłowy podpis metody CLR z parametrami, które są prawidłowymi typami zarządzanymi.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Zestaw `miCil` `miManaged`i .|Zestaw `miNative` `miUnmanaged`i .|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
