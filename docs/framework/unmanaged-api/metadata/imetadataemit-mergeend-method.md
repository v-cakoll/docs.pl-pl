---
title: IMetaDataEmit::MergeEnd — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448028"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd — Metoda

Scala do bieżącego zakresu wszystkich zakresów metadanych określonych przez jedno lub więcej wcześniejszych wywołań do [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>Składnia

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parametry

Ta metoda nie przyjmuje żadnych parametrów.

## <a name="remarks"></a>Uwagi

Ta procedura wyzwala rzeczywiste scalanie metadanych wszystkich zakresów importu określonych przez poprzednie wywołania do `IMetaDataEmit::Merge`, do bieżącego zakresu wyjściowego.

Następujące specjalne warunki dotyczą scalania:

- Identyfikator wersji modułu (MVID) nigdy nie jest importowany, ponieważ jest unikatowy dla metadanych w zakresie importu.

- Żadne istniejące właściwości całego modułu nie są zastępowane.

  Jeśli właściwości modułu zostały już ustawione dla bieżącego zakresu, nie zaimportowano żadnych właściwości modułu. Jeśli jednak właściwości modułu nie zostały ustawione w bieżącym zakresie, są one importowane tylko raz podczas pierwszego napotkania. Jeśli te właściwości modułu zostaną ponownie wykryte, są one duplikatami. Jeśli wartości wszystkich właściwości modułu (z wyjątkiem MVID) są porównywane i nie znaleziono duplikatów, zostanie zgłoszony błąd.

- W przypadku definicji typu (`TypeDef`) żadne duplikaty nie są scalane z bieżącym zakresem. obiekty `TypeDef` są sprawdzane pod kątem duplikatów dla każdej w *pełni kwalifikowanej nazwy obiektu* + *Identyfikator GUID* + *numer wersji*. Jeśli istnieje dopasowanie dla nazwy lub identyfikatora GUID, a którykolwiek z pozostałych dwóch elementów jest inny, zostanie zgłoszony błąd. W przeciwnym razie, jeśli wszystkie trzy elementy są zgodne, `MergeEnd` sprawdza kursor, aby upewnić się, że wpisy są rzeczywiście duplikatami; Jeśli nie, zostanie zgłoszony błąd. Sprawdzanie kursorów szuka:

  - Te same deklaracje elementu członkowskiego, występujące w tej samej kolejności. Elementy członkowskie, które są oflagowane jako `mdPrivateScope` (zobacz Wyliczenie [CorMethodAttr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) ) nie są uwzględnione w tym sprawdzaniu; są one scalane specjalnie.

  - Ten sam układ klasy.

  Oznacza to, że obiekt `TypeDef` musi być zawsze całkowicie i spójnie zdefiniowany w każdym zakresie metadanych, w którym jest zadeklarowany; Jeśli jego implementacje składowe (dla klasy) są rozłożone w wielu jednostkach kompilacji, przyjmuje się, że w każdym zakresie jest obecna pełna definicja, a nie przyrostowa do każdego zakresu. Na przykład jeśli nazwy parametrów są odpowiednie dla kontraktu, muszą one być emitowane w taki sam sposób do każdego zakresu; Jeśli nie są istotne, nie powinny być emitowane do metadanych.

  Wyjątek polega na tym, że obiekt `TypeDef` może mieć przyrostowe składowe oflagowane jako `mdPrivateScope`. Po napotkaniu tych `MergeEnd` przyrostowo dodaje je do bieżącego zakresu bez względu na duplikaty. Ponieważ kompilator rozumie zakres prywatny, kompilator musi być odpowiedzialny za Wymuszanie reguł.

- Względne adresy wirtualne (RVA) nie są importowane ani scalone; Kompilator powinien reemitować te informacje.

- Atrybuty niestandardowe są scalane tylko wtedy, gdy element, do którego są dołączone, zostanie scalony. Na przykład atrybuty niestandardowe skojarzone z klasą są scalane podczas pierwszego napotkania klasy. Jeśli atrybuty niestandardowe są skojarzone z `TypeDef` lub `MemberDef`, które są specyficzne dla jednostki kompilacji (na przykład sygnatury czasowej kompilowania elementu członkowskiego), nie są scalane i są do kompilatora, aby usunąć lub zaktualizować takie metadane.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** Cor. h

**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll

**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
