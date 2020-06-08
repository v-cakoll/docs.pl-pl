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
ms.openlocfilehash: fbf6ce8c8c9628b08872058a794fb0e005764ab1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501303"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod — Metoda
Tworzy definicję metody lub funkcji globalnej z określoną sygnaturą i zwraca token do tej definicji metody.  
  
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
 podczas `mdTypedef`Token klasy nadrzędnej lub interfejsu nadrzędnego metody. Ustaw `td` na `mdTokenNil` , jeśli definiujesz funkcję globalną.  
  
 `szName`  
 podczas Nazwa elementu członkowskiego w formacie Unicode.  
  
 `dwMethodFlags`  
 podczas Wartość wyliczenia [CorMethodAttr —](cormethodattr-enumeration.md) , która określa atrybuty metody lub funkcji globalnej.  
  
 `pvSigBlob`  
 podczas Podpis metody. Sygnatura jest utrwalana zgodnie z podanym opisem. Jeśli konieczne jest określenie dodatkowych informacji dla dowolnych parametrów, użyj metody [IMetaDataEmit:: SetParamProps —](imetadataemit-setparamprops-method.md) .  
  
 `cbSigBlob`  
 podczas Liczba bajtów w `pvSigBlob` .  
  
 `ulCodeRVA`  
 podczas Adres kodu.  
  
 `dwImplFlags`  
 podczas Wartość wyliczenia [CorMethodImpl —](cormethodimpl-enumeration.md) , która określa funkcje implementacji metody.  
  
 `pmd`  
 określoną Token elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs API metadanych gwarantuje zachowanie metod w takiej samej kolejności, w jakiej obiekt wywołujący emituje je dla danej klasy lub interfejsu, który jest określony w `td` parametrze.  
  
 Poniżej przedstawiono dodatkowe informacje dotyczące używania `DefineMethod` i określonych ustawień parametrów.  
  
## <a name="slots-in-the-v-table"></a>Gniazda w tabeli V  
 Środowisko uruchomieniowe używa definicji metod do konfigurowania miejsc z tabelą v. W przypadku, gdy co najmniej jeden z gniazd musi być pominięty, na przykład w celu zachowania parzystości przy użyciu układu interfejsu COM, Metoda fikcyjna jest definiowana w celu założenia gniazda lub gniazd w tabeli v. Ustaw `dwMethodFlags` na `mdRTSpecialName` wartość wyliczenia [CorMethodAttr —](cormethodattr-enumeration.md) i określ nazwę jako:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 gdzie *SequenceNumber* jest numerem sekwencji metody, a *CountOfSlots* to liczba gniazd do pominięcia w tabeli v. W przypadku pominięcia *CountOfSlots* przyjmuje się wartość 1. Te metody fikcyjne nie są wywoływane z kodu zarządzanego lub niezarządzanego, a wszystkie próby wywołania ich, z kodu zarządzanego lub niezarządzanego, generują wyjątek. Jedynym celem jest zajęcie miejsca w tabeli v, która jest generowana przez środowisko uruchomieniowe na potrzeby integracji z modelem COM.  
  
## <a name="duplicate-methods"></a>Metody duplikowania  
 Nie należy definiować zduplikowanych metod. Oznacza to, że nie należy wywoływać `DefineMethod` zduplikowanego zestawu wartości w `td` `wzName` `pvSig` parametrach, i. (Te trzy parametry jednoznacznie definiują metodę). Można jednak użyć duplikatu trzykrotnie, pod warunkiem, że dla jednej z definicji metody ustawia się `mdPrivateScope` bit w `dwMethodFlags` parametrze. ( `mdPrivateScope` Bit oznacza, że kompilator nie emituje odwołania do tej definicji metody).  
  
## <a name="method-implementation-information"></a>Informacje o implementacji metody  
 Informacje o implementacji metody często nie są znane w momencie zadeklarowania metody. W związku z tym nie trzeba przekazywać wartości w `ulCodeRVA` `dwImplFlags` parametrach i podczas wywoływania `DefineMethod` . Wartości można dostarczyć później za pomocą [IMetaDataEmit:: SetMethodImplFlags —](imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit:: SetRVA —](imetadataemit-setrva-method.md), zgodnie z potrzebami.  
  
 W niektórych sytuacjach, takich jak scenariusze wywołania platformy (PInvoke) lub współdziałanie z modelem COM, treść metody nie zostanie podana i `ulCodeRVA` powinna być ustawiona na wartość zero. W takich sytuacjach metoda nie powinna być oznaczona jako abstrakcyjna, ponieważ środowisko uruchomieniowe odnajdzie implementację.  
  
## <a name="defining-a-method-for-pinvoke"></a>Definiowanie metody dla funkcji PInvoke  
 Dla każdej funkcji niezarządzanej, która ma być wywoływana za pomocą funkcji PInvoke, należy zdefiniować metodę zarządzaną, która reprezentuje docelową funkcję niezarządzaną. Aby zdefiniować zarządzaną metodę, użyj z niektórymi `DefineMethod` parametrami ustawionymi na określone wartości, w zależności od sposobu użycia funkcji PInvoke:  
  
- True PInvoke-obejmuje wywołanie zewnętrznej metody niezarządzanej, która znajduje się w niezarządzanej bibliotece DLL.  
  
- Lokalny element PInvoke-obejmuje wywołanie natywnej metody niezarządzanej osadzonej w bieżącym module zarządzanym.  
  
 Ustawienia parametrów są podano w poniższej tabeli.  
  
|Parametr|Wartości dla prawdy|Wartości dla lokalnego elementu PInvoke|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ustaw `mdStatic` ; Wyczyść `mdSynchronized` i `mdAbstract` .|  
|`pvSigBlob`|Prawidłowy podpis metody środowiska uruchomieniowego języka wspólnego (CLR) z parametrami, które są prawidłowymi typami zarządzanymi.|Prawidłowy podpis metody CLR z parametrami, które są prawidłowymi typami zarządzanymi.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ustaw `miCil` i `miManaged` .|Ustaw `miNative` i `miUnmanaged` .|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
