---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115040"
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
  
 Typ dostępu: tylko do odczytu  
  
 W przypadku wartości true automatycznie zamknięciem sesji usługi powoduje zamknięcie sesji dupleksowej.  
  
### <a name="concurrencymode"></a>Właściwość ConcurrencyMode  
 Typ danych: ciąg  
Typ dostępu: tylko do odczytu  
  
 Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która określa, czy wysyłać dane serializacji nieznany podczas transmisji.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy umożliwia wybieranie wątkiem wykonywania w bieżącym kontekście synchronizacji.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
