---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073744"
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
  
### <a name="allowcookies"></a>AllowCookies  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez odbiornik HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która wskazuje, czy serwery proxy są ignorowane dla adresów lokalnych.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Po włączeniu połączeń HTTP pozostają aktywne niezależnie od tego, poziom aktywności.  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny rozmiar puli bufora.  
  
### <a name="proxyaddress"></a>ProxyAddress  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator URI, który zawiera adres serwera proxy do obsługi żądań HTTP.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez serwer proxy HTTP.  
  
### <a name="realm"></a>obszar  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Obszar uwierzytelniania.  
  
### <a name="transfermode"></a>Tryb transferu  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która wskazuje, czy włączone jest niebezpieczne udostępnianie połączenia na serwerze.  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
