---
title: <specifiedPickupDirectory>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: a459fee557285935c383dcfaf512c8a8a9aea570
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099277"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a>\<specifiedPickupDirectory >, Element (ustawienia sieci)
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
