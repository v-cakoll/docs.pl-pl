---
title: "IMetaDataDispenserEx::SetOption — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.SetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a58ac4379522c13125f98df058cd67bceb7cdbd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption — Metoda
Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych. Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Wskaźnik identyfikator GUID, który określa opcje do ustawienia.  
  
 `pValue`  
 [in] Wartość do użycia, aby ustawić opcję. Typ tej wartości musi być określona opcja typu Wariant.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono dostępne identyfikatory GUID który `optionId` może wskazywać parametru i prawidłowe wartości odpowiednich dla `pValue` parametru.  
  
|Identyfikator GUID|Opis|`pValue`Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Określa elementy, które są sprawdzane pod kątem duplikatów. Zawsze należy wywołać [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) metodę, która tworzy nowy element, możesz poprosić metodę, aby sprawdzić, czy element już istnieje w bieżącym zakresie. Na przykład można sprawdzić obecność `mdMethodDef` elementy; w takim przypadku, gdy jest wywoływana [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), sprawdzi, czy metoda nie istnieje już w bieżącym zakresie. To sprawdzenie korzysta z klucza, który unikatowo identyfikuje danej metody: nadrzędnego typu, nazwy i podpisu.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) wyliczenia.|  
|MetaDataRefToDefCheck|Formanty, które odwołuje się do elementów są konwertowane na definicje. Domyślnie aparat metadanych będzie optymalizacji kodu za pomocą konwersji elementu z odwołaniem do jego definicji, jeśli przywoływany element faktycznie jest zdefiniowana w bieżącym zakresie.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) wyliczenia.|  
|MetaDataNotificationForTokenMovement|Formanty ponownie token, który mapuje występujących podczas scalania metadanych Generowanie wywołań zwrotnych. Użyj [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metodę ustanawiania Twojej [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interfejsu.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) wyliczenia.|  
|MetaDataSetENC|Steruje zachowaniem edit-and-continue (ENC). Można ustawić tylko jeden tryb zachowania w czasie.|Musi być typ variant typu UI4 i musi zawierać wartość [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) wyliczenia. Wartość nie jest maską bitów.|  
|MetaDataErrorIfEmitOutOfOrder|Formanty, które błędy emitowany poza kolejnością Generowanie wywołań zwrotnych. Emitowanie poza kolejnością metadanych nie jest krytyczny; Jednak jeśli Emituj metadanych w kolejności, która jest ich drużyna jest faworytem przez aparat metadanych, metadanych jest mniejszych i w związku z tym można efektywniej przeszukiwać. Użyj `IMetaDataEmit::SetHandler` metodę ustanawiania Twojej [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) interfejsu.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) wyliczenia.|  
|MetaDataImportOption|Określa, jakie rodzaje elementów, które zostały usunięte podczas ENC są pobierane przez moduł wyliczający.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorImportOptions — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) wyliczenia.|  
|MetaDataThreadSafetyOptions|Określa, czy aparat metadanych uzyskuje odczytywania/zapisywania blokad, zapewniając bezpieczeństwo wątków. Domyślnie aparat zakłada, że dostęp jednowątkowe przez obiekt wywołujący, więc nie blokuje są uzyskiwane. Klienci są zobowiązani do utrzymywania synchronizacji odpowiednich wątku przy użyciu metadanych interfejsu API.|Musi być typ variant typu UI4 i musi zawierać wartość [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) wyliczenia. Wartość nie jest maską bitów.|  
|MetaDataGenerateTCEAdapters|Określa, czy importer biblioteki typów powinien wygenerować kart silnie sprzężonego zdarzenia (tce programu) dla kontenerów punktu połączenia COM.|Musi być typ variant typu wartość logiczna. Jeśli `pValue` ma ustawioną wartość `true`, kart tce programu generuje importer biblioteki typów.|  
|MetaDataTypeLibImportNamespace|Określa przestrzeń nazw z systemem innym niż domyślny dla biblioteki typów, który jest importowany.|Musi być wartością null lub wariant typu BSTR. Jeśli `pValue` jest wartością null bieżącej przestrzeni nazw jest ustawiona na wartość null; w przeciwnym razie, bieżącej przestrzeni nazw jest ustawiona na ciąg, który jest przechowywany w typ BSTR variant.|  
|MetaDataLinkerOptions|Określa, czy konsolidator powinien wygenerować zestawu lub pliku modułu .NET Framework.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) wyliczenia.|  
|MetaDataRuntimeVersion|Określa wersję środowiska CLR, względem którego został skompilowany ten obraz. Wersja jest przechowywana jako ciąg znaków, takich jak "v1.0.3705".|Musi to być wartość null, wartość VT_EMPTY lub wariant typu BSTR. Jeśli `pValue` jest wersja środowiska uruchomieniowego null, jest ustawiony na wartość null. Jeśli `pValue` jest VT_EMPTY, wersja jest ustawiana wartość domyślna, która jest przenoszony z wersji Mscorwks.dll.a;a;pierwsza, w którym wykonywany jest kod metadanych. W przeciwnym razie wersja środowiska uruchomieniowego jest ustawiona na ciąg, który jest przechowywany w typ BSTR variant.|  
|MetaDataMergerOptions|Określa opcje scalania metadanych.|Musi być typ variant typu UI4 i musi zawierać kombinację wartości `MergeFlags` wyliczenia, który jest opisany w pliku CorHdr.h.|  
|MetaDataPreserveLocalRefs|Wyłącza optymalizacji lokalnego odwołania do definicji.|Musi zawierać kombinację wartości [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) wyliczenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenserEx — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
