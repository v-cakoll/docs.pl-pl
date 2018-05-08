---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
Ustawia typ obsługi niestandardowego pliku cookie. Ten element tylko mogą występować Jeśli `mode` atrybutu `<cookieHandler>` element jest "Custom". Niestandardowy typ musi pochodzić z <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<customCookieHandler >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Określa typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Services.CookieHandler> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa do odczytu i zapisu plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu obsługi niestandardowych plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ obsługi niestandardowych plików cookie przez dołączenie `<customCookieHandler>` elementu podrzędnego, który odwołuje się do typu obsługi plików cookie. Ten element nie może być określona gdy `mode` ustawiono atrybut "Fragmentaryczne" lub "Default". Programy obsługi niestandardowego pliku cookie musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 `<customCookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.CustomTypeElement> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguruje się SAM do użycia niestandardowego pliku cookie obsługi typu `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.CookieHandler>
