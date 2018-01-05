---
title: "Usługa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7b631ede7bd011a92003dc5f6083c1c427d990e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service"></a>Usługa
Usługa  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Typ danych: tablicy ciągów  
  
 Dostęp typu: tylko do odczytu  
  
 Adres podstawowy używany przez usługę.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Zachowania skojarzone z tą usługą.  
  
### <a name="configurationname"></a>ConfigurationName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa wystąpienia wystąpienia liczników wydajności usługi.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa usługi pod adresem.  
  
### <a name="extensions"></a>Rozszerzenia  
 Typ danych: tablicy ciągów  
  
 Dostęp typu: tylko do odczytu  
  
 Konteksty wystąpienia dla rozszerzeń wystąpienia tej usługi.  
  
### <a name="metadata"></a>Metadane  
 Typ danych: tablicy ciągów  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia metadanych usługi.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Unikatowa nazwa tej usługi.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Przestrzeń nazw usługi.  
  
### <a name="opened"></a>Otwarte  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Czas otwarcia usługi.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Typ danych: tablica kanału  
  
 Dostęp typu: tylko do odczytu  
  
 Kanały wychodzące z wystąpienia usługi.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator procesu obsługującego usługę.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|
