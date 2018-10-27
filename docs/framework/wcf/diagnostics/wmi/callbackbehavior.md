---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 38a38a71db2927d187ccdd93e5e364b0d4955373
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452615"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa CallbackBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa CallbackBehavior ma następujące właściwości:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 W przypadku wartości true automatycznie zamknięciem sesji usługi powoduje zamknięcie sesji dupleksowej.  
  
### <a name="concurrencymode"></a>Właściwość ConcurrencyMode  
 Typ danych: ciąg  
Dostęp do typu: tylko do odczytu  
  
 Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która określa, czy wysyłać dane serializacji nieznany podczas transmisji.  
  
### <a name="includeexceptiondetailinfaults"></a>Parametr IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy umożliwia wybieranie wątkiem wykonywania w bieżącym kontekście synchronizacji.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
