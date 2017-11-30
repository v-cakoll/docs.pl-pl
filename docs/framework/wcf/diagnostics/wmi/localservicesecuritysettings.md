---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74eff3a6193e6507c1049accf4c43c3ecc8d30a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Składnia  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa LocalServiceSecuritySettings nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa LocalServiceSecuritySettings ma następujące właściwości:  
  
### <a name="detectreplays"></a>DetectReplays  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie.  
  
### <a name="inactivitytimeout"></a>Limit czasu nieaktywności  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących sesji bezpieczeństwa obsługiwanych przez usługę.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający okres istnienia wystawionego dla wszystkich nowych plików cookie zabezpieczeń.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba plików cookie, które mogą być buforowane.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących połączeń przypadających na usługę.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba negocjacji zabezpieczeń, które mogą być jednocześnie aktywne.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający maksymalny czas trwania fazy negocjacji zabezpieczeń między serwerem a klientem.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy połączenia używające obsługi wiadomości WS-Reliable podjąć próbę ponownego połączenia po błędach transportu.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.  
  
### <a name="replaywindow"></a>Elementy ReplayWindow  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający okres czasu, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający okres czasu, po upływie którego inicjator odnawia klucz sesji zabezpieczeń.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający okres poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt TimeSpan określający okres ważności sygnatury czasowej.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
