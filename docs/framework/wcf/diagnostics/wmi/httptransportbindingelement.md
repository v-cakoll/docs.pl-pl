---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 34ad4b8534d082d7f5248d42d70ca5bd0647a5dc
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454320"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa HttpTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa HttpTransportBindingElement ma następujące właściwości:  
  
### <a name="allowcookies"></a>allowCookies  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez odbiornik HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy serwery proxy są ignorowane dla adresów lokalnych.  
  
### <a name="hostnamecomparisonmode"></a>parametru hostNameComparisonMode  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.  
  
### <a name="keepaliveenabled"></a>keepAliveEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Po włączeniu połączeń HTTP pozostają aktywne niezależnie od tego, poziom aktywności.  
  
### <a name="maxbuffersize"></a>wartość maxBufferSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny rozmiar puli bufora.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Identyfikator URI, który zawiera adres serwera proxy do obsługi żądań HTTP.  
  
### <a name="proxyauthenticationscheme"></a>proxyAuthenticationScheme  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez serwer proxy HTTP.  
  
### <a name="realm"></a>obszar  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Obszar uwierzytelniania.  
  
### <a name="transfermode"></a>Tryb transferu  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.  
  
### <a name="unsafeconnectionntlmauthentication"></a>unsafeConnectionNtlmAuthentication  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy włączone jest niebezpieczne udostępnianie połączenia na serwerze.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
