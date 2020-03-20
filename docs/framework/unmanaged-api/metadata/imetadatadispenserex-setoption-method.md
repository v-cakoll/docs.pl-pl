---
title: IMetaDataDispenserEx::SetOption — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175905"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption — Metoda
Ustawia określoną opcję na daną wartość dla bieżącego zakresu metadanych. Opcja określa sposób obsługi wywołań bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [w] Wskaźnik do identyfikatora GUID, który określa opcję, która ma zostać ustawiona.  
  
 `pValue`  
 [w] Wartość, której można użyć do skonfigurowania opcji. Typ tej wartości musi być wariantem typu określonej opcji.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono `optionId` dostępne identyfikatory GUID, które `pValue` parametr może wskazywać, oraz odpowiadające im prawidłowe wartości parametru.  
  
|Identyfikator GUID|Opis|`pValue`Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Określa, które elementy są sprawdzane pod kątem duplikatów. Za każdym razem, gdy wywołujesz metodę [IMetaDataEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) która tworzy nowy element, można poprosić o metodę, aby sprawdzić, czy element już istnieje w bieżącym zakresie. Na przykład można sprawdzić istnienie `mdMethodDef` elementów; w takim przypadku po wywołaniu [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), sprawdzi, czy metoda nie istnieje jeszcze w bieżącym zakresie. Ten czek używa klucza, który jednoznacznie identyfikuje daną metodę: typ nadrzędny, nazwę i podpis.|Musi być wariant typu UI4 i musi zawierać kombinację wartości [CorCheckDuplicatesFor wyliczenia.](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)|  
|MetaDataRefToDefCheck|Formanty, do których odwołują się elementy są konwertowane na definicje. Domyślnie aparat metadanych zoptymalizuje kod, konwertując element, do którego istnieje odwołanie, na jego definicję, jeśli element, do którego istnieje odwołanie, jest faktycznie zdefiniowany w bieżącym zakresie.|Musi być wariant typu UI4 i musi zawierać kombinację wartości wyliczenia [CorRefToDefCheck.](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)|  
|MetaDataNotificationForTokenMovement|Określa, które ponowne mapy tokenu występujące podczas scalania metadanych generują wywołania zwrotne. Użyj [metody IMetaDataEmit::SetHandler,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) aby ustanowić interfejs [IMapToken.](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)|Musi być wariant typu UI4 i musi zawierać kombinację wartości wyliczenia [CorNotificationForTokenMovement.](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)|  
|MetaDataSetENC|Steruje zachowaniem edycji i kontynuowania (ENC). W pewnym momencie można ustawić tylko jeden tryb zachowania.|Musi być wariantem typu UI4 i musi zawierać wartość wyliczenia [CorSetENC.](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) Wartość nie jest maską bitową.|  
|MetaDataErrorIfEmitOutOfOrder|Formanty, które emitują błędy poza kolejnością, generują wywołania zwrotne. Emitowanie metadanych poza kolejnością nie jest śmiertelne; Jednak jeśli emitujesz metadane w kolejności preferowanej przez aparat metadanych, metadane są bardziej kompaktowe i dlatego mogą być bardziej efektywnie przeszukiwane. Użyj `IMetaDataEmit::SetHandler` tej metody, aby ustanowić interfejs [IMetaDataError.](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)|Musi być wariant typu UI4 i musi zawierać kombinację wartości [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) wyliczenia.|  
|MetaDataImportOption|Określa, które rodzaje elementów, które zostały usunięte podczas ENC są pobierane przez wyliczacza.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości [wyliczania wyliczenia CorImportOptions.](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)|  
|MetaDataThreadSafetyOptions|Określa, czy aparat metadanych uzyskuje blokady czytnika/modułu zapisującego, zapewniając w ten sposób bezpieczeństwo wątków. Domyślnie aparat zakłada, że dostęp jest jednowątkowy przez wywołującego, więc nie blokady są uzyskiwane. Klienci są odpowiedzialni za utrzymanie prawidłowej synchronizacji wątków podczas korzystania z interfejsu API metadanych.|Musi być wariant typu UI4 i musi zawierać wartość [wyliczenia CorThreadSafetyOptions.](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) Wartość nie jest maską bitową.|  
|MetaDataGenerateTCEAdapters|Określa, czy importer biblioteki typów powinien generować szczelnie sprzężona karta zdarzeń (TCE) dla kontenerów przyłącza COM.|Musi być wariantem typu BOOL. Jeśli `pValue` jest `true`ustawiona na , importer biblioteki typów generuje karty TCE.|  
|MetaDataTypeLibImportNamespace|Określa nieobezwłasną przestrzeń nazw dla importowanej biblioteki typów.|Musi być wartością null lub wariantem typu BSTR. Jeśli `pValue` jest wartością null, bieżący obszar nazw jest ustawiony na wartość null; w przeciwnym razie bieżąca przestrzeń nazw jest ustawiona na ciąg, który jest utrzymywany w typie BSTR wariantu.|  
|MetaDataLinkerOptions|Określa, czy konsolidator powinien generować zestaw lub plik modułu .NET Framework.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości [wyliczenia CorLinkerOptions.](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)|  
|MetaDataRuntimeVersion|Określa wersję środowiska wykonawczego języka wspólnego, dla którego ten obraz został zbudowany. Wersja jest przechowywana jako ciąg, taki jak "v1.0.3705".|Musi być wartością null, VT_EMPTY lub wariantem typu BSTR. Jeśli `pValue` ma wartość null, wersja środowiska uruchomieniowego jest ustawiona na wartość null. Jeśli `pValue` jest VT_EMPTY, wersja jest ustawiona na wartość domyślną, która jest pobierana z wersji Mscorwks.dll, w którym jest uruchomiony kod metadanych. W przeciwnym razie wersja środowiska wykonawczego jest ustawiona na ciąg, który jest utrzymywany w typie BSTR wariantu.|  
|MetaDataMergerOptions|Określa opcje scalania metadanych.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości `MergeFlags` wyliczenia, które jest opisane w pliku CorHdr.h.|  
|MetaDataPreserveLocalRefs|Wyłącza optymalizację odwołań lokalnych do definicji.|Musi zawierać kombinację wartości [wyliczenia CorLocalRefPreservation.](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
