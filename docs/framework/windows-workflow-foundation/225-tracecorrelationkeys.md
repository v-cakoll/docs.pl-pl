---
title: 225 — TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755665"
---
# <a name="225---tracecorrelationkeys"></a>225 — TraceCorrelationKeys
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|225|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane stosowania korelacji na podstawie zawartości dla usługi przepływu pracy. Zawiera on klucze korelacji, które są stosowane do korelowanie komunikatów na wystąpienie.  
  
## <a name="message"></a>Komunikat  
 Obliczona klucz korelacji "%1" przy użyciu wartości "%2" w zakresie nadrzędnym "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Klucz wystąpienia|`xs:GUID`|Klucz, który został wygenerowany z wartości korelacji.|  
|Wartości|`xs:string`|Wartości, które były używane do obliczania klucza wystąpienia korelacji.|  
|Zakresu nadrzędnego|`xs:string`||  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
