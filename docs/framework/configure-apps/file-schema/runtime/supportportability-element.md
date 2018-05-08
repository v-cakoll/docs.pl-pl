---
title: '&lt;supportPortability&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt; — Element
Określa, aplikacja może odwoływać tego samego zestawu w dwóch różnych implementacji programu .NET Framework, wyłączając domyślne zachowanie, która traktuje zestawy jako równoważne do celów przenośność aplikacji.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<assemblybinding — > — Element  
\<supportPortability > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|PKT|Atrybut wymagany.<br /><br /> Określa token klucza publicznego zestawu wykorzystywanych jako ciąg.|  
|włączone|Atrybut opcjonalny.<br /><br /> Określa, czy można włączyć obsługę przenoszenia między implementacji określonego zestawu .NET Framework.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włącz obsługę przenośności między implementacji określonego zestawu .NET Framework. Domyślnie włączone.|  
|false|Wyłącz obsługę przenośności między implementacji określonego zestawu .NET Framework. Umożliwia to aplikacji odwołują się do wielu wdrożeń określonego zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], automatycznie podano pomocy technicznej dla aplikacji, które można użyć jednej z dwóch implementacji programu .NET Framework, na przykład albo wdrożenia programu .NET Framework lub .NET Framework dla programu Silverlight implementacji. Dwa implementacji określonego zestawu .NET Framework są widoczne jako równoważne przez obiekt wiążący zestawu. W kilka scenariuszy ta funkcja przenośność aplikacji powoduje występowanie problemów. W tych scenariuszach `<supportPortability>` element może być użyty, aby wyłączyć tę funkcję.  
  
 Taki scenariusz jest zestawem, aby odwoływać zarówno wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu danego odwołania. Na przykład projektanta XAML zapisywane w systemie Windows Presentation Foundation (WPF) może być konieczne odwoływać zarówno w celu wykonania pulpitu WPF, dla interfejsu użytkownika projektanta i podzbiór WPF, który znajduje się w implementacji programu Silverlight. Domyślnie wystąpi błąd kompilatora spowodować oddzielne odwołań, ponieważ powiązań zestawów będzie widział dwa zestawy jako równoważne. Ten element wyłącza domyślne zachowanie i umożliwia kompilacja powiodła się.  
  
> [!IMPORTANT]
>  Aby kompilator, aby przekazać informacje do środowiska CLR dla powiązania zestawu logiki, należy użyć `/appconfig` opcję kompilatora, aby określić lokalizację pliku app.config, który zawiera ten element.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia aplikacji odwołują się do wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu .NET Framework, który istnieje w obu wdrożeniach. `/appconfig` — Opcja kompilatora może służyć do określania lokalizacja tego pliku app.config.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ AppConfig (opcje kompilatora C#)](http://msdn.microsoft.com/library/ee523958.aspx)  
 [Omówienie ujednolicenie programu .NET framework zestawu](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
