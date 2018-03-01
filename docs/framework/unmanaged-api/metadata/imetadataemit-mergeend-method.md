---
title: "IMetaDataEmit::MergeEnd — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd — Metoda
Scalenia do bieżącego zakresu zakresy metadanych określonych przez jeden lub więcej poprzedniego wywołania [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura wyzwala rzeczywiste scalania metadanych, wszystkich import określono poprzedzając wywołań zakresów `IMetaDataEmit::Merge`, w bieżącym zakresie danych wyjściowych.  
  
 Do scalania mają zastosowanie następujące warunki specjalne:  
  
-   Identyfikator wersji modułu (identyfikatora MVID) nigdy nie zostaną zaimportowane, ponieważ jest unikatowa w zakresie importu metadanych.  
  
-   Żadne istniejące właściwości modułu całej zostaną zastąpione.  
  
     Jeśli moduł właściwości zostały już skonfigurowane dla bieżącego zakresu, Brak właściwości modułu zostaną zaimportowane. Jednak jeśli nie ustawiono właściwości modułu w bieżącym zakresie, są one importowane tylko raz, gdy są najpierw napotkano. Jeśli te właściwości modułu wystąpi ponownie, znajdują się duplikaty. Jeśli znajdują się duplikaty nie są porównywane wartości wszystkich właściwości modułu (z wyjątkiem identyfikatora MVID), występuje błąd.  
  
-   Dla definicji typów (`TypeDef`), bez duplikatów są scalane w bieżącym zakresie. `TypeDef`obiekty są sprawdzane pod kątem duplikatów dla każdego *obiektu w pełni kwalifikowaną nazwę* + *GUID* + *numer wersji*. Jeśli są zgodne na nazwę lub identyfikator GUID i inne elementy są różne, występuje błąd. W przeciwnym razie, jeśli wszystkie trzy elementy są zgodne, `MergeEnd` sprawdza pobieżną zapewnienie wpisy są rzeczywiście duplikaty; Jeśli nie, występuje błąd. Szuka tego pobieżnego:  
  
    -   Tego samego elementu członkowskiego deklaracjami występujących w tej samej kolejności. Elementy członkowskie, które są oznaczone jako `mdPrivateScope` (zobacz [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie) nie są uwzględnione w tym wyboru; są one scalane specjalnie.  
  
    -   Ten sam układ klasy.  
  
     Oznacza to, że `TypeDef` obiektu musi zawsze być w pełni i stale zdefiniowana w co zakres metadanych w którym zadeklarowany jest; jeśli jego implementacje elementów członkowskich (dla klasy) są rozkładane w wielu jednostkach kompilacji, pełnej definicji zakłada się, że w każdym zakresem i nie przyrostowe do każdego zakresu. Na przykład jeśli nazwy parametrów mają zastosowanie do Umowy, ich musi być wydane tak samo do każdego zakresu; Jeśli nie są istotne, nie powinny one wydane do metadanych.  
  
     Wyjątkiem jest to, że `TypeDef` obiekt może mieć przyrostowe elementy członkowskie oznaczone jako `mdPrivateScope`. Po wystąpieniu, `MergeEnd` przyrostowo dodaje je do bieżącego zakresu bez względu na duplikaty. Ponieważ kompilator rozumie zakres prywatny, kompilator musi być odpowiedzialny za egzekwowanie zasad.  
  
-   Względne wirtualnych adresów (RVAs) nie są importowane lub scalić; kompilator powinien ponownie wyemitować tych informacji.  
  
-   Atrybuty niestandardowe są scalane, tylko wtedy, gdy scalonego elementu, do której są dołączone. Na przykład niestandardowe atrybuty powiązane z klasą są łączone przy pierwszym napotkaniu klasy. Jeśli atrybutów niestandardowych, które są skojarzone z `TypeDef` lub `MemberDef` która jest specyficzna dla jednostki kompilacji (na przykład sygnaturę czasową kompilacji elementu członkowskiego), nie są one scalane i zależy od kompilator, aby usunąć lub zaktualizować takich metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
