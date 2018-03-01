---
title: '&lt;appSettings&gt; elementu &lt;konfiguracji&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > elementu \<configuration >

Zawiera ustawienia aplikacji niestandardowej. Jest to sekcję konfiguracji wstępnie zdefiniowanych dostarczane przez program .NET Framework.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **plik**  | Atrybut opcjonalny.<br><br>Określa ścieżkę względną do zewnętrznego pliku zawierającego ustawienia konfiguracji aplikacji niestandardowej. Określony plik zawiera ten sam rodzaj ustawień, które są określone w  **\<Dodaj >**,  **\<Usuń >**, i  **\<Wyczyść >** elementów i używa tej samej pary klucz wartość w formacie tych elementów.<br><br>Określona ścieżka jest względną do pliku konfiguracji głównego. Dla aplikacji formularzy systemu Windows, jest to folder binarne (takie jak */bin/debug*), nie lokalizację pliku konfiguracji aplikacji. Dla aplikacji formularzy sieci Web, ścieżka jest względem katalogu głównego aplikacji, których *web.config* znajduje się plik.<br><br>Należy pamiętać, środowisko uruchomieniowe ignoruje atrybut, jeśli nie można odnaleźć określonego pliku. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >** — Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<Dodaj >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Dodaje ustawienia aplikacji niestandardowej. |
| [**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Czyści wszystkie ustawienia zdefiniowane aplikacji. |
| [**\<Usuń >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Usuwa ustawienie wcześniej określonych aplikacji. |

## <a name="remarks"></a>Uwagi

 **\<AppSettings >** element przechowuje informacje o konfiguracji niestandardowej aplikacji, takich jak parametry połączenia bazy danych, ścieżki do pliku, adresy URL usługi XML sieci Web lub innych informacji konfiguracji niestandardowej dla aplikacja. Pary klucz wartość określona w  **\<appSettings >** elementu są dostępne w kodu za pomocą <xref:System.Configuration.ConfigurationSettings> klasy.

Można użyć **pliku** atrybutu w  **\<appSettings >** elementu *Web.config* i pliki konfiguracji aplikacji. Ten atrybut określa plik konfiguracji, który udostępnia dodatkowe ustawienia lub zastępuje ustawienia określone w  **\<appSettings >** elementu. **Pliku** atrybut może być używany w źródła formantu zespołu scenariusze programowania, np. gdy użytkownik chce, aby zastąpić ustawienia projektu określony w pliku konfiguracji aplikacji.

Pliki konfiguracji określone przez **pliku** atrybut musi mieć węzeł główny  **\<appSettings >** zamiast  **\<konfiguracji >**.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono plik ustawień zewnętrznej aplikacji (*custom.config*) definiuje ustawienia aplikacji niestandardowej:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

W poniższym przykładzie przedstawiono plik konfiguracji aplikacji, który wykorzystuje ustawienia w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji z własnych:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
