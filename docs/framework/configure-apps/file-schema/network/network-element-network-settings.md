---
title: '&lt;sieci&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;sieci&gt; elementu (ustawienia sieciowe)
Służy do konfigurowania opcji sieciowych do zewnętrznego serwera transportu protokołu SMTP (Simple Mail).  
  
 \<Konfiguracja >  
\<System.NET >  
\<mailSettings >  
\<SMTP >  
\<sieci >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clientDomain`|Określa nazwę domeny klienta do użycia w początkowe żądanie protokołu SMTP, aby nawiązać połączenie z serwerem poczty SMTP. Wartość domyślna to nazwa hosta lokalnego komputera lokalnego wysyłania żądania.|  
|`defaultCredentials`|Określa, czy domyślne poświadczenia użytkownika powinny być używane do uzyskania dostępu do serwera poczty SMTP dla transakcji SMTP. Wartość domyślna to `false`.|  
|`enableSsl`|Określa, czy dostęp do serwera poczty SMTP używany jest protokół SSL. Wartość domyślna to `false`.|  
|`host`|Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`password`|Określa hasło używane do uwierzytelniania serwera poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`port`|Określa numer portu na potrzeby nawiązania połączenia z serwerem poczty SMTP. Wartość domyślna to 25.|  
|`targetName`|Określa nazwę dostawcy usługi (SPN) na potrzeby uwierzytelniania w przypadku używania ochrony rozszerzonej dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`userName`|Określa nazwę użytkownika do uwierzytelniania z serwerem poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<SMTP > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre serwery SMTP wymagają uwierzytelnienia użytkownika na serwerze przed użyciem. Jeśli chcesz uwierzytelnienia przy użyciu domyślnych poświadczeń sieci na hoście, ustaw `defaultCredentials` atrybutu `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `defaultCredentials` atrybutu z plików zastosowania konfiguracji.  
  
 Można również użyć uwierzytelnianie podstawowe (nazwa użytkownika i hasło) do uwierzytelniania osoby do serwera SMTP. Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.  
  
> [!NOTE]
>  Uwierzytelnianie podstawowe przesyła `userName` i `password` wartości do serwera bez szyfrowania. Każda osoba, która monitorowanie ruchu w sieci można wyświetlać swoje poświadczenia i ich używać do łączenia się z serwerem. Należy rozważyć zastosowanie bardziej bezpieczne mechanizm uwierzytelniania, takie jak Kerberos lub programu NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true`, protokołu Kerberos lub NTLM zostaną użyte, jeśli serwer obsługuje te protokoły.  
  
 Podstawowe opcje poświadczenia sieci uwierzytelniania i domyślne wykluczają się wzajemnie; Jeśli ustawisz `defaultCredentials` do `true` i określ nazwę użytkownika i hasło, domyślnych poświadczeń sieciowych jest używany i danych uwierzytelniania podstawowego jest ignorowana.  
  
 Dla uwierzytelniania podstawowego w przypadku określenia `userName`, należy określić również `password` uwierzytelnienia do serwera poczty.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `userName` atrybutu z plików zastosowania konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `password` atrybutu z plików zastosowania konfiguracji. A `password` atrybutu nie zwykle zostaną wprowadzone w plikach konfiguracji ze względów bezpieczeństwa.  
  
 `clientDomain` Atrybut zmiany nazwy domeny klienta używany w początkowej żądania protokołu SMTP do serwera SMTP. `clientDomain` Atrybut można określać do w pełni kwalifikowaną nazwą domeny komputera lokalnego, a nie nazwy localhost, który jest używany domyślnie. Zapewnia to większą zgodności ze standardami protokołu SMTP. Wartość domyślna to nazwa hosta lokalnego komputera lokalnego wysyłania żądania. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `clientDomain` atrybutu z plików zastosowania konfiguracji.  
  
 `targetName` Atrybut jest używany do uwierzytelniania, korzystając z ochrony rozszerzonej. Wartość domyślna to w postaci "SMTPSVC /\<hosta >" gdzie \<hosta > jest nazwą hosta serwera poczty SMTP. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `targetName` atrybutu z plików zastosowania konfiguracji.  
  
 `enableSsl` Atrybut określa, czy dostęp do serwera poczty SMTP używany jest protokół SSL. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Klasa obsługuje tylko rozszerzenia usługi SMTP dla zabezpieczenia SMTP za pośrednictwem zabezpieczeń warstwy transportu zgodnie z definicją w dokumencie RFC 3207. W tym trybie sesji SMTP zaczyna się od nieszyfrowany kanał, a następnie polecenie STARTTLS wystawiony przez klienta do serwera, aby przełączyć się do zapewnienia bezpiecznej komunikacji przy użyciu protokołu SSL. Zobacz dokument RFC 3207 opublikowane przez Internet Engineering Task Force (IETF) Aby uzyskać więcej informacji.  
  
 Metoda alternatywnego połączenia jest, gdzie sesji SSL nawiązaniu góry przed każdego protokołu, które polecenia są wysyłane. Ta metoda łączenia jest czasami nazywany SMTPS i domyślnie używa portu 465. Ta metoda alternatywnego połączenia przy użyciu protokołu SSL nie jest obecnie obsługiwane.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `enableSsl` atrybutu z plików zastosowania konfiguracji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych w sieci.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
