---
title: <appSettings>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dcdf8d0f11ae65353da08bba1f8d2fe5ab415c6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705561"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings >, element dla \<konfiguracji >

Zawiera ustawienia aplikacji niestandardowych. Jest to sekcję wstępnie zdefiniowanych konfiguracji podano w programie .NET Framework.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Plik**  | Atrybut opcjonalny.<br><br>Określa ścieżkę względną do zewnętrznego pliku zawierającego ustawienia konfiguracji aplikacji niestandardowych. Określony plik zawiera ten sam rodzaj ustawień, które są określone w  **\<Dodaj >**,  **\<Usuń >**, i  **\<Wyczyść >** elementów i używa tej samej pary klucz/wartość w formacie tych elementów.<br><br>Określona ścieżka jest określana względem to główny plik konfiguracji. W przypadku aplikacji Windows Forms jest binarny folder (takie jak */bin/debug*), nie lokalizacji pliku konfiguracji aplikacji. Dla aplikacji formularzy sieci Web, ścieżka jest określana względem katalogu głównego aplikacji, gdzie *web.config* znajduje się plik.<br><br>Należy pamiętać, że środowisko uruchomieniowe ignoruje atrybut, jeśli nie można odnaleźć określonego pliku. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >** — Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Dodaje ustawienia aplikacji niestandardowych. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Usuwa wszystkie uprzednio zdefiniowany aplikacji ustawienia. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Usuwa ustawienie wcześniej zdefiniowanych aplikacji. |

## <a name="remarks"></a>Uwagi

 **\<AppSettings >** element przechowuje informacje o konfiguracji niestandardowej aplikacji, takich jak parametry połączenia bazy danych, ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacja. Pary klucz/wartość, określona w  **\<appSettings >** elementu są dostępne w kodzie za pomocą <xref:System.Configuration.ConfigurationSettings> klasy.

Możesz użyć **pliku** atrybutu w  **\<appSettings >** elementu *Web.config* i pliki konfiguracyjne aplikacji. Ten atrybut określa plik konfiguracji, która zapewnia dodatkowe ustawienia, lub zastępuje ustawienia określone w  **\<appSettings >** elementu. **Pliku** atrybut może być używany w źródło sterowania zespołu rozwoju scenariuszach, na przykład po użytkownik chce, aby zastąpić ustawienia projektu, określone w pliku konfiguracji aplikacji.

Pliki konfiguracji, określone przez **pliku** atrybut musi mieć węzeł główny  **\<appSettings >** zamiast  **\<konfiguracji >**.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje plik ustawień aplikacji zewnętrznej (*custom.config*) definiuje ustawienia aplikacji niestandardowej:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Poniższy przykład przedstawia plik konfiguracji aplikacji, który wykorzystuje ustawienie w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji własnych:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
