---
title: IAssemblyCacheItem — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796703"
---
# <a name="iassemblycacheitem-interface"></a>IAssemblyCacheItem — Interfejs
Reprezentuje pojedynczy zestaw w globalnej pamięci podręcznej zestawów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AbortItem, metoda](iassemblycacheitem-abortitem-method.md)|Zezwala na zestaw w globalnej pamięci podręcznej zestawów na wykonywanie operacji czyszczenia przed jego wydaniem.|  
|[Commit, metoda](iassemblycacheitem-commit-method.md)|Zatwierdza odwołanie do pamięci podręcznej.|  
|[CreateStream, metoda](iassemblycacheitem-createstream-method.md)|Tworzy strumień o określonej nazwie i formacie.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [Global Assembly Cache](../../app-domains/gac.md)
- [IAssemblyCache, interfejs](iassemblycache-interface.md)
