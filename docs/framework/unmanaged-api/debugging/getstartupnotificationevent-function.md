---
title: GetStartupNotificationEvent — Funkcja
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67f3ef57b4996eb4a956c596b76fb94b1bdfd7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738890"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent — Funkcja
Tworzy lub zostanie otwarte dojście zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie docelowym określonym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [in] Proces identyfikator procesu docelowego, z którego będą otrzymywać powiadomienia o uruchamiania środowiska CLR.  
  
 `phStartupEvent`  
 [out] Wskaźnik do uchwytu, który zostanie zasygnalizowane przez CLR podczas uruchamiania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie uzyskano dojścia do uruchamiania zdarzenie powiadomienia.  
  
 E_INVALIDARG  
 `phStartupEvent` ma wartość null lub `debuggeePID` nie odwołuje się do procesu, który jest obecnie uruchomiona.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można uzyskać dojścia do uruchamiania zdarzenie powiadomienia.  
  
## <a name="remarks"></a>Uwagi  
 W systemie operacyjnym Windows `debuggeePID` mapuje do systemu operacyjnego przetworzyć identyfikatora.  
  
 Zdarzenie jest sygnalizowane przed każdą zarządzane, że kod jest wykonywany przez środowisko CLR, która jest sygnalizowane zdarzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
