---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133497"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna, która określa, czy ataki metodą kanał są wykrywane i automatycznie uwzględnione.  
  
### <a name="inactivitytimeout"></a>Limit czasu nieaktywności  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba oczekujących sesji bezpieczeństwa, obsługiwanych przez usługę.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Element TimeSpan określający czas istnienia nadawany wszystkie nowe pliki cookie zabezpieczeń.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba plików cookie, które mogą być buforowane.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Element TimeSpan określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba oczekujących połączeń z usługą.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba negocjacji zabezpieczeń, które mogą być wykonywane jednocześnie.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Element TimeSpan określa maksymalny czas do przeprowadzenia w fazie negocjowanie zabezpieczeń między serwerem a klientem.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy połączenia za pomocą usługi WS-Reliable messaging próbę ponownego połączenia po błędach transportu.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Liczba buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.  
  
### <a name="replaywindow"></a>Elementy ReplayWindow  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Przedział czasu, który określa czas, w której poszczególne komunikatów są poprawni.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Przedział czasu, który określa czas, po upływie którego inicjator odnawia klucz sesji zabezpieczeń.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Przedział czasu, który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w wiadomościach przychodzących podczas odnawiania klucza.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Przedział czasu, który określa czas, w którym sygnatura czasowa jest poprawna.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
