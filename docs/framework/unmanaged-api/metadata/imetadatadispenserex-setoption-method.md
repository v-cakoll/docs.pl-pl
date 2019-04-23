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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9869efee18549c3d0c8b9ee9ca27cf31c1ccf452
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197116"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption — Metoda
Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych. Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Wskaźnik do identyfikator GUID, który określa opcje do skonfigurowania.  
  
 `pValue`  
 [in] Wartość do użycia, aby ustawić opcję. Typ tej wartości musi być typ variant określoną opcję typu.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa tabela zawiera listę dostępnych identyfikatorów GUID, `optionId` może wskazywać parametru i odpowiadające im wartości prawidłowe dla `pValue` parametru.  
  
|Identyfikator GUID|Opis|`pValue` Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Określa, które elementy są zaznaczone dla duplikatów. Zawsze należy wywołać [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) metody, która tworzy nowy element, możesz poprosić metody, aby sprawdzić, czy element już istnieje w bieżącym zakresie. Na przykład, można sprawdzić, czy istnieje `mdMethodDef` elementów; w takim przypadku, gdy zostanie wywołana [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), sprawdzi, że metoda istnieje już w bieżącym zakresie. To sprawdzenie używa klucza, który unikatowo identyfikuje danej metody: element nadrzędny typ, nazwa i podpis.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [corcheckduplicatesfor —](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) wyliczenia.|  
|MetaDataRefToDefCheck|Formanty, które są przywoływane elementy są konwertowane na definicje. Domyślnie aparat metadanych zoptymalizuje kodu za pomocą konwersji odwołania elementu do jego definicji, jeśli przywoływany element faktycznie jest zdefiniowany w bieżącym zakresie.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [correftodefcheck —](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) wyliczenia.|  
|MetaDataNotificationForTokenMovement|Formanty, które token ponownie mapuje występujące podczas scalania metadanych generować wywołania zwrotne. Użyj [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metodę ustanawiania swoje [imaptoken —](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interfejsu.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [cornotificationfortokenmovement —](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) wyliczenia.|  
|MetaDataSetENC|Steruje zachowaniem edit-and-continue (ENC). Można ustawić tylko jeden tryb zachowania w czasie.|Musi mieć wariant typu UI4 i musi zawierać wartość [corsetenc —](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) wyliczenia. Wartość nie jest maską bitów.|  
|MetaDataErrorIfEmitOutOfOrder|Formanty, które błędy emitowane —-kolejnością Generowanie wywołań zwrotnych. Emitowanie metadanych poza kolejnością jest krytyczny; Jeśli jednak użytkownik emitować metadane w kolejności jest faworytem przez aparat metadanych, metadanych jest bardziej zwarty i w związku z tym można efektywniej przeszukiwane. Użyj `IMetaDataEmit::SetHandler` metodę ustanawiania swoje [imetadataerror —](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) interfejsu.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [corerrorifemitoutoforder —](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) wyliczenia.|  
|MetaDataImportOption|Określa, jakie rodzaje elementów, które zostały usunięte podczas ENC są pobierane przez moduł wyliczający.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [corimportoptions — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) wyliczenia.|  
|MetaDataThreadSafetyOptions|Określa, czy aparat metadanych uzyskuje czytnika/moduł zapisujący blokady, zapewniając bezpieczeństwo wątków. Domyślnie aparat przyjęto założenie, że dostęp jest jednowątkowym przez obiekt wywołujący, dzięki czemu blokady nie są pobierane. Klienci są odpowiedzialne za utrzymywanie synchronizacji wątku, korzystając z interfejsów API metadanych.|Musi mieć wariant typu UI4 i musi zawierać wartość [corthreadsafetyoptions —](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) wyliczenia. Wartość nie jest maską bitów.|  
|MetaDataGenerateTCEAdapters|Określa, czy importer biblioteki typów powinien wygenerować kart ściśle powiązanych zdarzeń (TCE) dla kontenerów punktów połączenia com.|Musi mieć wariant typu wartość logiczna. Jeśli `pValue` ustawiono `true`, importer biblioteki typów generuje kart TCE.|  
|MetaDataTypeLibImportNamespace|Określa obszar nazw innych niż domyślne dla biblioteki typów, który jest importowany.|Musi być wartością null lub wariant typu BSTR. Jeśli `pValue` jest wartością null bieżącej przestrzeni nazw jest ustawiona na wartość null; w przeciwnym razie, bieżąca przestrzeń nazw jest ustawiona na ciąg, który jest przechowywany w typ BSTR variant.|  
|MetaDataLinkerOptions|Określa, czy konsolidator powinien wygenerować zestawu lub pliku modułu .NET Framework.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości [corlinkeroptions —](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) wyliczenia.|  
|MetaDataRuntimeVersion|Określa wersję środowiska CLR, względem którego został skompilowany ten obraz. Wersja jest przechowywana jako ciąg, takie jak wartości "v1.0.3705".|Musi to być wartość null, wartość VT_EMPTY lub wariant typu BSTR. Jeśli `pValue` jest wersja środowiska uruchomieniowego ma wartość null, jest ustawiony na wartość null. Jeśli `pValue` jest VT_EMPTY, wersja jest ustawiana na wartość domyślną, jest rysowana od wersji Mscorwks.dll, w którym wykonywany jest kod metadanych. W przeciwnym razie wersji środowiska uruchomieniowego jest ustawiona na ciąg, który jest przechowywany w typ BSTR variant.|  
|MetaDataMergerOptions|Określa opcje Scalanie metadanych.|Musi mieć wariant typu UI4 i musi zawierać kombinację wartości `MergeFlags` wyliczenia, który jest opisany w pliku sekcję CorHdr.h.|  
|MetaDataPreserveLocalRefs|Wyłącza optymalizację lokalnego odwołania do definicji.|Musi zawierać kombinację wartości [corlocalrefpreservation —](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) wyliczenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
