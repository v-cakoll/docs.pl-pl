---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252017"
---
# <a name="customcookiehandler"></a>\<customCookieHandler>
Ustawia niestandardowy typ procedury obsługi plików cookie. Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "Custom". Typ niestandardowy musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**  
  
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
|— typ|Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Services.CookieHandler> klasy. Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , czy program używa do odczytu i zapisu plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku określenia niestandardowego programu obsługi plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ niestandardowej obsługi `<customCookieHandler>` plików cookie, dołączając element podrzędny, który odwołuje się do typu procedury obsługi plików cookie. Nie można określić tego elementu, `mode` gdy atrybut ma wartość "fragmentaryczne" lub "domyślne". Niestandardowe programy obsługi plików cookie muszą pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 Element jest reprezentowany <xref:System.IdentityModel.Configuration.CustomTypeElement> przez klasę. `<customCookieHandler>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguruje SAM do korzystania z niestandardowej procedury obsługi plików cookie typu `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.CookieHandler>
