---
title: '&lt;specifiedPickupDirectory&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b62dc1a9118f7d4f1f693ade36626deaecd23999
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459740"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a>&lt;specifiedPickupDirectory&gt; — Element (ustawienia sieci)
Konfiguruje katalog lokalny dla serwera transportu protokołu SMTP (Simple Mail).  
  
 \<Konfiguracja >  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<specifiedPickupDirectory>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|Katalog, w których aplikacje zapisać wiadomość e-mail do późniejszego przetwarzania przez serwer SMTP.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<SMTP >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Uwagi  
 `specifiedPickupDirectory` Atrybut Ustawia katalog oszczędzić wiadomości e-mail do przetworzenia przez serwer SMTP w aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono c:\maildrop jako katalog podnoszenia poczty.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
