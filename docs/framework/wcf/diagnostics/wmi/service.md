---
title: Usługa
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991448"
---
# <a name="service"></a>Usługa
Usługa  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa usługi nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa usługi ma następujące właściwości:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Typ danych: tablica ciągów  
  
 Typ dostępu: tylko do odczytu  
  
 Adres podstawowy używany przez usługę.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: Zachowanie tablicy  
  
 Typ dostępu: tylko do odczytu  
  
 Zachowania skojarzone z tą usługą.  
  
### <a name="configurationname"></a>ConfigurationName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa wystąpienia wystąpienia liczników wydajności usługi.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa usługi pod adresem.  
  
### <a name="extensions"></a>Rozszerzenia  
 Typ danych: tablica ciągów  
  
 Typ dostępu: tylko do odczytu  
  
 Konteksty wystąpień dla rozszerzeń wystąpienie usługi.  
  
### <a name="metadata"></a>Metadane  
 Typ danych: tablica ciągów  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia metadanych usługi.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Unikatowa nazwa tej usługi.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Przestrzeń nazw usługi.  
  
### <a name="opened"></a>Otwarte  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Czas otwarcia usługi.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Typ danych: Tablica kanału  
  
 Typ dostępu: tylko do odczytu  
  
 Kanały wychodzące z wystąpienia usługi.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator procesu procesu, który hostuje usługę.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
