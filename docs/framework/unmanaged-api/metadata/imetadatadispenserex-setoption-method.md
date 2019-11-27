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
ms.openlocfilehash: bc30f9fb120db92ccfc1e7dd0560b3fe18c54b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432731"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption — Metoda
Ustawia określoną opcję na daną wartość dla bieżącego zakresu metadanych. Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 podczas Wskaźnik do identyfikatora GUID, który określa opcję, która ma zostać ustawiona.  
  
 `pValue`  
 podczas Wartość, która ma zostać użyta do ustawienia opcji. Typ tej wartości musi być wariantem typu określonej opcji.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa tabela zawiera listę dostępnych identyfikatorów GUID, do których może wskazywać parametr `optionId` i odpowiednie prawidłowe wartości parametru `pValue`.  
  
|Identyfikator GUID|Opis|`pValue` parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Kontroluje, które elementy są sprawdzane pod kątem duplikatów. Za każdym razem, gdy wywoływana jest metoda [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) , która tworzy nowy element, można polecić metodę, aby sprawdzić, czy element już istnieje w bieżącym zakresie. Można na przykład sprawdzić obecność elementów `mdMethodDef`; w tym przypadku, gdy wywołasz [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), sprawdzimy, czy metoda jeszcze nie istnieje w bieżącym zakresie. Ten test korzysta z klucza, który jednoznacznie identyfikuje daną metodę: Parent Type, Name i Signature.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorCheckDuplicatesFor —](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) .|  
|MetaDataRefToDefCheck|Kontroluje, które elementy, do których istnieją odwołania, są konwertowane na definicje. Domyślnie aparat metadanych optymalizuje kod przez przekonwertowanie elementu, do którego się odwołuje, jeśli element, do którego się odwoływano, jest zdefiniowany w bieżącym zakresie.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorRefToDefCheck —](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) .|  
|MetaDataNotificationForTokenMovement|Określa, które ponowne mapowania tokenu występują podczas scalania metadanych generują wywołania zwrotne. Użyj metody [IMetaDataEmit:: SetHandle](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) , aby nawiązać Interfejs [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) .|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorNotificationForTokenMovement —](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) .|  
|MetaDataSetENC|Steruje zachowaniem funkcji Edit-and-Continue (ENC). Można ustawić tylko jeden tryb zachowania w danym momencie.|Musi być VARIANT typu UI4 i musi zawierać wartość wyliczenia [CorSetENC —](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) . Wartość nie jest maską bitów.|  
|MetaDataErrorIfEmitOutOfOrder|Kontroluje, które emitowane błędy generują wywołania zwrotne. Emitowanie metadanych poza kolejnością nie jest krytyczne; Jednak w przypadku emisji metadanych w kolejności, w której jest preferowany aparat metadanych, metadane są bardziej kompaktowe i dlatego mogą być bardziej efektywnie przeszukiwane. Użyj metody `IMetaDataEmit::SetHandler`, aby nawiązać Interfejs [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) .|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorErrorIfEmitOutOfOrder —](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) .|  
|MetaDataImportOption|Kontroluje typy elementów, które zostały usunięte podczas ENC, są pobierane przez moduł wyliczający.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorImportOptions — Enumeration](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) .|  
|MetaDataThreadSafetyOptions|Określa, czy aparat metadanych uzyskuje blokady czytnika/składnika zapisywania, zapewniając w ten sposób bezpieczeństwo wątków. Domyślnie silnik zakłada, że dostęp jest jednowątkowy przez obiekt wywołujący, więc nie są pobierane żadne blokady. Klienci są odpowiedzialni za zachowanie poprawnej synchronizacji wątków podczas korzystania z interfejsu API metadanych.|Musi być VARIANT typu UI4 i musi zawierać wartość wyliczenia [CorThreadSafetyOptions —](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) . Wartość nie jest maską bitów.|  
|MetaDataGenerateTCEAdapters|Określa, czy importer biblioteki typów powinien generować karty z ściśle połączonymi zdarzeniami (TCE) dla kontenerów punktów połączenia COM.|Musi być wariantem typu BOOL. Jeśli `pValue` jest ustawiona na `true`, importer biblioteki typów generuje karty TCE.|  
|MetaDataTypeLibImportNamespace|Określa niedomyślną przestrzeń nazw dla importowanej biblioteki typów.|Musi mieć wartość null lub być wariantem typu BSTR. Jeśli `pValue` jest wartością null, bieżąca przestrzeń nazw jest ustawiona na wartość null; w przeciwnym razie bieżąca przestrzeń nazw jest ustawiana na ciąg, który jest przechowywany w typie BSTR wariantu.|  
|MetaDataLinkerOptions|Określa, czy konsolidator powinien generować zestaw lub .NET Framework plik modułu.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia [CorLinkerOptions —](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) .|  
|MetaDataRuntimeVersion|Określa wersję środowiska uruchomieniowego języka wspólnego, dla którego został skompilowany obraz. Wersja jest przechowywana jako ciąg, na przykład "v 1.0.3705".|Musi być wartością null, wartością VT_EMPTY lub wariantem typu BSTR. Jeśli `pValue` ma wartość null, wersja środowiska uruchomieniowego jest ustawiona na wartość null. Jeśli `pValue` jest VT_EMPTY, wersja jest ustawiona na wartość domyślną, która jest rysowana z wersji mscorwks. dll, w której jest uruchomiony kod metadanych. W przeciwnym razie wersja środowiska uruchomieniowego jest ustawiona na ciąg, który jest przechowywany w typie BSTR wariantu.|  
|MetaDataMergerOptions|Określa opcje scalania metadanych.|Musi być wariantem typu UI4 i musi zawierać kombinację wartości wyliczenia `MergeFlags`, która jest opisana w pliku CorHdr. h.|  
|MetaDataPreserveLocalRefs|Wyłącza Optymalizowanie lokalnych odwołań do definicji.|Musi zawierać kombinację wartości wyliczenia [CorLocalRefPreservation —](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) .|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
