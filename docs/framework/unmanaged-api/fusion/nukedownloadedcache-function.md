---
title: NukeDownloadedCache — Funkcja
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796307"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache — Funkcja
Usuwa pamięć podręczną pobierania środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w WinError. h.  
  
## <a name="remarks"></a>Uwagi  
 Pamięć podręczna pobierania środowiska CLR to obszar, w którym zestawy o silnych nazwach pobrane z adresu URL są przechowywane do ponownego użycia.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **Biblioteki** Fusion. dll i mscorwks. dll. Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CreateHistoryReader, funkcja](createhistoryreader-function.md)
- [GetHistoryFileDirectory, funkcja](gethistoryfiledirectory-function.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
