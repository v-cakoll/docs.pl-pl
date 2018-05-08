---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 1975fd2e04a5c9cdb68bc838802abafbd781b7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.  
  
### <a name="authenticationscheme"></a>authenticationScheme  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy serwery proxy są ignorowane w przypadku adresów lokalnych.  
  
### <a name="hostnamecomparisonmode"></a>parametru hostNameComparisonMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Po włączeniu połączenia HTTP są utrzymywane bez względu na poziom aktywności.  
  
### <a name="maxbuffersize"></a>wartość maxBufferSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar puli buforów.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator URI zawierający adres serwera proxy do obsługi żądań HTTP.  
  
### <a name="proxyauthenticationscheme"></a>proxyAuthenticationScheme  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP.  
  
### <a name="realm"></a>obszar  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Obszar uwierzytelniania.  
  
### <a name="transfermode"></a>Tryb transferu  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość określająca, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.  
  
### <a name="unsafeconnectionntlmauthentication"></a>unsafeConnectionNtlmAuthentication  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy na serwerze włączone jest niebezpieczne udostępnianie połączenia.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
