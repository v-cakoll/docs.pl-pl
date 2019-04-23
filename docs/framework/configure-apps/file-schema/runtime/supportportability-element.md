---
title: <supportPortability>, element
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc26f9721e911e05c5b5d4092be21a4e1191c84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183949"
---
# <a name="supportportability-element"></a>\<supportPortability> Element
Określa, czy aplikacja może odwołać się tego samego zestawu w dwóch różnych implementacjach systemu .NET Framework, wyłączając zachowania domyślne, które traktuje zestawy za równorzędne do celów przenoszenia aplikacji.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<assemblybinding — > Element  
\<supportPortability> Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|PKT|Atrybut wymagany.<br /><br /> Określa publiczny klucz tokena dotkniętego zestawu jako ciąg.|  
|Włączone|Atrybut opcjonalny.<br /><br /> Określa, czy obsługa przenoszenia między implementacjami określonego zestawu .NET Framework powinien być włączony.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włącz obsługę przenoszenia między implementacjami określonego zestawu .NET Framework. Domyślnie włączone.|  
|false|Wyłącz obsługę przenoszenia między implementacjami określonego zestawu .NET Framework. Umożliwia aplikacjom odwołanie się do wielu implementacjach określonego zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], obsługa jest dostarczana automatycznie dla aplikacji, które mogą użyć jednego z dwóch wdrożeń systemu .NET Framework, na przykład implementacji .NET Framework lub .NET Framework do wdrożenia dodatku Silverlight. Dwie implementacje określonego zestawu .NET Framework są postrzegane jako równoważne przez binder zestawu. W niektórych scenariuszach ta funkcja przenoszenia aplikacji powoduje problemy. W tych scenariuszach `<supportPortability>` element może być użyty, aby wyłączyć funkcję.  
  
 Taki scenariusz jest to zespół, który ma odniesienia zarówno wykonania .NET Framework, jak i programu .NET Framework dla wdrożenia dodatku Silverlight ze szczególnym odniesieniem zespołu. Na przykład projektant XAML, napisany w Windows Presentation Foundation (WPF) może być konieczne odwołać zarówno implementacje pulpitu WPF dla interfejsu użytkownika projektanta i podzbiór WPF, który znajduje się w implementacji programu Silverlight. Domyślnie oddzielne odwołania spowodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne. Ten element wyłącza domyślne zachowanie i pozwala kompilacja osiągnąć sukces.  
  
> [!IMPORTANT]
>  Aby kompilator mógł przekazać informacje do logiki związanej z zestawem wykonywalnych języka wspólnego, należy użyć `/appconfig` opcję kompilatora, aby określić lokalizację pliku app.config, który zawiera ten element.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia aplikacjom odwołanie się do wdrożenia programu .NET Framework i .NET Framework do wdrożenia dodatku Silverlight dowolnego zestawu .NET Framework, która znajduje się w obu implementacjach. `/appconfig` — Opcja kompilatora musi służyć do określania lokalizacji tego pliku app.config.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [/ AppConfig (opcje kompilatora C#)](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Przegląd ujednolicenia zestawów programu .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
